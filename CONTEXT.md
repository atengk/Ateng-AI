# Matt Pocock 智能体工程技能上下文 (Agent Engineering Skills Context)

本上下文定义了在研发与协作流程中使用 Matt Pocock 智能体工程技能套件时的统一领域语言与术语规范，为需求推演、架构设计、任务拆解与审查实施提供一致的词汇基准。

## Language

### 需求推演与任务规划 (Planning & Wayfinding)

**Frontier (决策前沿)**:
设计树或任务拓扑中所有前置依赖已完全满足、当前可直接决策或执行的最小就绪集合。
_Avoid_: Active tasks, ready queue, backlog, current work

**Design Tree (设计树)**:
将复杂方案拆解为逐层分支的决策层级图，子决策必须在前置决策决议后方可展开推演。
_Avoid_: Mind map, decision flow, flowchart

**Tracer Bullet Ticket (示踪弹任务)**:
垂直贯穿系统各层级（架构、接口、UI、测试）、端到端可验证且粒度适配单个会话上下文的独立任务单元。
_Avoid_: User story, subtask, work item, slice

**Wayfinding Map (路线导航图)**:
作为超大会话级攻坚主图的顶层 Issue 或汇总文档，记录当前已知决策、待解迷雾（Fog）并关联所有子任务。
_Avoid_: Epic, master ticket, project plan, roadmap

### 架构设计与工程编码 (Architecture & Implementation)

**Deep Module (深层模块)**:
拥有极其精简通用的对外接口，但内部封装了高度复杂性与丰富业务价值的软件设计单元。
_Avoid_: Fat service, big class, component

**Seam (架构接缝)**:
系统内部不改变生产代码即可插入测试桩、替换依赖或观察外部行为的高层级隔离缝隙。
_Avoid_: Mock point, hook, interface injection

**Expand-Contract (扩展-收缩重构)**:
针对大爆炸级重构采用的两阶段迁移模式：先添加新形态共存（Expand），分批迁移调用点后再彻底删除旧形态（Contract）。
_Avoid_: Big bang refactor, direct replacement, breaking rename

### 质量把控与团队协同 (Quality & Collaboration)

**Triage Roles (分流角色)**:
标准五分类状态机（`needs-triage`, `needs-info`, `ready-for-agent`, `ready-for-human`, `wontfix`），用于精准裁决 Issue 与外部 PR 的生命周期。
_Avoid_: Issue status, bug priority, stage

**Agent Brief (智能体任务简报)**:
上下文自包含、无歧义且经过验证（带代码复现路径与验收断言）的规范任务说明，供离线自主 Agent 直接开箱执行。
_Avoid_: Task description, issue body, prompt instruction

**Handoff Document (交接文档)**:
将长会话历史提炼压缩为包含已达共识、未决事项与下一会话精确目标的结构化交接说明书。
_Avoid_: Summary, chat history, conversation recap

**Local-First Execution (本地优先执行)**:
智能体对代码或文档的所有操作默认仅在本地工作区完成自检，严禁未经人类显式授权擅自触发 Git 提交与远程推送。详见 `docs/adr/0001-local-first-git-commit-policy.md`。
_Avoid_: Auto-commit, silent push, background sync

### 智能体技能标准与生态 (Agent Skills Standard & Ecosystem)

**Agent Skill (智能体技能)**:
遵循 `agentskills.io` 开放标准的自包含文件夹，由 `SKILL.md`（元数据与核心指引）、可选的 `scripts/`、`references/` 和 `assets/` 组成，供 AI 智能体动态加载以完成专业化任务。
_Avoid_: Plugin, tool pack, function extension, action

**Progressive Disclosure (渐进式披露)**:
智能体按需分阶段加载技能资源的技术机制：启动时仅加载元数据（~100 Tokens），激活时载入指令主体（< 5000 Tokens），执行时按需读取外部资源，从而最小化上下文窗口消耗。
_Avoid_: Lazy loading, on-demand prompt, dynamic import

**Skill Contract (技能契约)**:
在 `SKILL.md` 头部由 YAML Frontmatter 定义的形式化约束规范，涵盖 `name`、`description`、`compatibility`、`metadata` 与 `allowed-tools` 等核心字段。
_Avoid_: Header config, skill config, frontmatter schema

**Skill Validator (技能校验器)**:
基于官方 `skills-ref` 规范库对自研技能包的目录结构、命名合法性及 Frontmatter 契约进行端到端静态校验的工程工具。
_Avoid_: Linter, syntax checker, schema tester


