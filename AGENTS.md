# 项目规范与 Agent 行为守则 (Repository Agent Guidelines)

本规范定义了所有在 `Ateng-AI` 知识库中工作的 AI Agent（智能体）必须严格遵守的全局工程纪律、交互规范与工具链约束。

---

## 一、Git 版本控制铁律 (最高红线)

> [!CAUTION] 核心工程红线：严禁自动提交与静默推送
> 任何 AI Agent **严禁**在未经开发者显式、口令式授权（如明确发出“提交到本地”、“推送到远程”指令）的前提下，擅自执行 `git commit` 或 `git push`！
> 详细架构决策参见：[`docs/adr/0001-local-first-git-commit-policy.md`](docs/adr/0001-local-first-git-commit-policy.md)。

1. **本地优先原则 (Local-First Execution)**：
   - 所有的文件创建、内容修改、格式调整与依赖安装，默认**仅在本地工作区**进行。
   - 智能体完成代码或文档修改后，应在本地完成编译自检，并将结果呈现给开发者审核，等待进一步指令。
2. **两阶段显式确认**：
   - **本地提交阶段**：仅当用户明确指示“提交到本地”时，执行 `git add` 与 `git commit`。
   - **远程推送阶段**：仅当用户明确指示“推送到远程”时，方可执行 `git push`。
3. **规范化提交 (Conventional Commits)**：
   - 统一遵循 Conventional Commits 规范，格式为 `<type>(<scope>): <中文描述>`。
   - 严禁生成泛化无意义的提交信息，单次提交保持原子性，聚焦单一意图。

---

## 二、文档编写与排版标准 (Tech-Doc 基线)

编写或修改本项目中的任何 Markdown 文档时，必须遵循以下标准：

1. **中英文半角空格 (盘古之白)**：
   - 汉字与英文、代码标识符（如 `VitePress`、`pnpm`、`TypeScript`）及数字之间，必须保留一个半角空格。
   - 示例：`支持使用 pnpm 9+ 进行高效构建。`
2. **文档头部标准化元数据**：
   - 新建技术专题或指南文档时，起始必须提供标准元数据表：
     ```markdown
     # [文档标题]

     | 属性 | 详情 |
     | :--- | :--- |
     | **文档类型** | 技术专题指南 / 全景导读 / 接口契约 |
     | **当前状态** | 已归档 (Accepted) / 建设中 (Draft) |
     | **作者** | Ateng |
     | **创建日期** | YYYY-MM-DD |
     | **关联系统/模块** | Ateng-AI / [子模块名] |
     ```
3. **自包含 Mermaid 语法安全**：
   - 所有 Mermaid 节点文本中若包含括号 `()`、方括号 `[]` 或特殊符号，**必须使用双引号包裹**（例如 `NodeA["智能体 (Agent)"]`）。
   - 时序图（`sequenceDiagram`）必须启用 `autonumber` 与生命周期激活。
4. **GitHub 标准 Alerts 语法**：
   - 重点说明与风险提示使用 `> [!NOTE]`、`> [!TIP]`、`> [!IMPORTANT]`、`> [!WARNING]`、`> [!CAUTION]`。

---

## 三、工具链与构建自检纪律

1. **环境与包管理器**：
   - 本项目统一使用 **`pnpm 9+`** 作为包管理器，Node.js 推荐版本 >= 20。
   - 严禁使用 npm 或 yarn 混用生成其它锁文件。
2. **本地端到端构建验证**：
   - 任何涉及文档结构、导航栏、侧边栏或 VitePress 配置的改动，必须在本地运行以下命令执行全量静态编译校验：
     ```bash
     pnpm docs:build
     ```
   - 确保 **0 编译错误** 且 **0 死链告警（Dead Links）**，严禁将存在死链的代码留存给流水线。

---

## 四、领域统一语言与架构遵从

1. **术语遵从**：
   - 涉及到智能体研发协作的概念时，必须严格遵从根目录 [`CONTEXT.md`](CONTEXT.md) 中定义的标准统一语言（如 `Frontier`、`Design Tree`、`Tracer Bullet Ticket`、`Deep Module` 等），严禁随意引入负面清单（`_Avoid_`）中的生僻近义词。
2. **ADR 架构决策遵从**：
   - 必须尊重 [`docs/adr/`](docs/adr/) 下记录的架构决策记录。方案如与现有 ADR 存在冲突，必须显式指明原因并重新评估，严禁静默覆盖。

---

## 五、Agent skills 配置

本仓库为 Matt Pocock 专业工程技能套件配置的基础设施契约如下：

### Issue tracker

GitHub Issues（通过 `gh` CLI 管理）。详见 [`docs/agents/issue-tracker.md`](docs/agents/issue-tracker.md)。

### Triage labels

标准五角色分流标签体系 (`needs-triage`, `needs-info`, `ready-for-agent`, `ready-for-human`, `wontfix`)。详见 [`docs/agents/triage-labels.md`](docs/agents/triage-labels.md)。

### Domain docs

单上下文架构（[`CONTEXT.md`](CONTEXT.md) 与 [`docs/adr/`](docs/adr/)）。详见 [`docs/agents/domain.md`](docs/agents/domain.md)。
