<div align="center">

# Ateng-AI

**AI 技术、智能体与大模型工具链的技术仓库**

[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Author](https://img.shields.io/badge/Author-Ateng-green.svg)](https://github.com/atengk)
[![Status](https://img.shields.io/badge/Status-Building-orange.svg)]()
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)]()

<p align="center">
  持续沉淀与记录 AI Agent 智能体生态、MCP（Model Context Protocol）协议、Skills 技能扩展库、本地私有化大模型与 LLMOps 工具链的技术文档与实践经验。
</p>

</div>

---

## 📌 仓库定位

随着大语言模型从单纯的“对话交互”向“行动决策（Agentic Workflow）”演进，AI 智能体正全面重构现代研发与生产力流程。

`Ateng-AI` 旨在作为个人的 **AI 核心技术与工程化落地知识库**，重点记录：
1. **智能体与工具链实操**：从主流 AI Agent 宿主软件的使用调优，到基于 MCP 协议的系统级能力打通。
2. **能力与规则沉淀**：收集并自研高价值 Agent Skills、行为准则（`AGENTS.md`）与系统提示词。
3. **私有化模型基座**：记录开源大模型在本地或私有算力上的部署、推理加速与工程集成。

---

## 🎯 核心聚焦领域

```
                      ┌─────────────────────────────────┐
                      │            Ateng-AI             │
                      │  AI 技术与智能体工具链知识体系  │
                      └────────────────┬────────────────┘
                                       │
        ┌──────────────┬───────────────┼───────────────┬──────────────┐
        ▼              ▼               ▼               ▼              ▼
   【AI Agent】    【MCP 协议】     【Skills/Rules】  【本地大模型】   【RAG 知识库】
  • Antigravity  • 数据库生态      • 通用技能沉淀   • Ollama/vLLM   • 向量数据库
  • Claude Code  • 研发协作工具    • 行为准则标准   • DeepSeek/Qwen • 混合检索
  • Cursor/IDE   • 生产力集成      • Prompt 模版化  • 私有化运行    • 智能问答
```

### 1. 🤖 AI Agent 实践与生态
- **编码与生产力 Agent**：深入使用并评测 Antigravity、Claude Code、Cursor、Roo Code 等智能体工具。
- **工作流编排**：多智能体（Multi-Agent）协同机制、子任务派发策略与自动化流程。

### 2. 🔌 MCP (Model Context Protocol)
- **协议标准与接入**：基于 Anthropic 提出的 MCP 统一协议规范，让智能体安全连接外部环境。
- **常用服务端整合**：
  - 数据库操作：MySQL、PostgreSQL、Redis 等只读/读写安全配置。
  - 研发与版本控制：Git、Gitee、GitHub、IDE 联动。
  - 办公与协同：飞书、邮件推送、定时任务等。
- **自定义 MCP 开发**：Node.js / Python 驱动的私有 MCP 服务端开发记录。

### 3. 🛠️ Agent Skills & Rules
- **Skill 技能库沉淀**：编写符合规范的 `SKILL.md` 与配套执行脚本，赋能 Agent 拥有专业技能。
- **准则规范化**：探索高质量的 `AGENTS.md`、`CLAUDE.md` 等全局行为准则，避免模型幻觉与偏离规范。

### 4. 🧠 本地大模型与基础设施 (LLMOps)
- **轻量本地推理**：Ollama、LM Studio 快速接入与离线运行。
- **高并发推理引擎**：vLLM、TensorRT-LLM 部署配置与显存优化。
- **模型探索**：DeepSeek、Qwen（千问）等优秀开源模型的实测、量化与对比。

### 5. 📚 RAG 与外挂知识库
- **向量数据库集成**：Chroma、Milvus、Qdrant 等向量存储应用。
- **知识检索增强**：文档分块处理、多路召回与重排序（Rerank）优化。

---

## 🗺️ 建设路线图 (Roadmap)

- [ ] **Phase 1: 基础建设与 Agent 入门**
  - [ ] 规范仓库基础文档规范与分类体系
  - [ ] 整理 Antigravity、Claude Code 等核心工具的基础配置与常用快捷技巧
- [ ] **Phase 2: MCP 工具链实战**
  - [ ] 梳理常用开发与数据库类 MCP Server 的标准配置模版
  - [ ] 实现首个自定义 MCP 服务端（如自建研发助手服务）
- [ ] **Phase 3: Skills 沉淀与规范演进**
  - [ ] 沉淀第一批可复用的通用开发与运维 Skill 脚本
  - [ ] 完善可移植的 `AGENTS.md` 行为准则模板
- [ ] **Phase 4: 本地大模型与知识库进阶**
  - [ ] 本地搭建 Ollama + 优秀开源代码模型运行环境
  - [ ] 探索 Agent + 个人知识库（RAG）的闭环实践

---

## 🤝 贡献与交流

本仓库为持续演进的个人学习与实践记录，欢迎提交 Issue 交流技术见解，或发起 Pull Request 分享你常用的优质 MCP、Skill 或 Agent 配置！

---

## 📄 开源协议

本项目遵循 [MIT License](LICENSE) 开源协议。
