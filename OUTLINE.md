# MatrixOne 产品技术白皮书 · 大纲 / Whitepaper Outline

> 升级版基线 / Upgrade baseline：《MatrixOne 产品白皮书》(2024)
> 目标版本 / Target：v25.x — *One database for everything*（AI-native HTAP + Git-for-Data + 内置向量检索）
> 本文件是**章节框架评审稿**。确认后再逐章撰写正文到 `whitepaper/zh` 与 `whitepaper/en`。
> This file is the **chapter framework for review**. Once approved, chapters are drafted into `whitepaper/zh` and `whitepaper/en`.

---

## 一、定位与一句话主张 / Positioning

| 维度 / Dimension | 2024 旧版 / Old | v25.x 新版 / New（本白皮书）|
| --- | --- | --- |
| 一句话定位 / Tagline | 新一代超融合异构云原生数据库 | **One database for everything**：AI 原生超融合数据库 |
| 核心叙事 / Narrative | 超融合 HSTAP + Serverless，化繁为简 | 在超融合基础上叠加 **Git-for-Data + AI 原生 + Agent 记忆底座** |
| 对标替代 / Replaces | 多个专用数据库 | MySQL + ClickHouse + Elasticsearch + Pinecone |
| 关键新增 / New pillars | — | ① Git for Data ② 向量/全文/混合检索 ③ Agent 记忆与 Intelligence 生态 |

> 🟢 = 沿用 2024 / Kept　🟡 = 升级扩写 / Upgraded　🔵 = 全新章节或内容 / New

---

## 二、章节框架（中英对照）/ Chapter Framework

| # | 文件 / File | 中文标题 | English Title | 状态 |
| --- | --- | --- | --- | --- |
| 00 | `00-preface` | 前言 | Preface | 🟡 |
| 01 | `01-challenges` | AI 时代的数据基础设施挑战 | Data Infrastructure Challenges in the AI Era | 🟡 |
| 02 | `02-trends` | 数据库技术演进趋势 | Database Technology Trends | 🟡 |
| 03 | `03-product-overview` | MatrixOne 产品概览 | MatrixOne Product Overview | 🟡 |
| 04 | `04-architecture` | 云原生技术架构 | Cloud-Native Architecture | 🟡 |
| 05 | `05-storage-engine-tae` | 存储引擎 TAE | Storage Engine: TAE | 🟡 |
| 06 | `06-key-features` | 核心特性 | Key Features | 🟡🔵 |
| 07 | `07-matrixone-cloud` | MatrixOne Cloud 与 Serverless | MatrixOne Cloud & Serverless | 🟢 |
| 08 | `08-matrixone-intelligence` | MatrixOne Intelligence：面向 AI 的数据底座 | MatrixOne Intelligence: Data Backbone for AI | 🔵 |
| 09 | `09-value-benefits` | 应用收益 | Value & Benefits | 🟡 |
| 10 | `10-use-cases` | 应用场景 | Use Cases | 🟡 |
| 11 | `11-about-matrixorigin` | 关于矩阵起源 | About MatrixOrigin | 🟢 |
| A | `appendix` | 附录 | Appendix | 🔵 |

---

## 三、逐章详细大纲 / Detailed Outline

### 00 · 前言 / Preface　🟡
- 关于本白皮书：面向对象、内容范围 / About this whitepaper: audience & scope
- 适用读者：架构师、开发者、DBA、技术决策者、AI 应用团队 / Audience
- 一句话定位与阅读导览 / One-line positioning & reading guide
- 版权、商标与免责声明 / Copyright, trademark & disclaimer（沿用 2024 法务文本）

### 01 · AI 时代的数据基础设施挑战 / Data Infrastructure Challenges in the AI Era　🟡
> 基线：2024 第 01 章；升级点：把"AIGC 挑战"扩展为"GenAI + Agent 时代"，强化记忆/多模态/实时。
- 1.1 架构挑战：专用数据库泛滥，IT 架构日益复杂 / Sprawl of specialized databases　🟢
  - 数据库从十几种到数百种、选型清单、数据孤岛、开发者负担
