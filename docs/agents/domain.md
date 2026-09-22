# 领域文档规范 (Domain Docs)

工程类技能在探索和分析代码库时，如何读取与使用本仓库的领域文档。

## 探索前必读 (Before exploring, read these)

- 仓库根目录下的 **`CONTEXT.md`**，或者
- 仓库根目录下的 **`CONTEXT-MAP.md`**（若存在）—— 它指向各个上下文对应的 `CONTEXT.md`。请阅读与当前任务相关的上下文文档。
- **`docs/adr/`** —— 阅读与你即将开展工作的领域相关的架构决策记录（ADR）。在多上下文仓库中，还需检查 `src/<context>/docs/adr/` 下的上下文级决策。

如果上述任何文件不存在，**请保持静默并直接继续**。无需提示文件缺失，也不要主动提议预先创建。当术语或决策真正达成一致时，`/domain-modeling` 技能（可通过 `/grill-with-docs` 与 `/improve-codebase-architecture` 触发）会按需延迟创建它们。

## 目录结构 (File structure)

单上下文仓库（绝大多数仓库的标准结构）：

```
/
├── CONTEXT.md
├── docs/adr/
│   ├── 0001-event-sourced-orders.md
│   └── 0002-postgres-for-write-model.md
└── src/
```

多上下文仓库（根目录下存在 `CONTEXT-MAP.md`）：

```
/
├── CONTEXT-MAP.md
├── docs/adr/                          ← 系统全局级决策
└── src/
    ├── ordering/
    │   ├── CONTEXT.md
    │   └── docs/adr/                  ← 上下文特定决策
    └── billing/
        ├── CONTEXT.md
        └── docs/adr/
```

## 使用统一词汇表规范 (Use the glossary's vocabulary)

当你的输出涉及领域概念时（如 Issue 标题、重构方案、技术假设、测试用例名称等），必须严格使用 `CONTEXT.md` 中定义的术语。严禁随意使用词汇表中明确避免的近义词或自定义名称。

如果你所需的概念尚未收录在词汇表中，这是一个关键信号 —— 要么是你正在臆造项目未使用的语言（请重新审视），要么是领域模型存在真实缺失（请记录下来交由 `/domain-modeling` 处理）。

## 明确标注 ADR 决策冲突 (Flag ADR conflicts)

如果你的方案或产出与现有的 ADR 产生冲突，必须显式指明，严禁静默覆盖：

> _与 ADR-0007 (event-sourced orders) 存在冲突 —— 但值得重新评估，原因是……_
