# Skills 技能中心

| 属性 | 详情 |
| :--- | :--- |
| **文档类型** | 技能大厅与分类导览 (Skills Catalog) |
| **当前状态** | 已归档 (Accepted) |
| **作者** | Ateng |
| **创建日期** | 2026-09-22 |
| **关联系统/模块** | Ateng-AI / Skills |

欢迎来到 **Ateng-AI 智能体技能中心**。在现代 AI Agent 架构中，Skills（技能扩展库）是智能体连接开发环境、遵循团队工程准则并执行专业化研发任务的核心能力载体。

---

## 🎯 技能库全景索引

智能体技能库采用模块化沉淀体系，当前重点集成并支持如下专业工程技能生态：

```
                                  ┌─────────────────────────────────┐
                                  │    Ateng-AI 智能体技能生态体系    │
                                  └────────────────┬────────────────┘
                                                   │
         ┌────────────────────────┬────────────────┴────────────────┬────────────────────────┐
         ▼                        ▼                                 ▼                        ▼
【Anthropic 官方体系】     【Matt Pocock 工程套件】          【Superpowers 自动化】    【Spec Kit 规格驱动】
 • 开放标准与元技能         • 25 个专业工程技能               • 15 个全自主研发技能     • 5 阶段 SDD 闭环研发
 • 渐进式披露三层架构       • 示踪弹任务与双轴审查            • 严格 TDD 与 Worktree    • 宪法记忆与双轨架构
 👉 [进入 Anthropic 专题](/skills/anthropic/) 👉 [进入 Matt Pocock 专题](/skills/mattpocock/) 👉 [进入 Superpowers 专题](/skills/superpowers/) 👉 [进入 Spec Kit 专题](/skills/spec-kit/)
```

### 1. [Anthropic 官方技能规范与全景指南](/skills/anthropic/)
遵循 Anthropic Agent Skills 开放规范，涵盖渐进式披露心智模型、官方精选技能全景、自定义技能开发与自动化 Eval 评测及企业安全治理。

- **[📖 全景导读与核心指南](/skills/anthropic/)**：开放标准愿景、渐进式披露三层认知跃迁与 5 分钟极速上手。
- **[🏛️ 架构原理与规范标准](/skills/anthropic/01-architecture-and-spec)**：`SKILL.md` 物理拓扑契约、Frontmatter 元数据规范与资源解耦。
- **[⚡ 运行环境与安装部署](/skills/anthropic/02-installation-and-runtime)**：Claude Code CLI 插件管理、Claude.ai 部署与跨平台运行时。
- **[📚 官方技能全景与实战](/skills/anthropic/03-official-skills-catalog)**：Office 文档、研发工具、创意设计等官方精选技能深度解构。
- **[🛠️ 技能开发与评测体系](/skills/anthropic/04-skill-development-and-eval)**：元技能 `skill-creator` 实战、自动化 Eval 评测集与描述调优闭环。
- **[🛡️ 安全治理与最佳实践](/skills/anthropic/05-security-and-best-practices)**：提示词注入防御、代码沙箱隔离、设计反模式与 CI/CD 规范。
- **[📑 语法速查与参考矩阵](/skills/anthropic/06-quick-reference)**：`SKILL.md` 语法模板 Cheat Sheet 与事实核查矩阵。

### 2. [Matt Pocock 技能套件 (25 个专业工程技能)](/skills/mattpocock/)
Matt Pocock 提出的一套工业级 AI Agent 研发协作方法论，将自然语言沟通全面收敛为标准化设计树（Design Tree）、示踪弹任务（Tracer Bullet Tickets）与高质量实施代码。

- **[🧭 套件全景与快速入门](/skills/mattpocock/)**：25 个技能分类矩阵、双轴调用模型与研发闭环图谱。
- **[⚙️ 体系架构与初始化配置](/skills/mattpocock/01-architecture-and-setup)**：仓库契约架构、Issue Tracker 适配与全局智能路由。
- **[🧩 需求对齐与深度模块设计](/skills/mattpocock/02-alignment-and-design)**：极限盘问机制、领域统一语言与 Ousterhout 深度模块设计。
- **[📋 规范制定与任务分流管理](/skills/mattpocock/03-planning-and-triage)**：免面试规格合成、曳光弹任务切片与五角色分流。
- **[🔬 工程研发与红绿测试审查](/skills/mattpocock/04-engineering-execution-and-quality)**：红-绿-重构刚性铁律、六阶段系统排障与双子 Agent 审查。
- **[🔍 深度调研与自动化向导](/skills/mattpocock/05-research-and-devops)**：高信任度技术调研与防错交互运维向导。
- **[🤝 效能协作与文档编写](/skills/mattpocock/06-productivity-and-collaboration)**：跨会话上下文交接、异步决策问卷与面向 Agent 的文档工程。

### 3. [Superpowers 自动化交付技能体系 (15 个核心技能)](/skills/superpowers/)
由 Jesse Vincent（obra）提出的一套面向 AI 编码智能体的工业级自主研发方法论与 15 个开箱即用技能库。通过“约束优于自由”的工程控制理念，彻底根治 Agent 容易失控、盲目编码、跳过测试与代码幻觉的痛点。

