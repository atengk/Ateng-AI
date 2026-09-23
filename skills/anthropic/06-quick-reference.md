# Anthropic Skills 语法速查手册与权威参考矩阵

| 属性 | 详情 |
| :--- | :--- |
| **文档类型** | 快速参考手册 (Cheat Sheet) / 事实核查矩阵 |
| **当前状态** | 已归档 (Accepted) |
| **作者** | Ateng |
| **创建日期** | 2026-09-23 |
| **关联系统/模块** | Anthropic Skills / Agent Skills Specification |

---

## 1. `SKILL.md` 模板与语法速查 (Cheat Sheet)

### 1.1 最小可行技能模板 (Minimal Viable Skill)

适用于职责单一、无需外部脚本辅助的轻量级纯文本 SOP 技能（约 20 行）：

```markdown
---
name: json-formatter
description: Validates and pretty-prints JSON payloads. Use when the user asks to format, repair, or sort keys in raw JSON data. Avoid using for XML or YAML files.
---

# JSON 格式化与校验指南

## 核心任务
- 将用户输入的无序或畸形 JSON 字符串转换为标准 2 空格缩进的格式化文本。
- 自动按字母序对根节点及子节点字典的 Key 进行升序排列。

## 操作规范
1. **语法校验**：解析传入的字符串。若包含语法错误（如缺少闭合引号、逗号冗余），指出具体行号与修复方案。
2. **格式输出**：必须以标准 Markdown `json` 代码块包裹交付，严禁输出裸文本。
```

---

### 1.2 工业级完整生产模板 (Enterprise Production-Grade Skill)

适用于包含前置依赖检查、外部脚本编排、深水区参考手册及容错补偿的复杂业务技能：

```markdown
---
name: enterprise-report-generator
description: Generates executive financial and ops reports in Excel (.xlsx) and Word (.docx). Use when the user requests generating monthly performance summaries, cost audits, or board decks. Avoid using for lightweight plain-text notes.
license: Apache-2.0
compatibility: claude-code>=1.0.0
metadata:
  category: finance-reporting
  author: Ateng
  version: 2.1.0
---

# 企业级运营与财务综合报告生成指南

## 1. 角色定位与设计哲学
本技能面向企业级核心经营指标汇总。强制遵循“数据计算依赖脚本、排版布局依赖模板、输出结果原生带公式”的工业级准则。

## 2. 前置环境与运行时卫语句 (Prerequisites)
在执行任何生成动作之前，必须首先验证当前运行环境：
1. **Python 运行时**：执行 `python --version` 确保版本 `>= 3.10`。
2. **必需第三方库**：
   - 检查 `openpyxl`：`python -c "import openpyxl"`
   - 检查 `python-docx`：`python -c "import docx"`
   - 若依赖缺失，中断任务并提示执行：`pip install openpyxl python-docx`。

## 3. 标准作业流程 (Workflow & SOP)
### 步骤 1: 业务数据模型对齐与清洗
- 提取用户需求中的周期（月度/季度）、营收数值、成本结构与部门归属。
- 调用确定性清洗脚本处理原始数据：
  ```bash
  python scripts/clean_metrics.py --input raw_data.json --output clean.json
  ```

### 步骤 2: 驱动模板合成产物
- 复制 `assets/template.xlsx` 作为基础底模。
- 严格遵循 [references/styling-guide.md](references/styling-guide.md) 中的财务掩码规范：
  - 金额格式：`¥#,##0.00`
  - 增长率公式：`=(C3-B3)/B3`，格式化为 `0.0%`
  - 首行冻结窗格，启用深色表头与斑马纹。

### 步骤 3: 产物完整性与格式自检
- 检查文件是否损坏，输出摘要前 10 行关键指标。