- 1.2 应用挑战：基础设施与应用需求的矛盾 / Infrastructure vs. application needs　🟢
  - 企业软件 / SaaS / 智能物联网 / 数智中台四类场景的两难
- 1.3 AI 挑战：GenAI 与 Agent 时代的数据新需求 / New demands of the GenAI & agent era　🟡
  - 多模态、向量、实时新鲜度、Agent 长期记忆与上下文
- 1.4 专用向量数据库的局限："又一个数据孤岛" / The "yet another silo" problem of bolt-on vector DBs　🟡
  - 数据重复、ETL、一致性、授权成本、缺失 DBMS 级完整性

### 02 · 数据库技术演进趋势 / Database Technology Trends　🟡
> 基线：2024 第 02 章；升级点：新增 2.4「数据版本化 / Git-for-Data」趋势。
- 2.1 数据引擎能力迈向融合 / Convergence of data engines　🟢
  - NewSQL · HTAP · 流批一体 · 湖仓一体 → **HSTAP**
- 2.2 云原生技术逐步成熟 / Maturing cloud-native foundations　🟢
  - Kubernetes（统一 OS）· Serverless · 对象存储成为事实标准
- 2.3 从 Cloud Native 到 AI Native / From cloud-native to AI-native　🟡
  - 向量需求爆发、Text2SQL 降低门槛、BI+AI 融合
- 2.4 数据版本化与 Git-for-Data 趋势 / Data versioning & the Git-for-Data trend　🔵
  - 实验隔离、可回溯、可审计；AI 训练集/验证集的版本化需求

### 03 · MatrixOne 产品概览 / MatrixOne Product Overview　🟡
> 基线：2024 第 03.1–03.3；升级点：定位语升级为 One database for everything、加入 AI 原生。
- 3.1 什么是 MatrixOne / What is MatrixOne　🟡
  - 一套存储 + 一套计算引擎，支持 TP / AP / 流 / 时序 / 向量 / 全文
- 3.2 设计理念：从「多」到「少」、从「具体」到「抽象」/ Design philosophy　🟢
  - 超融合（融合理念）+ Serverless（抽象屏蔽）+ **AI 原生**
- 3.3 核心能力总览 / Core capabilities at a glance　🟡
  - 超融合引擎 · 异构云原生 · 极致性能 · **Git-for-Data · AI 原生**
- 3.4 产品形态 / Editions / Product forms　🟢
  - 社区版 / 企业版 / MatrixOne Cloud

### 04 · 云原生技术架构 / Cloud-Native Architecture　🟡
> 基线：2024 第 03.4 + 03.5；升级点：拆为独立架构章，深化三层解耦与组件职责。
- 4.1 整体架构：计算 / 事务 / 共享存储三层解耦 / Three-layer disaggregation　🟢
- 4.2 计算层 CN：无状态、Serverless、多级缓存、负载隔离 / Compute layer (CN)　🟢
  - CNSet / CN Group · MatrixOne Proxy 会话级 SQL 路由
- 4.3 事务层 TN：分布式事务、冲突检测、隔离级别 / Transaction layer (TN)　🟢
  - SI / RC 隔离级别，乐观 / 悲观事务模型
- 4.4 共享存储层：对象存储 + LogService / Shared storage & LogService　🟢
  - Multi-Raft 共享日志、dragonboat、低延迟提交、异步转存对象存储
- 4.5 三大解耦：存算分离 / 读写分离 / 冷热分离 / The three separations　🟢
- 4.6 [架构图] 组件全景 / [Diagram] component panorama　🔵（待绘制）

