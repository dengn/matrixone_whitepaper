# MatrixOne Whitepaper · MatrixOne 技术白皮书

> One database for everything —— AI 原生、超融合（HSTAP）、Git-for-Data 的云原生数据库
> An AI-native, hyper-converged (HSTAP), cloud-native database with Git-for-Data

本仓库用于撰写与持续更新 **MatrixOne 最新产品技术白皮书**，采用 **中英双语 / Markdown** 形式维护。
This repository hosts the **latest MatrixOne product & technical whitepaper**, maintained as **bilingual (Chinese + English) Markdown**.

> **升级基线 / Upgrade baseline**：在 2024 版《MatrixOne 产品白皮书》的成熟结构上，
> 升级到 **v25.x** 最新定位 —— *One database for everything*（AI 原生 HSTAP + Git-for-Data + 内置向量检索 + Agent 记忆底座）。
> Built on the proven structure of the 2024 *MatrixOne Product Whitepaper*, upgraded to the **v25.x** positioning.

---

## 📌 当前状态 / Current Status

| 阶段 / Phase | 状态 / Status |
| --- | --- |
| 大纲与目录结构 / Outline & structure | ✅ 已完成初稿 / First draft done |
| 章节正文 / Chapter drafts | 🚧 待逐章撰写 / Pending, chapter by chapter |
| 架构图 / Diagrams | ⬜ 待绘制 / To be drawn |
| 性能数据核实 / Benchmark verification | ⬜ 待补充与核实 / TBD |
| 中英对齐校对 / Bilingual proofreading | ⬜ 未开始 / Not started |

> 👉 章节大纲是本轮的核心交付物，请先评审 **[OUTLINE.md](./OUTLINE.md)**。
> 👉 The outline is this round's key deliverable — please review **[OUTLINE.md](./OUTLINE.md)** first.

---

## 🗂️ 目录结构 / Repository Structure

```text
matrixone_whitepaper/
├── README.md                 # 本文件 / This file
├── OUTLINE.md                # 主大纲（中英双语）/ Master bilingual outline ★
├── whitepaper/
│   ├── zh/                   # 中文章节 / Chinese chapters
│   │   ├── 00-executive-summary.md
│   │   ├── 01-introduction.md
│   │   └── ...
│   └── en/                   # 英文章节 / English chapters（与 zh 一一对应 / mirrors zh）
│       ├── 00-executive-summary.md
│       └── ...
└── assets/
    └── diagrams/             # 架构图与示意图 / Architecture & illustration diagrams
```

**双语策略 / Bilingual strategy**：中英文各自独立成文，文件名一一对应（`zh/NN-*.md` ↔ `en/NN-*.md`），
便于最终各自排版为干净的单语 PDF；`OUTLINE.md` 中并排呈现中英结构，方便整体评审。
Chinese and English are kept as separate, mirrored files (`zh/NN-*.md` ↔ `en/NN-*.md`) so each can be
typeset into a clean monolingual PDF, while `OUTLINE.md` presents both side by side for holistic review.

---

## ✍️ 写作流程 / Authoring Workflow

1. **大纲先行 / Outline first** —— 在 `OUTLINE.md` 中确定章节框架（本轮）。
2. **逐章填充 / Chapter by chapter** —— 评审通过后，按章节填充 `whitepaper/zh` 与 `whitepaper/en`。
3. **配图 / Diagrams** —— 在 `assets/diagrams/` 补充架构图，正文引用。
4. **核实 / Verify** —— 性能数据、版本号、特性以 [官方文档](https://docs.matrixorigin.cn) 与
   [matrixorigin/matrixone](https://github.com/matrixorigin/matrixone) 为准。
5. **校对 / Proofread** —— 中英对齐、术语统一（见附录术语表）。

---

## 📚 主要参考 / Key References

**基线白皮书 / Baseline whitepapers（Google Drive，私有）：**
- 《MatrixOne 产品白皮书》(2024) —— 本次升级的**主基线** / primary baseline
- 《2025 MatrixOne Intelligence 多模态 AI 数据智能解决方案白皮书》—— 第 08 章及案例参考 / referenced in Ch.08 & cases

**官方公开资料 / Official public sources：**
- 官网 / Official site：<https://www.matrixorigin.io/matrixone>
- 文档 / Docs：<https://docs.matrixorigin.cn>
- 源码 / Source：<https://github.com/matrixorigin/matrixone>
- 系统架构 / System architecture：<https://medium.com/@matrixorigin-database/matrixone-system-architecture-8d4de36649ea>
- 产品体系演进 / Product evolution：<https://www.matrixorigin.io/posts/MatrixOne-MatrixOS>
- GPU 向量检索 / GPU vector search (cuVS)：<https://www.matrixorigin.io/blog/matrixone-nvidia-cuvs-vector-search>
- 智能体记忆 / Agent memory：<https://github.com/matrixorigin/Memoria>

> ⚠️ 所有技术细节、版本号与性能数据在定稿前需对照官方最新资料核实。
> ⚠️ All technical details, version numbers and benchmarks must be verified against official sources before finalizing.
