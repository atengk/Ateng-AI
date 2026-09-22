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
        ┌──────────────────────────────┴──────────────────────────────┐
        ▼                                                             ▼
【Anthropic 官方技能体系】                                   【Matt Pocock 工程技能套件】
 • 遵循 agentskills.io 开放标准                                • 涵盖 25 个端到端专业工程技能
 • 涵盖 19 个官方技能与 Office 生产级套件                     • 贯穿推演、设计、编码、质量与协同
 • 渐进式披露、离线校验与多宿主运行                            • 设计树、示踪弹任务与双轴代码审查
 👉 [点击进入 Anthropic 专题](/skills/anthropic/)             👉 [点击进入 Matt Pocock 专题](/skills/mattpocock/)
```

### 1. [Anthropic 官方技能规范与全景指南](/skills/anthropic/)
遵循 Anthropic Agent Skills 开放规范，涵盖官方 19 个工业级技能全景矩阵、自定义技能渐进式披露设计、离线工程校验与多宿主运行时集成。

- **[开放标准与技术导读](/skills/anthropic/)**：开放技能标准背景愿景、技术维度横向解耦与生态协同架构。
- **[官方 19 个技能全景矩阵与核心实战拆解](/skills/anthropic/catalog)**：Office 四件套、工程与 MCP、前端设计、组织协同 4 大集群速查，双重协议合规警示卡片与核心技能深度解构。
- **[自定义技能开发、目录规约与离线校验工程指南](/skills/anthropic/authoring)**：详解 `SKILL.md` 形式化契约、`scripts/` / `references/` / `assets/` 资源解耦、`skills-ref` 静态校验与 CI/CD 门禁流水线实战。
- **[多宿主集成、客户端配置与运行时调试指南](/skills/anthropic/runtime)**：主流宿主适配配置、环境变量管理、离线运行排障与全生命周期调试。

### 2. [Matt Pocock 技能套件 (25 个专业工程技能)](/skills/mattpocock/)
Matt Pocock 提出的一套工业级 AI Agent 研发协作方法论，将自然语言沟通全面收敛为标准化设计树（Design Tree）、示踪弹任务（Tracer Bullet Tickets）与高质量实施代码。

- **[套件全景与速查](/skills/mattpocock/)**：25 个技能分类矩阵与生命周期闭环图谱。
- **[需求推演与任务规划](/skills/mattpocock/planning)**：严苛设计推演、统一语言词汇表与路线图导航。
- **[架构设计与工程编码](/skills/mattpocock/engineering)**：深层模块（Deep Module）设计、TDD 红绿循环与原型探索。
- **[质量把控与排障审查](/skills/mattpocock/review-quality)**：双轴代码审查、四阶段疑难排障与 Issue 分流状态机。
- **[协同交接与辅助工具](/skills/mattpocock/collaboration)**：智能技能路由、跨会话交接与交互向导。
- **[工程初始化与配置规范](/skills/mattpocock/setup)**：Issue Tracker、Triage Labels 与 Domain Docs 接入指南。

---

## 🚀 快速上手使用技能

在支持 Agent Skills 规范的宿主环境（如 Google Antigravity、Claude Code、Cursor 等）中，可以直接通过快捷斜杠命令或自然语言触发对应技能：

### 1. 触发 Matt Pocock 工程技能工作流

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

### 2. 挂载与校验 Anthropic 官方及自研技能

```bash
# 1. 使用 skills-ref 离线校验自研技能契约与规范
skills-ref validate ./my-skill

# 2. 在 Claude Code 中直接加载工作区技能
claude-code --skill ./skills/anthropic/

# 3. 在 Google Antigravity 中通过工作区技能机制开箱即用
# （技能放置于 .agents/skills/ 目录下即可自动感知加载）
```

> [!TIP] 推荐阅读
> 建议初次接触智能体技能的开发者先从 [Anthropic 开放标准与技术导读](/skills/anthropic/) 开始，理解三级渐进式加载机制；随后结合 [Matt Pocock 套件全景导读](/skills/mattpocock/) 掌握端到端软件工程实践。
