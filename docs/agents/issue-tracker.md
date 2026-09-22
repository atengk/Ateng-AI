# Issue 跟踪器：GitHub (Issue tracker: GitHub)

本仓库的 Issue 和需求规格（Specs）统一托管于 GitHub Issues。所有操作均使用 `gh` CLI 完成。

## 约定与操作命令 (Conventions)

- **创建 Issue**：`gh issue create --title "..." --body "..."`。多行内容建议使用 heredoc。
- **读取 Issue**：`gh issue view <number> --comments`，配合 `jq` 过滤评论并获取标签。
- **列出 Issue**：`gh issue list --state open --json number,title,body,labels,comments --jq '[.[] | {number, title, body, labels: [.labels[].name], comments: [.comments[].body]}]'`，按需附加 `--label` 和 `--state` 过滤。
- **发表评论**：`gh issue comment <number> --body "..."`
- **添加 / 移除标签**：`gh issue edit <number> --add-label "..."` / `--remove-label "..."`
- **关闭 Issue**：`gh issue close <number> --comment "..."`

仓库信息可直接从 `git remote -v` 推断 —— 在 Git 克隆目录下运行 `gh` 时会自动完成识别。

## Pull Requests 作为分流受理对象 (Pull requests as a triage surface)

**PRs as a request surface: no.** _（若本仓库将外部 PR 视为功能需求受理，请将其设为 `yes`；`/triage` 技能会读取此标识）_

当设为 `yes` 时，PR 与 Issue 使用相同的标签与状态流转，对应使用 `gh pr` 命令：

- **读取 PR**：`gh pr view <number> --comments`，并通过 `gh pr diff <number>` 获取差异。
- **列出待分流的外部 PR**：`gh pr list --state open --json number,title,body,labels,author,authorAssociation,comments`，仅保留 `authorAssociation` 为 `CONTRIBUTOR`、`FIRST_TIME_CONTRIBUTOR` 或 `NONE` 的条目（排除 `OWNER`/`MEMBER`/`COLLABORATOR`）。
- **评论 / 标签 / 关闭**：分别使用 `gh pr comment`、`gh pr edit --add-label`/`--remove-label`、`gh pr close`。

由于 GitHub 的 Issue 与 PR 共享编号空间，单个 `#42` 可能是 Issue 也可能是 PR —— 优先尝试 `gh pr view 42`，失败后回退至 `gh issue view 42`。

## 当技能提示“发布到 Issue 跟踪器”时 (When a skill says "publish to the issue tracker")

创建一个 GitHub Issue。

## 当技能提示“获取相关 Ticket”时 (When a skill says "fetch the relevant ticket")

执行 `gh issue view <number> --comments`。

## 路线图导航操作 (Wayfinding operations)

由 `/wayfinder` 技能调用。**导航图 (Map)** 为一个主 Issue，其**子任务 (Child)** 为关联的具体 Ticket。

- **导航图 (Map)**：标记为 `wayfinder:map` 的独立 Issue，内容包含 Notes / 已做决策 (Decisions-so-far) / 未明边界 (Fog)。通过 `gh issue create --label wayfinder:map` 创建。
- **子任务 Ticket (Child ticket)**：作为 GitHub 子 Issue（通过 sub-issues 端点的 `gh api`）关联到主图。若未开启子 Issue 功能，则在主图 Issue 正文的任务列表中添加子项，并在子项正文顶部标注 `Part of #<map>`。标签格式为：`wayfinder:<type>`（可选 `research`/`prototype`/`grilling`/`task`）。被认领后，Ticket 将分配给执行者。
- **阻塞依赖 (Blocking)**：使用 GitHub 原生 Issue 依赖 —— 规范且在 UI 上直观可见。添加依赖关系：`gh api --method POST repos/<owner>/<repo>/issues/<child>/dependencies/blocked_by -F issue_id=<blocker-db-id>`，其中 `<blocker-db-id>` 为阻塞者的数值型**数据库 ID**（通过 `gh api repos/<owner>/<repo>/issues/<n> --jq .id` 获取，**而非** `#number` 或 `node_id`）。GitHub 会在 `issue_dependencies_summary.blocked_by` 中返回活跃阻塞者。若不可用，则在子项正文顶部添加 `Blocked by: #<n>, #<n>` 作为降级方案。所有前置阻塞项关闭后，Ticket 自动解除阻塞。
- **前沿就绪查询 (Frontier query)**：列出导航图下所有未关闭的子项（`gh issue list --state open`，作用域限制在子 Issue 或任务列表），过滤掉存在未关闭阻塞项（`issue_dependencies_summary.blocked_by > 0` 或 `Blocked by` 包含开启状态的 Issue）或已被分配的条目；按导航图顺序取第一项执行。
- **认领 (Claim)**：`gh issue edit <n> --add-assignee @me` —— 开展工作前的第一步操作。
- **解决 (Resolve)**：`gh issue comment <n> --body "<answer>"`，接着执行 `gh issue close <n>`，最后将上下文指针（简述 + 链接）追加到主图的 Decisions-so-far 章节中。