### 05 · 存储引擎 TAE / Storage Engine: TAE　🟡
> 基线：2024「高性价比存储引擎」段落；升级点：独立成章，补充数据组织细节。
- 5.1 TAE 设计目标：事务 + 分析一体 / Unified transaction + analytics　🟢
- 5.2 行列混合存储与 Column Family / Hybrid row-column storage　🟢
- 5.3 File Service：异构存储介质抽象 / File Service abstraction　🟢
- 5.4 分级存储与多级缓存（内存 + 本地盘 + 对象存储）/ Tiered storage & caching　🟢
- 5.5 数据组织：Checkpoint / LogTail / Snapshot / Data organization　🔵
- 5.6 纠删码与冗余（~150% 冗余的高可用）/ Erasure coding & redundancy　🔵（待核实数据）

### 06 · 核心特性 / Key Features　🟡🔵
> 基线：2024 第 03.5 重点特性；升级点：新增 Git-for-Data、扩写 AI 原生（向量+全文+混合检索+Pinecone 兼容）。
- 6.1 超融合 HSTAP：一份数据多种负载、无 ETL / HSTAP, one data many workloads　🟢
- 6.2 **Git for Data** / Git for Data　🔵 ★
  - 毫秒级零拷贝快照 · 时间旅行查询 · 分支与合并 · 即时回滚 · 不可变审计
  - 价值：AI 训练集版本化、实验隔离、合规审计
- 6.3 **AI 原生：向量与全文检索** / AI-native: vector & full-text search　🟡🔵 ★
  - 向量类型（vecf32 / vecf64）· IVF / HNSW 索引 · 全文检索
  - 混合检索（标量 + 向量 + 全文）· **Pinecone 兼容 API** · RAG 支持 · 库内 ML
- 6.4 内置流引擎与增量物化视图（IVM）/ Built-in streaming & incremental materialized views　🟢
- 6.5 分布式高可用（Multi-Raft）/ Distributed high availability　🟢
- 6.6 企业级安全与合规（RBAC / TLS / 加密 / 审计）/ Enterprise security & compliance　🟢
- 6.7 MySQL 兼容性（协议 / 语法 / 生态工具，兼容 8.0）/ MySQL compatibility　🟢

### 07 · MatrixOne Cloud 与 Serverless / MatrixOne Cloud & Serverless　🟢
> 基线：2024 第 04 章，基本沿用，核对最新计费与可用区。
- 7.1 什么是 MatrixOne Cloud / What is MatrixOne Cloud
- 7.2 Serverless 数据服务模式：两级平台 + 四级主体（组织/成员/实例/数据库）/ Serverless model
- 7.3 按 SQL 计费：CU（Compute Unit）与消费速率控制 / CU-based billing
- 7.4 核心特性：零门槛 / 全托管 / Serverless SQL / 多租户 / 极速分析 / 多云 / Core features

### 08 · MatrixOne Intelligence：面向 AI 的数据底座 / Data Backbone for AI　🔵
> 全新章节，作为产品白皮书与《Intelligence 解决方案白皮书》之间的桥梁；本章概述，细节引用解决方案白皮书。
- 8.1 从数据库到 AI 数据智能平台 / From database to AI data intelligence platform
- 8.2 生态组件总览 / Ecosystem components
  - MatrixDC（算网调度）· MatrixPipeline（多模态数据工程）· MatrixGenesis（模型/Agent 开发）· MatrixSearch（多模态检索）
- 8.3 Agent 记忆底座与 Memoria / Agent memory backbone & Memoria
  - 长期上下文、防幻觉、数据一致性
- 8.4 RAG 与多模态协同：库内向量检索 × 解决方案 / RAG & multimodal synergy
  - > 详见《MatrixOne Intelligence 解决方案白皮书》/ See the Intelligence solution whitepaper

