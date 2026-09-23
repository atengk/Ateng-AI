# Anthropic Skills 官方精选技能全景与实战目录

| 属性 | 详情 |
| :--- | :--- |
| **文档类型** | 技术专题图谱 / 技能实战参考手册 |
| **当前状态** | 已归档 (Accepted) |
| **作者** | Ateng |
| **创建日期** | 2026-09-23 |
| **关联系统/模块** | anthropics/skills 官方技能库 |

---

## 1. 官方核心办公文档技能矩阵 (Document Skills)

在 [anthropics/skills](https://github.com/anthropics/skills) 官方仓库中，办公文档处理套件（`docx`, `xlsx`, `pptx`, `pdf`）是架构复杂度最高、经过最多生产检验的核心资产。它们直接支撑了 Claude.ai 官方的文件生成与深度编辑能力，采用 **源码可用（Source-available）** 协议开源，作为工业级技能设计的黄金参考标杆。

```
                  ┌──────────────────────────────────────────────┐
                  │          官方办公文档技能套件矩阵             │
                  └──────────────────────────────────────────────┘
                                         │
        ┌───────────────────┬────────────┴───────┬───────────────────┐
        ▼                   ▼                    ▼                   ▼
┌───────────────┐   ┌───────────────┐    ┌───────────────┐   ┌───────────────┐
│     docx      │   │     xlsx      │    │     pptx      │   │      pdf      │
├───────────────┤   ├───────────────┤    ├───────────────┤   ├───────────────┤
│ • 红线修订跟踪│   │ • 复杂公式注入│    │ • 动态幻灯排版│   │ • 结构化文本流│
│ • 边注/行内批注│   │ • 数据透视分析│    │ • 母版主题继承│   │ • 坐标视觉标注│
│ • 企业排版样式│   │ • 条件格式着色│    │ • 占位符防溢出│   │ • 双向拆分合并│
└───────────────┘   └───────────────┘    └───────────────┘   └───────────────┘
```

---

### 1.1 `docx`：工业级 Word 文档生成与修订跟踪

- **定位与价值**：不仅仅是生成普通文字段落，而是全功能操作 OpenXML 标准的 `.docx` 文件。深度支持法律文本审校、正式合同起草与企业白皮书排版。
- **底层技术栈**：基于 Python `python-docx` 库与底层 XML 树（`lxml`）直接操作。
- **核心能力与业务 SOP**：
  1. **修订模式（Track Changes）**：能够在不破坏原文的前提下，向文档中注入 `<w:ins>`（插入）和 `<w:del>`（删除）标签，模拟 Word 原生红线修订，并标注修改人与时间戳。
  2. **批注系统（Comments）**：支持在指定字词或段落锚点上添加边注与审阅批注。
  3. **专业排版规范**：内置中英文标题层级样式、1.25 倍紧凑行高、表格无缝内边距及自动分页符控制。

```bash
# 触发示例
"请审阅这份采购合同草案 contract.docx，使用修订模式修正其中的违约责任条款，并在付款节点处添加一条批注说明风险。"
```

---

### 1.2 `xlsx`：高阶 Excel 财务报表、公式透视与复杂分析

- **定位与价值**：生成具有专业审计级排版的电子表格，杜绝“纯静态数字倾泻”，强制要求采用公式驱动。
- **底层技术栈**：基于 Python `openpyxl` 库。
- **核心能力与业务 SOP**：
  1. **公式优先原则（Formula-First）**：合计、均值、毛利率等派生数据，必须写入 Excel 原生公式（如 `=SUM(C2:C20)`、`=AVERAGE(D2:D20)`、`=VLOOKUP(...)`），确保用户在 Excel 中修改基础数据时结果自动联动。
  2. **财务数字格式化**：数值单元格必须显式注入格式化掩码（如千分位会计格式 `#,##0.00`、百分比格式 `0.0%`）。
  3. **视觉层级与条件格式**：首行标题栏深色背景与冻结窗格（Freeze Panes）、斑马纹隔行变色、自动数据条（Data Bars）。

```bash
# 触发示例
"基于提供的 Q3 销售流水，生成一份专业财务损益表 profit_loss.xlsx，要求包含毛利率公式，并对首行进行冻结。"
```

---

### 1.3 `pptx`：结构化演示文稿布局与模板驱动生成

- **定位与价值**：摆脱千篇一律的白底黑字简报，输出具有设计美感与逻辑层次的商务级幻灯片。
- **底层技术栈**：基于 Python `python-pptx` 库。
- **核心能力与业务 SOP**：
  1. **16:9 现代宽屏基线**：统一锁定标准 16:9 宽屏比例（13.333 $\times$ 7.5 英寸）。
  2. **网格系统与防文本溢出**：预先计算卡片宽度、间距与字体磅值，杜绝文字超出卡片边框或换行挤压。
  3. **双栏/三栏对比容器**：采用卡片式容器封装痛点分析、方案对比与路线图。

```bash
# 触发示例
"为公司的云原生架构演进方案制作一套 5 页的技术汇报幻灯片 cloud_arch.pptx，采用深色科技风主题，包含对比卡片。"
```

---

### 1.4 `pdf`：结构化文本提取、视觉标注与双向合并

- **定位与价值**：针对 PDF 格式的不可变特性，提供高精度的逆向结构化读取与衍生处理。
- **底层技术栈**：基于 Python `pypdf`、`pdfplumber` 或 `pymupdf` (fitz)。
- **核心能力与业务 SOP**：
  1. **表格结构逆向重构**：从无边界线 PDF 中精准提取表格结构并转换为 Markdown 或 Pandas DataFrame。
  2. **高亮与坐标批注注入**：在保留原始版面的基础上，根据文字坐标注入高亮图层与矩形标注框。
  3. **文档拼接与水印盖印**：安全地将多个凭据 PDF 合并为单卷并加盖防伪水印。

---

## 2. 工程研发与自动化测试技能 (Engineering & Testing)

此类别技能面向软件工程交付与质量保障，采用 Apache 2.0 宽松开源协议。

| 技能标识 (Name) | 核心职责 | 技术实现路径 | 适用场景 |
| :--- | :--- | :--- | :--- |
| **`skill-creator`** | **元技能 (Meta-Skill)**：通过人机交互自动构建、测试、评估与优化新技能 | 交互式生成脚手架 + 双裁判 Agent 盲测 + 描述调优脚本 | 从 0 到 1 打造高质量生产技能 |
| **`mcp-builder`** | 生成符合规范的 Model Context Protocol 服务端脚手架 | FastMCP (Python) / TypeScript MCP SDK | 为私有 API 或数据库编写 Claude 工具插件 |
| **`webapp-testing`** | 驱动无头浏览器执行 Web 端端到端自动化验收测试 | Playwright / Chromium 无头自动化驱动 | 页面回归测试、视觉破损检测、用户交互回放 |

### 2.1 `mcp-builder` 核心实战要点
指导开发者在构建 MCP（Model Context Protocol）服务时，严格遵从协议规范：
- 正确区分 **Tools（工具）**、**Resources（静态资源）** 与 **Prompts（提示词模板）**。
- 为每个工具参数定义严格的 Pydantic 或 JSON Schema 类型注解与中文描述。
- 自动处理多行错误输出与优雅异常降级。

### 2.2 `webapp-testing` 核心实战要点
- 利用 Playwright 启动隔离浏览器上下文，自动等待 DOM 水合就绪。
- 支持捕获完整页面截图（Full Page Screenshot）并交由视觉模型评估 UI 渲染缺陷。
- 输出标准化的 JUnit XML 或 HTML 测试运行报告。

---

## 3. 创意、版式与视觉设计技能 (Creative & Visual Design)

Anthropic 官方设计类技能专注于打破“泛滥的 AI 塑料感”，通过引入系统化设计哲学与可复现算法，生成具备现代质感的视觉产物。

### 3.1 `algorithmic-art`：基于 p5.js 的可复现随机生成艺术
- **设计哲学**：拒绝一次性生成的不可控图片，提倡“计算美学宣言（Computational Manifesto）”。
- **技术要点**：
  - 基于 **p5.js** 编写纯前端渲染代码。
  - **Seed 随机种子锁定**：通过注入确定性伪随机数发生器（PRNG），确保相同的种子在任何时间、任何设备上均能渲染出像素级完全一致的艺术图案。
  - 运用流场（Flow Fields）、元胞自动机（Cellular Automata）与分形几何（Fractals）。

---

### 3.2 `canvas-design`：专业级海报、刊物与版面设计引擎
- **设计哲学**：遵循网格系统（Grid Systems）与排版层次（Typographic Hierarchy）。
- **技术要点**：
  - 强制声明中英文字体栈保底（如 Inter, Roboto, Noto Sans SC）。
  - 建立严格的垂直节奏基线（Vertical Baseline Grid），消除无序空行与比例失调。
  - 生成矢量级 SVG 或无损 PNG 产物。

---

### 3.3 `frontend-design` 与 `theme-factory`：反 AI 脸工业级前端方案
- **反“AI 塑料感”准则**：
  - 严禁滥用千篇一律的生硬蓝色渐变、大圆角纯白卡片与过重模糊阴影。
  - 倡导微质感设计：精细的 1px 边框分隔线（Subtle Borders）、高呼吸感字间距、考究的字重对比（400 vs 600）。
- **`theme-factory` 赋能**：
  - 自动输出符合 WCAG 2.1 AA 级无障碍色彩对比度要求的 Tailwind CSS 调色板与语义化 CSS 自定义属性（CSS Variables）。

---

## 4. 企业通信与品牌协作技能 (Enterprise & Brand)

针对大型组织协同中一致性差、协作效率低的痛点，官方提供了成熟的企业级工作流技能。

### 4.1 `brand-guidelines`：企业品牌视觉与话术规范硬约束
- **核心机制**：
  - 在 Level 1 发现层监听所有涉及品牌文案、公关稿及对外宣传材料的请求。
  - 在 Level 2 注入企业专有语气基调（Tone of Voice，如：严谨、专业、克制）、标准英文缩写大小写规范、违禁词拦截列表及配色 Hex 值。
  - 在生成物交付前强制执行规范审查清单（Checklist），拦截不合规表述。

---

### 4.2 `doc-coauthoring`：专业人机协同长篇文档编写编排
- **协作闭环流程**：
  ```
  [阶段 1: 大纲对齐] ──> [阶段 2: 逐章增量起草] ──> [阶段 3: 交叉审查与修正]
         ▲                                                       │
         └───────────────── 提出调整与增量修订 ───────────────────┘
  ```
  - **规避长篇遗忘**：长篇技术白皮书或架构文档由 Agent 拆解为多个受控小节，每次仅起草一节并主动向人类作者征求确认。
  - **就地修改原则**：保留修改历史与上下文版本锚点，杜绝整篇重写引发的内容跳跃。

---

## 5. 官方技能全景速查对照表

| 技能目录名 | 许可证类型 | 核心依赖技术 | 推荐激活词 (Triggers) |
| :--- | :--- | :--- | :--- |
| `skills/docx` | Source-available | Python (`python-docx`, `lxml`) | "创建 Word 文档", "修订合同", "导出 docx" |
| `skills/xlsx` | Source-available | Python (`openpyxl`) | "制作 Excel 表格", "财务分析表", "公式汇总" |
| `skills/pptx` | Source-available | Python (`python-pptx`) | "生成 PPT", "制作演示文稿", "宽屏汇报" |
| `skills/pdf` | Source-available | Python (`pypdf`, `pymupdf`) | "提取 PDF 表格", "PDF 标注", "合并 PDF" |
| `skills/skill-creator` | Apache-2.0 | Python, Markdown Evals | "编写新技能", "创建 Agent 技能", "评测技能" |
| `skills/mcp-builder` | Apache-2.0 | Python / TypeScript SDK | "创建 MCP Server", "构建 Model Context Protocol" |
| `skills/webapp-testing` | Apache-2.0 | Playwright | "E2E 测试", "自动化回归", "页面截图测试" |
| `skills/algorithmic-art` | Apache-2.0 | JavaScript (`p5.js`) | "生成式艺术", "p5.js 绘图", "算法几何" |
| `skills/frontend-design` | Apache-2.0 | Tailwind CSS, React | "现代网页设计", "UI 界面排版", "避免 AI 质感" |
| `skills/brand-guidelines` | Apache-2.0 | Markdown Checklist | "品牌合规文案", "公关规范起草", "企业视觉约束" |

---

## 6. 权威参考资料与事实依据 (References & Grounding)

- [[Tier 1]] [anthropics/skills Official GitHub](https://github.com/anthropics/skills) - 官方参考实现仓库与技能完整源码 (核验日期: 2026-09-23)
- [[Tier 1]] [Anthropic Support: Claude's Document Capabilities](https://www.anthropic.com/news/create-files) - 官方 Office 文件生成能力发布公告与协议声明 (核验日期: 2026-09-23)
- [[Tier 1]] [Model Context Protocol Specification](https://modelcontextprotocol.io) - MCP 协议工具、资源与提示词规范基线 (核验日期: 2026-09-23)

### 契约核查矩阵：
| 核查对象 (技能/库) | 官方基准事实 (Ground Truth) | 对应依据 | 状态 |
| :--- | :--- | :--- | :--- |
| 办公套件开源协议 | Source-available 源码可用，供学习与二次开发 | anthropics/skills README | 已核实真实有效 |
| 通用创新技能协议 | Apache-2.0 宽松开源协议 | anthropics/skills LICENSE | 已核实真实有效 |
| 电子表格公式规则 | 强制使用 Excel 公式而不是静态数字写入 | `skills/xlsx/SKILL.md` | 已核实真实有效 |
| 幻灯片宽屏基准 | 统一采用 16:9 比例 (13.333 $\times$ 7.5 in) | `skills/pptx/SKILL.md` | 已核实真实有效 |
