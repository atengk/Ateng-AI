<div align="center">

# Ateng-AI

**工业级 AI 智能体、MCP 协议与大模型工具链技术知识库**

[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Author](https://img.shields.io/badge/Author-Ateng-green.svg)](https://github.com/atengk)
[![Documentation](https://img.shields.io/badge/Docs-Online-success.svg)](https://atengk.github.io/Ateng-AI/)
[![VitePress](https://img.shields.io/badge/Built%20with-VitePress%201.6-646cff.svg)](https://vitepress.dev/)
[![Status](https://img.shields.io/badge/Status-Active%20Building-orange.svg)]()

<p align="center">
  持续沉淀与记录 AI Agent 智能体生态、MCP（Model Context Protocol）协议、Skills 技能扩展库、本地私有化大模型与 LLMOps 工具链的技术文档与实战经验。
</p>

[🌐 **在线访问知识库网站**](https://atengk.github.io/Ateng-AI/) · [📖 **Matt Pocock 技能套件指南**](https://atengk.github.io/Ateng-AI/skills/mattpocock/) · [📋 **仓库 Agent 行为准则**](AGENTS.md)

</div>

---

## 📌 仓库定位

随着大语言模型从单纯的“对话交互”向“行动决策（Agentic Workflow）”演进，AI 智能体正全面重构现代研发与生产力流程。

`Ateng-AI` 旨在作为个人的 **工业级 AI 核心技术与工程化落地知识库**，重点记录：
1. **智能体与工具链实操**：从主流 AI Agent 宿主软件的使用调优，到基于 MCP 协议的系统级能力打通。
2. **能力与规则沉淀**：收集并自研高价值 Agent Skills、行为准则（`AGENTS.md`）与系统提示词。
3. **私有化模型基座**：记录开源大模型在本地或私有算力上的部署、推理加速与工程集成。

---

## 🎯 核心聚焦领域

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

### 1. 🤖 AI Agent 实践与生态 ([`agent/`](agent/))
- **编码与生产力 Agent**：深入使用并评测 Antigravity、Claude Code、Cursor、Roo Code 等智能体工具。
- **工作流编排**：多智能体（Multi-Agent）协同机制、子任务派发策略与自动化流程。

### 2. 🛠️ Agent Skills & 规则库 ([`skills/`](skills/))
- **Matt Pocock 专业工程技能套件**：涵盖 **25 个工业级技能** 的全生命周期研发方法论，涵盖需求推演（`grilling`, `grill-with-docs`）、规格制定（`to-spec`）、示踪弹切片（`to-tickets`）、深层模块设计（`codebase-design`）、TDD 红绿循环（`tdd`）、双轴代码审查（`code-review`）到会话交接（`handoff`）。
- **统一领域语言与 ADR**：根目录配备 [`CONTEXT.md`](CONTEXT.md) 词汇表与 [`docs/adr/`](docs/adr/) 架构决策记录。
- **行为准则规范化**：建立严格的 [`AGENTS.md`](AGENTS.md) 仓库级行为守则与 Git 提交红线。

### 3. 🔌 MCP (Model Context Protocol) ([`mcp/`](mcp/))
- **协议标准与接入**：基于 Anthropic 提出的 MCP 统一协议规范，让智能体安全连接外部环境。
- **常用服务端整合**：
  - 数据库操作：MySQL、PostgreSQL、Redis 等只读/读写安全配置。
  - 研发与版本控制：Git、Gitee、GitHub、IDE 联动。
  - 办公与协同：飞书、邮件推送、定时任务等。
- **自定义 MCP 开发**：Node.js / Python 驱动的私有 MCP 服务端开发记录。

### 4. 🧠 本地大模型与基础设施 (LLMOps) ([`llm/`](llm/))
- **轻量本地推理**：Ollama、LM Studio 快速接入与离线运行。
- **高并发推理引擎**：vLLM、TensorRT-LLM 部署配置与显存优化。
- **模型探索**：DeepSeek、Qwen（通义千问）等优秀开源模型的实测、量化与对比。

### 5. 📚 RAG 与外挂知识库 ([`rag/`](rag/))
- **向量数据库集成**：Chroma、Milvus、Qdrant 等向量存储应用。
- **知识检索增强**：文档分块处理、多路召回与重排序（Rerank）优化。

---

## 🗂️ 目录结构说明

```text
Ateng-AI/
├── .github/workflows/    # CI/CD 自动化构建部署配置 (GitHub Actions)
├── .vitepress/           # VitePress 站点配置、侧边栏、自定义主题与样式
├── agent/                # AI Agent 智能体生态与实践
├── docs/
│   ├── adr/              # 架构决策记录 (Architecture Decision Records)
│   └── agents/           # 智能体工程规范 (Issue Tracker, Triage, Domain Docs)
├── llm/                  # 本地私有化大模型与 LLMOps 推理基座
├── mcp/                  # Model Context Protocol 协议生态与 Server 部署
├── rag/                  # RAG 知识检索增强与向量知识库
├── skills/               # Agent Skills 技能中心
│   └── mattpocock/       # Matt Pocock 25 个专业工程技能全景指南
├── AGENTS.md             # 仓库级 AI Agent 行为准则与操作红线 (必读)
├── CONTEXT.md            # 统一领域语言词汇表 (Ubiquitous Language Glossary)
├── index.md              # 文档站点门户首页配置
├── package.json          # 项目依赖配置 (VitePress, Mermaid 插件等)
└── pnpm-lock.yaml        # pnpm 依赖锁文件
```

---

## 🚀 本地开发与预览指南

本项目基于 [VitePress](https://vitepress.dev/) 搭建，并集成了 `vitepress-plugin-mermaid` 原生支持流程图与时序图渲染。

### 1. 环境准备
- **Node.js**：推荐 `>= 20.0.0`
- **包管理器**：推荐使用 **`pnpm 9+`**

### 2. 本地运行步骤

```bash
# 1. 克隆代码仓库
git clone https://github.com/atengk/Ateng-AI.git
cd Ateng-AI

# 2. 安装依赖 (使用 pnpm)
pnpm install

# 3. 启动本地开发服务 (支持热重载)
pnpm docs:dev

# 4. 生产环境静态打包构建
pnpm docs:build

# 5. 本地预览构建产物
pnpm docs:preview
```

---

## 🗺️ 建设路线图 (Roadmap)

- [x] **Phase 1: 基础建设与规范成型**
  - [x] 建立 VitePress 现代化文档系统与自动化 GitHub Pages 部署流水线
  - [x] 配置仓库级智能体工程规范（Issue Tracker、分流标签、领域模型）
  - [x] 确立本地优先（Local-First）与禁止未经许可提交的架构决策记录（`ADR-0001`）
  - [x] 建立项目统一领域语言词汇表（`CONTEXT.md`）
- [x] **Phase 2: Matt Pocock 25 技能全体系建设**
  - [x] 编撰套件全景矩阵与生命周期闭环流程图（`skills/mattpocock/index.md`）
  - [x] 编撰需求推演与任务规划专题（`planning.md`）
  - [x] 编撰架构设计与工程编码专题（`engineering.md`）
  - [x] 编撰质量把控与排障审查专题（`review-quality.md`）
  - [x] 编撰协同交接与辅助工具专题（`collaboration.md`）
  - [x] 编撰工程初始化与配置规范专题（`setup.md`）
  - [x] 集成 Mermaid 插件实现架构拓扑图、时序图与状态机原生自适应渲染
- [ ] **Phase 3: MCP 工具链实战**
  - [ ] 梳理常用开发与数据库类 MCP Server 的标准配置模版
  - [ ] 实现首个自定义 MCP 服务端（如自建研发助手服务）
- [ ] **Phase 4: 本地大模型与知识库进阶**
  - [ ] 本地搭建 Ollama + 优秀开源代码模型运行环境
  - [ ] 探索 Agent + 个人知识库（RAG）的闭环实践

---

## 🤝 贡献与交流

本仓库为持续演进的个人技术与工程化实践记录，欢迎提交 Issue 交流技术见解，或发起 Pull Request 分享你常用的优质 MCP、Skill 或 Agent 配置！

---

## 📄 开源协议

本项目遵循 [MIT License](LICENSE) 开源协议。