## 4. 边界处理与容错规则 (Error Handling)
- **文件锁冲突（PermissionError）**：若目标文件正被本地 Office 软件打开占用，自动追加随机时间戳保存（如 `report_20260923_1420.xlsx`）并友好提示用户。
- **除零异常防御**：同期基数为 0 时，增长率单元格写入 `N/A`，严禁产生 `#DIV/0!` 破坏版面。
```

---

## 2. 核心 CLI 指令与目录路径速查

### 2.1 Claude Code 技能管理常用命令表

| 操作意图 | 命令语法 | 说明与影响 |
| :--- | :--- | :--- |
| **挂载市场** | `/plugin marketplace add <github-org/repo>` | 注册远程技能仓库索引（如 `anthropics/skills`） |
| **安装集合** | `/plugin install <collection-name>@<marketplace>` | 批量安装场景化技能集合（如 `document-skills`） |
| **安装单技能** | `/plugin install <skill-name>@<marketplace>` | 按需安装独立技能（如 `mcp-builder`） |
| **查看技能** | `/plugin list` | 列出当前会话已激活生效的所有技能及版本 |
| **更新技能** | `/plugin update <package-name>` | 拉取最新提交并更新本地运行时缓存 |
| **卸载技能** | `/plugin uninstall <package-name>` | 移除技能并恢复默认路由 |

---

### 2.2 跨平台标准目录路径速查表

| 作用域类型 | 操作系统 | 推荐物理挂载路径 |
| :--- | :--- | :--- |
| **项目作用域 (Project)** | Linux / macOS / Windows | `<project-root>/.claude/skills/<skill-name>/` |
| **开放标准项目路径** | 通用 (跨 Agent 兼容) | `<project-root>/.agents/skills/<skill-name>/` |
| **用户全局 (Global)** | Linux / macOS | `~/.claude/skills/<skill-name>/` |
| **用户全局 (Global)** | Windows | `C:\Users\<Username>\.claude\skills\<skill-name>\` |

---

## 3. 常见报错与排障决策树 (Troubleshooting & FAQs)

### 3.1 技能未能如期触发 (Skill Under-triggering)
- **现象**：向 Claude 发出了明确任务，但 Agent 未调用技能中的 SOP。
- **排查步骤**：
  1. 执行 `/plugin list` 确认该技能是否处于已激活状态。
  2. 检查 `SKILL.md` 的 YAML Frontmatter 中的 `name` 与 `description`。
  3. **优化 `description`**：检查描述是否过于抽象，显式增加触发短语：`Use when the user requests creating...`。
  4. 运行 `python -m skills.skill_creator.improve_description` 执行召回率优化。

---

### 3.2 脚本执行报 `ModuleNotFoundError`
- **现象**：Agent 尝试运行 `python scripts/helper.py` 时报错缺少依赖包。
- **排查步骤**：
  1. 宿主系统的 Python 全局环境或当前虚拟环境（`venv`）未安装依赖。
  2. 在 `SKILL.md` 中增加**步骤 0：前置环境卫语句**，在执行前主动检测并自动安装：
     ```bash
     pip install -r requirements.txt
     ```

---

### 3.3 上下文超限或推理漂移 (Context Bloat / Drift)
- **现象**：技能激活后，模型响应速度变慢，容易遗忘早期指令。
- **排查步骤**：
  1. 统计 `SKILL.md` 的实际行数是否超过了 **500 行黄金红线**。
  2. 将正文中大篇幅的参考代码、API 契约或样式表移至 `references/` 目录，通过正文中的相对链接按需读取。

---

## 4. 权威参考资料与事实依据清单 (References & Grounding)

本文档套件（全 7 篇）的所有参数、命令、架构分层与安全基线均严格基于以下权威官方信源核实：

### 4.1 官方黄金信源清单 (Tier 1 Authority Sources)

1. [[Tier 1]] [anthropics/skills 官方 GitHub 代码库](https://github.com/anthropics/skills) - 官方参考实现仓库、双轨许可协议与技能目录拓扑 (核验日期: 2026-09-23)
2. [[Tier 1]] [Agent Skills 行业开放标准 (agentskills.io)](https://agentskills.io) - `SKILL.md` 语法规范、渐进式披露生命周期与跨生态互操作标准 (核验日期: 2026-09-23)
3. [[Tier 1]] [Anthropic 官方工程技术博客: Equipping agents for the real world](https://anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills) - 架构设计哲学、Token 预算控制与工业落地实战 (核验日期: 2026-09-23)
4. [[Tier 1]] [Claude 客户支持中心: What are skills? (Article 12512176)](https://support.claude.com/en/articles/12512176-what-are-skills) - 官方关于技能心智模型与使用场景权威说明 (核验日期: 2026-09-23)
5. [[Tier 1]] [Claude 客户支持中心: Using skills in Claude (Article 12512180)](https://support.claude.com/en/articles/12512180-using-skills-in-claude) - Claude Code CLI 与插件市场安装规范 (核验日期: 2026-09-23)
6. [[Tier 1]] [Claude 客户支持中心: Creating custom skills (Article 12512198)](https://support.claude.com/en/articles/12512198-creating-custom-skills) - 自定义技能打包、上传与运行时特权配置 (核验日期: 2026-09-23)

---

### 4.2 全套件关键事实与技术契约全景核查矩阵

| 核查对象 (规范/配置/命令) | 官方基准事实 (Ground Truth) | 对应官方依据 | 核实状态 |
| :--- | :--- | :--- | :--- |
| **Marketplace 挂载语法** | `/plugin marketplace add anthropics/skills` | Claude Code CLI Docs | 已核实真实有效 |
| **官方插件集合名称** | `document-skills@anthropic-agent-skills` | anthropics/skills 仓库 | 已核实真实有效 |
| **YAML 必需字段契约** | `name` 与 `description` 为强制项，其余为可选扩展 | `agentskills.io` 核心规范 | 已核实真实有效 |
| **渐进式披露三层模型** | Level 1 Discovery $\rightarrow$ Level 2 Activation $\rightarrow$ Level 3 Resources | Anthropic Engineering Blog | 已核实真实有效 |
| **单技能物理目录拓扑** | `SKILL.md` + 可选 `scripts/`、`references/`、`assets/` | `spec/agent-skills-spec.md` | 已核实真实有效 |
| **跨平台标准目录路径** | `<repo>/.agents/skills/` 与 `<repo>/.claude/skills/` | Agent Skills Open Standard | 已核实真实有效 |
| **元技能双裁判机制** | `grader.md` 规则打分 + `comparator.md` 双盲横向比对 | `skills/skill-creator` | 已核实真实有效 |
| **描述调优脚本路径** | `skills.skill_creator.improve_description` | 官方评测自动化工具链 | 已核实真实有效 |
| **Office 技能许可协议** | Source-available 源码可用，商业研究与个人开发可用 | anthropics/skills LICENSE | 已核实真实有效 |
| **常规与创意技能协议** | Apache-2.0 宽松开源协议 | anthropics/skills LICENSE | 已核实真实有效 |
| **正文规模防护红线** | 建议控制在 500 行以内，大篇幅资料外置于 `references/` | Anthropic Best Practices | 已核实真实有效 |
| **沙箱隔离最佳实践** | 生产环境推荐容器 `--read-only`、网络出站禁用与环境变量清洗 | OWASP LLM Top 10 | 已核实真实有效 |

---

## 5. 文档套件全景关联导航

- [返回套件全景总览 (index.md)](./index.md)
- [01. 架构原理与 SKILL.md 规范标准](./01-architecture-and-spec.md)
- [02. 多端运行环境与安装部署实战](./02-installation-and-runtime.md)
- [03. 官方精选技能全景与实战目录](./03-official-skills-catalog.md)
- [04. 自定义技能开发与 Eval 评测体系](./04-skill-development-and-eval.md)
- [05. 企业级安全治理与生产最佳实践](./05-security-and-best-practices.md)
- [06. 语法速查手册与权威参考矩阵](./06-quick-reference.md)
