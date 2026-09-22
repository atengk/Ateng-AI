---
layout: home

hero:
  name: "Ateng-AI"
  text: "工业级 AI 智能体与技术架构知识库"
  tagline: 持续沉淀 Agentic Workflow 智能体工程范式、MCP 协议生态、Skills 扩展库与本地大模型实践
  image:
    src: /hero.svg
    alt: Ateng-AI 技术图
  actions:
    - theme: brand
      text: 🚀 快速开始
      link: /skills/
    - theme: alt
      text: 🛠️ Matt Pocock 套件
      link: /skills/mattpocock/
    - theme: alt
      text: 🌟 GitHub
      link: https://github.com/atengk/Ateng-AI

features:
  - icon: 🤖
    title: AI Agent 智能体生态
    details: 深入实践 Antigravity、Claude Code 等前沿 Agent 宿主，探索多智能体协同协作、子任务自动派发与自主研发流。
    link: /skills/
  - icon: 🛠️
    title: Matt Pocock 技能套件
    details: 全面收录 25 个专业工程技能，覆盖需求推演、领域建模、示踪弹任务拆解、TDD 实施到双轴审查全生命周期。
    link: /skills/mattpocock/
  - icon: 🔌
    title: MCP 统一协议连接
    details: 基于 Model Context Protocol 协议规范，安全打通数据库、Git 版本控制、IDE 联动与第三方协同工具链。
    link: /skills/
  - icon: 🧠
    title: 本地私有化大模型
    details: 沉淀 Ollama、vLLM 高并发本地与私有推理基座，探索 DeepSeek、Qwen 等开源优秀模型的工程集成。
    link: /skills/
  - icon: 📚
    title: RAG 知识检索增强
    details: 结合向量数据库与混合检索策略，探索专业文档语义切块、多路召回、重排序（Rerank）与垂直领域智能问答。
    link: /skills/
  - icon: 📐
    title: 工业级工程与质量准则
    details: 严格执行标准行为准则（AGENTS.md）、深层模块理论（Deep Module）、契约测试与零盲目编码的工程铁律。
    link: /skills/mattpocock/setup
---

<div class="home-content-wrapper" style="max-width: 1152px; margin: 40px auto 0; padding: 0 24px;">

## 🗺️ 知识体系架构全景

随着大语言模型从单纯的“对话交互”演进为“具备自主行动与决策能力的智能体（Agentic Workflow）”，现代软件开发正经历工程范式的根本性重塑。`Ateng-AI` 致力于打造一套体系化、可复用、高可靠的 **AI 研发工程化落地知识库**：

```
                      ┌─────────────────────────────────┐
                      │            Ateng-AI             │
                      │  工业级 AI 智能体与技术架构体系 │
                      └────────────────┬────────────────┘
                                       │
        ┌──────────────┬───────────────┼───────────────┬──────────────┐
        ▼              ▼               ▼               ▼              ▼
   【AI Agent】    【Skills 套件】   【MCP 协议】     【本地大模型】   【RAG 知识库】
  • Antigravity  • 25 个工程技能   • 数据库与工具  • Ollama/vLLM   • 向量检索增强
  • Claude Code  • 需求推演规划    • Git 与研发协同 • DeepSeek/Qwen • 混合多路召回
  • 多智能体调度 • 架构与双轴审查  • 办公自动化     • 私有算力推理  • 垂直问答落地
```

---

## 🧭 核心专题直达索引

针对当前已完整交付的 **Matt Pocock 25 个专业工程技能套件**，您可以按照研发阶段直接跳转至对应深度指南：

| 阶段专题 | 核心聚焦技能 | 核心价值与产出物 | 快速入口 |
| :--- | :--- | :--- | :---: |
| **🧭 全景与速查** | 25 个技能全景矩阵、路由表 | 全生命周期闭环图、9 大高频工作场景速查矩阵 | [进入阅读](/skills/mattpocock/) |
| **📋 需求推演与规划** | `grilling`, `domain-modeling`, `to-spec`, `to-tickets`, `wayfinder` | 决策树前沿推演、领域词汇表与 ADR、示踪弹任务拓扑、路线图导航 | [进入阅读](/skills/mattpocock/planning) |
| **🏗️ 架构设计与编码** | `codebase-design`, `improve-codebase-architecture`, `implement`, `tdd`, `prototype` | John Ousterhout 深层模块理论、架构扫描报告、红绿测试、抛弃型原型 | [进入阅读](/skills/mattpocock/engineering) |
| **🔍 质量把控与排障** | `code-review`, `diagnosing-bugs`, `resolving-merge-conflicts`, `triage` | 双轴并行审查（规范+契约）、四阶段疑难排障、变基冲突化解、五角色工单分流 | [进入阅读](/skills/mattpocock/review-quality) |
| **🤝 协同交接与工具** | `ask-matt`, `handoff`, `wizard`, `teach`, `research`, `writing-for-agents` | 智能技能路由、跨会话压缩交接、可交互 Bash 运维向导、沉浸式教学 | [进入阅读](/skills/mattpocock/collaboration) |
| **⚙️ 工程初始化规范** | `setup-matt-pocock-skills`, Issue Tracker, Triage Labels, Domain Docs | 代码库脚手架初始化、GitHub Issues 对接、分流标签字典、统一语言词汇表 | [进入阅读](/skills/mattpocock/setup) |

---

## ⚡ 智能体端到端工程闭环

在实际研发实践中，推荐遵循如下标准化闭环链路：

1. **推演前置**：使用 `/grill-with-docs` 消除未明确假设，将领域术语沉淀至 [`CONTEXT.md`](/skills/mattpocock/setup#三、领域文档架构-domain-docs-规范)。
2. **契约固化**：使用 `/to-spec` 提炼为不可逆的 Spec 技术规格，并由 `/to-tickets` 拆解为具备阻塞拓扑的示踪弹任务。
3. **测试先行**：使用 `/implement` 联合 `/tdd`，先确立失败测试用例，再进行无损契约编码。
4. **双轴防线**：使用 `/code-review` 派发并行子 Agent，从“规范轴”与“契约轴”两端交叉验收，确保高质量合入。

> [!TIP] 更多技能探索
> 欢迎从 [Skills 技能中心大厅](/skills/) 开启您的智能体工程化之旅！

</div>