### 09 · 应用收益 / Value & Benefits　🟡
> 基线：2024 第 05 章；升级点：把 AI 收益并入。
- 9.1 极简开发：技术栈从 6+ 收敛到 1，无需 ETL / Radically simpler stack　🟢
- 9.2 高扩展性：独立、动态、自主弹性 / Independent, dynamic, elastic scaling　🟢
- 9.3 高性价比：更高性能、更低成本（对象存储 + 向量化执行 + 按量付费）/ Performance & cost　🟢
- 9.4 高灵活性：任意类型 / 任意负载 / 任意环境（含向量/多模态）/ Flexibility　🟡

### 10 · 应用场景 / Use Cases　🟡
> 基线：2024 第 06 章；升级点：扩写 AI/RAG/Agent 场景，补充最新客户案例。
- 10.1 物联网数据平台 / IoT data platform　🟢
- 10.2 企业 SaaS 服务 / Enterprise SaaS　🟢
- 10.3 实时看板与分析应用 / Real-time dashboards & analytics　🟢
- 10.4 AI / RAG / Agent 智能应用 / AI, RAG & agent applications　🟡🔵
- 10.5 客户案例精选（极视角 / 深智城 / 江西铜业 / 金意陶 / 素问 等）/ Selected customer stories　🔵
  - > 案例可复用《Intelligence 解决方案白皮书》/ Reuse from the Intelligence whitepaper

### 11 · 关于矩阵起源 / About MatrixOrigin　🟢
> 基线：2024 结尾；核对最新资质与荣誉。
- 11.1 公司简介 / Company overview
- 11.2 资质与荣誉（信通院 HTAP 可信数据库、高新技术企业、国产化适配等）/ Certifications & honors
- 11.3 社区与开源 / Community & open source
- 11.4 联系方式 / Contact

### 附录 / Appendix　🔵
- A. 术语表 / Glossary：HSTAP · TAE · CN · TN · LogService · CNSet · CU · IVM · RBAC · IVF · HNSW · RAG
- B. 架构图清单 / Diagram index
- C. 版本与文档对照 / Version & docs mapping
- D. 参考资料 / References

---

## 四、需要绘制的图 / Diagrams To Produce

| 编号 | 章节 | 图示内容 / Content |
| --- | --- | --- |
| FIG-1 | 03/04 | 三层解耦总体架构（计算/事务/共享存储 + 云服务）/ Overall 3-layer architecture |
| FIG-2 | 04 | 请求路径与数据流（SQL → CN → TN → LogService → 对象存储）/ Request & data flow |
| FIG-3 | 05 | TAE 存储引擎内部结构 / TAE internals |
| FIG-4 | 06.2 | Git for Data：快照/分支/时间旅行示意 / Git-for-Data concept |
| FIG-5 | 06.3 | 混合检索流程（标量+向量+全文）/ Hybrid search pipeline |
| FIG-6 | 08 | MatrixOne Intelligence 生态全景 / Intelligence ecosystem |

---

## 五、待核实 / 待补充清单 / To Verify & Fill

- [ ] 最新版本号与版本命名（v25.x 具体版本）/ Latest version & naming
- [ ] 性能数据（TPC-C / TPC-H / 向量检索 QPS、收益百分比）/ Benchmarks & ROI figures
- [ ] 纠删码冗余比例、副本数等存储参数 / Storage params (EC ratio, replicas)
- [ ] Pinecone 兼容 API 的具体覆盖范围 / Pinecone-compatible API scope
- [ ] 向量索引支持的距离度量与维度上限 / Vector index metrics & dimension limits
- [ ] MatrixOne Cloud 支持的云厂商与可用区现状 / Cloud providers & regions
- [ ] 最新资质荣誉、客户案例与授权数据 / Latest honors & customer numbers
- [ ] Memoria / Intelligence 各组件的最新命名与能力边界 / Latest ecosystem naming

> ⚠️ 以上均以官方文档 <https://docs.matrixorigin.cn> 与源码 <https://github.com/matrixorigin/matrixone> 为准。
