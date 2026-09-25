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

**Composite Workflow (复合工作流)**:
由用户显式编排技能与模型纪律原语技能依据严格输入输出契约串联而成的端到端研发管道，严禁在流水线中发生同级编排技能递归嵌套。
_Avoid_: Complex flow, chained scripts, mixed pipeline, macro

**Failure Guard (翻车熔断防护)**:
在长流水线执行中，针对 Agent 偏离意图、陷入红灯循环或上下文超载时预设的人工干预断点与重置规约。
_Avoid_: Error handler, retry mechanism, fallback routine

**Breaking Migration (破坏性跃迁)**:
跨主版本升级时，底层依赖或契约发生破坏性变更，依托官方一手调研、废弃扫描与双版本兼容测试网推进的平滑演进过程。
_Avoid_: Version bump, dependency upgrade, force migration

**Intent-Preserving Merge (意图级合流)**:
在解决陈旧分支冲突时，超越机械代码行覆盖比对，通过深刻理解双端业务意图与架构接缝进行的功能无损合并。
_Avoid_: Fast-forward, auto-merge, mechanical conflict resolution

**Legacy Archeology (遗留代码考古与逆向建模)**:
对缺乏文档与单测的陈旧系统，通过依赖热点扫描、黑话破译与接缝探寻，自底向上逆向恢复统一语言并沉淀 `CONTEXT.md` 的工程实践。
_Avoid_: Code reading, manual audit, reverse engineering

**Hypothesis-Driven Validation (假说驱动验证)**:
将 TDD 红绿测试思想投射至商业运营、运维与制度推演，先确立量化证伪指标（Red），再设计最小业务机制见绿（Green）的闭环验证范式。
_Avoid_: Trial and error, vibe business, speculative pivot

**Organizational Seam (业务组织接缝)**:
在多部门协同、跨业务域或非技术流程治理中，保持业务单元低耦合、高内聚，支持独立演进与灰度落地的权责契约边界。
_Avoid_: Department boundary, organizational silo, handoff wall

**Evaluation-Driven Development (评测驱动研发)**:
将传统 TDD 的红绿重构铁律升维至 AI/LLM 应用研发，在编写 Prompt 或 Agent 编排逻辑之前，先定义包含准确率、召回率、幻觉率阈值的量化断言集，以确定性评测网指导模型调优与逻辑重构。
_Avoid_: Prompt trial, vibe eval, manual eyeballing, speculative prompting

**Data Contract Guard (数据契约卫语句)**:
在大数据与数仓 ETL 管道的关键架构接缝处预设的形式化质量拦截规则（如空值率容差、主键唯一性、数值分布区间断言），契约破坏时立即熔断并阻断脏数据污染下游报表。
_Avoid_: Data validation, SQL check, pipeline filter, manual audit

**PoC Guard (漏洞复现卫语句)**:
在安全应急与漏洞修复中，先编写最小可复现漏洞攻击路径的自动化验证脚本（将 PoC 作为红灯失败用例），修复后再作为防止漏洞死灰复燃的回归保护断言永久纳管。
_Avoid_: Exploit script, security check, test payload, manual pentest

**Virtual Hardware Mock (虚拟仿真硬件桩)**:
在软硬件协同研发与物联网通信中，基于芯片 Datasheet 和总线协议在软件侧构建的高保真虚拟设备桩，使上位机开发与协议解析完全脱离物理板卡与连线依赖。
_Avoid_: Dummy device, simulator, hardware stub, stub driver

**Look-Ahead Invariant (防未来函数不变量)**:
在金融量化策略与时序数据回测中，断言任何决策时刻 $t$ 绝对不可读取 $t+1$ 时刻以后的行情、成交量或财报数据，彻底根除时序穿越导致的虚假高收益。
_Avoid_: Future data leak, peeking ahead, time leak, lookahead

**Frame Budget Invariant (帧预算不变量)**:
在 3D 渲染与图形物理仿真中，断言每帧 CPU 与 GPU 计算总耗时必须严格锁定在目标帧率预算内（如 60FPS 对应 16.6ms），超限时立即触发几何降级或跳帧保护。
_Avoid_: Performance limit, FPS drop check, render timeout, lag guard

**Anti-Goodhart Metric Guard (反古德哈特度量卫语句)**:
在研发效能与团队组织治理中预设的防作弊机制，当一项指标被选为考核目标时，立即联合设立对抗性反向制衡指标（如度量“交付吞吐量”时必须强绑定“线上缺陷逃逸率”与“客户满意度”），防止指标被操纵失真。
_Avoid_: Metric KPI, performance rule, scorecard guard, target rule

**Clinical Data Invariant (临床数据不变量)**:
在医学临床试验数据清洗与质控中，断言受试者生理生化参数、用药剂量与访视时间窗必须符合医学病理逻辑与方案契约，违背不变量时自动触发数据质疑（Query）。
_Avoid_: Medical check, GCP validation, trial rule, protocol validator





