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
                      │        Agent Skills 体系        │
                      └────────────────┬────────────────┘
                                       │
        ┌──────────────────────────────┴──────────────────────────────┐
        ▼                                                             ▼
【Matt Pocock 工程技能套件】                                     【通用自研技能库】
 • 涵盖 25 个端到端工程智能体技能                                 • 知识库检索与文档构建
 • 贯穿推演、设计、编码、质量与协同                               • 基础设施与研发运维辅助
 👉 [点击进入全景指南](/skills/mattpocock/)                       👉 持续建设演进中...
```

### 1. [Matt Pocock 技能套件 (25 个专业工程技能)](/skills/mattpocock/)
Matt Pocock 提出的一套工业级 AI Agent 研发协作方法论，将自然语言沟通全面收敛为标准化设计树（Design Tree）、示踪弹任务（Tracer Bullet Tickets）与高质量实施代码。

- **[套件全景与速查](/skills/mattpocock/)**：25 个技能分类矩阵与生命周期闭环图谱。
- **[需求推演与任务规划](/skills/mattpocock/planning)**：严苛设计推演、统一语言词汇表与路线图导航。
- **[架构设计与工程编码](/skills/mattpocock/engineering)**：深层模块（Deep Module）设计、TDD 红绿循环与原型探索。
- **[质量把控与排障审查](/skills/mattpocock/review-quality)**：双轴代码审查、四阶段疑难排障与 Issue 分流状态机。
- **[协同交接与辅助工具](/skills/mattpocock/collaboration)**：智能技能路由、跨会话交接与交互向导。
- **[工程初始化与配置规范](/skills/mattpocock/setup)**：Issue Tracker、Triage Labels 与 Domain Docs 接入指南。

---

## 🚀 快速上手使用技能

在支持 Agent Skills 规范的宿主环境（如 Google Antigravity、Claude Code、Cursor 等）中，可以直接通过快捷斜杠命令触发对应技能：

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

> [!TIP] 推荐阅读
> 建议先从 [Matt Pocock 套件全景导读](/skills/mattpocock/) 开始，全面了解智能体在现代软件工程生命周期中的闭环协作模式。