- **[🦸 全景总览与架构指南](/skills/superpowers/)**：架构哲学、四大工程支柱、15 个技能全景矩阵与全生命周期轨迹。
- **[💻 多平台环境部署与集成](/skills/superpowers/01-installation-and-harnesses)**：14+ 平台安装实战、Session-Start Hook 与环境自检排障。
- **[📝 需求澄清与计划制定](/skills/superpowers/02-core-workflow-and-specs)**：交互式头脑风暴、Visual Companion 画板与防呆实施计划。
- **[🤖 子代理驱动开发 (SDD)](/skills/superpowers/03-subagent-driven-development)**：Git Worktree 隔离、Ledger 容灾账本、5 轮修复循环与熔断裁决。
- **[🚦 质量保障与系统排障](/skills/superpowers/04-testing-and-debugging)**：红绿 TDD 铁律、系统化调试四大法则与完成前核验。
- **[🔄 代码审查与分支生命周期](/skills/superpowers/05-review-and-branch-lifecycle)**：客观审查包生成、多智能体并发调度与分支交付 SOP。
- **[🩺 进阶扩展与诊断套件](/skills/superpowers/06-skill-authoring-and-diagnostics)**：自定义技能编写、劝服心理学、自动化 Evals 与性能诊断。

### 4. [Spec Kit 规格驱动开发体系 (GitHub 官方)](/skills/spec-kit/)
由 GitHub 官方开源的规格驱动开发（Spec-Driven Development, SDD）工具套件与工程规约。将开发重心从即兴对话（Vibe Coding）前置收敛为结构化契约，通过项目宪法、需求规格、技术方案与原子任务闭环杜绝 AI 幻觉与代码漂移。

- **[🌱 全景导读与 SDD 范式](/skills/spec-kit/)**：从 Vibe Coding 到规范驱动开发跃迁、三大核心公理与双轨架构。
- **[⚙️ 环境基准与多 Agent 集成](/skills/spec-kit/01-installation-and-setup)**：Python 3.11+ / uv 环境基准、Copilot / Claude / Cursor 集成与存量项目引入。
- **[🔄 核心工作流全景实战](/skills/spec-kit/02-core-workflow-sdd)**：Constitution 宪法 → Specify → Plan → Tasks → Implement 全链路。
- **[🛠️ CLI 命令行与技能速查](/skills/spec-kit/03-cli-and-commands)**：`specify-cli` 全量参数字典、`/speckit-*` Agent 技能及故障排除。
- **[🚀 扩展生态与企业实战](/skills/spec-kit/04-extensions-and-advanced)**：Bug 修复流、Idea 评估流、CI/CD 自动化门禁与大型 Monorepo 治理。

---

## 🚀 快速上手使用技能

在支持 Agent Skills 规范的宿主环境（如 Google Antigravity、Claude Code、Cursor 等）中，可以直接通过快捷斜杠命令或自然语言触发对应技能：

### 1. 触发 Superpowers 自动化交付工作流

```bash
# 1. 在 Google Antigravity 中一键安装 Superpowers 插件
agy plugin install https://github.com/obra/superpowers

# 2. 会话启动后，Agent 自动挂载 session-start hook
# 当接收开发需求时，Agent 会主动后退 (Step Back) 进行需求切片澄清并编写详细计划
# 3. 驱动子智能体执行开发与双角色代码审查
/subagent-driven-development
```

### 2. 触发 Matt Pocock 工程技能工作流

```bash
# 1. 询问适合当前场景的技能与工作流
/ask-matt

# 2. 对当前技术方案展开深度压力测试与推演
/grill-with-docs

# 3. 将推演结论沉淀为标准技术规格并发布到 Issue 跟踪器
/to-spec

# 4. 将技术规格切分为具备依赖拓扑的垂直任务
/to-tickets
```

### 3. 挂载与校验 Anthropic 官方及自研技能

```bash
# 1. 使用 skills-ref 离线校验自研技能契约与规范
skills-ref validate ./my-skill

# 2. 在 Claude Code 中直接加载工作区技能
claude-code --skill ./skills/anthropic/

# 3. 在 Google Antigravity 中通过工作区技能机制开箱即用
# （技能放置于 .agents/skills/ 目录下即可自动感知加载）
```

### 4. 驱动 Spec Kit 规格驱动开发工作流

```bash
# 1. 安装 specify-cli 并初始化工程
uv tool install specify-cli
specify init my-app --integration copilot

# 2. 在 IDE Chat 对话中依序驱动 SDD 规范生命周期
/speckit-constitution
/speckit-specify <特性需求描述>
/speckit-plan
/speckit-tasks
/speckit-implement
```

> [!TIP] 推荐阅读路径
> 建议开发者先从 [Anthropic 开放标准与技术导读](/skills/anthropic/) 开始，理解技能标准与渐进式加载机制；随后结合 [Matt Pocock 套件全景导读](/skills/mattpocock/) 掌握敏捷设计树与示踪弹任务规划；通过 [Superpowers 自动化交付全景导读](/skills/superpowers/) 掌握生产级多智能体协同与严格 TDD 落地闭环；最后依托 [Spec Kit 规格驱动开发全景导读](/skills/spec-kit/) 建立宪法约束下的防漂移工程闭环。
