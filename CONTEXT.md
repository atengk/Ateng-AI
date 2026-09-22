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
