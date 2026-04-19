# 同辙 · StratAlign — AI 原生潜力评分标准
# AI-Native Potential Scoring Criteria

---

## 一、评分模型概述 | Scoring Model Overview

AI 原生潜力评分采用三维评分矩阵，衡量业务场景的 AI 化可行性与价值。每个维度独立评分 (1-5)，乘积后经数据基础设施系数修正，得出最终得分。

The AI-Native Potential Score uses a 3-dimension matrix to measure the feasibility and value of AI-enabling a business scenario. Each dimension is scored independently (1-5), multiplied together, then adjusted by the Data Infrastructure Coefficient to produce the final score.

**公式 Formula:**

```
最终得分 Final Score = (规则显性度 × 数据模态 × 决策频率) × 数据基础设施系数
Final Score = (Rule Explicitness × Data Modality × Decision Frequency) × Data Infrastructure Coefficient

理论最高分 Theoretical Max = 5 × 5 × 5 × 1.0 = 125
理论最低分 Theoretical Min = 1 × 1 × 1 × 0.3 = 0.3
```

---

## 二、维度一: 规则显性度 | Dimension 1: Rule Explicitness

> 衡量业务规则的文档化、标准化、可编码程度。
> Measures how well business rules are documented, standardized, and codifiable.

| 评分 Score | 等级 Level | 中文描述 | English Description | 典型特征 Typical Traits |
|---|---|---|---|---|
| **1** | 隐性知识 Implicit Tacit | 完全依赖个人经验和直觉，无任何文档 | Fully dependent on personal experience and intuition, no documentation | 老师傅口口相传；决策逻辑存在于个人脑中；离职即丢失 |
| **2** | 经验规则 Experience-based | 有口头经验传承，少量非正式记录 | Oral experience sharing, minimal informal records | 师徒制传承；有零散笔记但不系统；关键人依赖强 |
| **3** | 部分标准化 Partially Standardized | 有部分 SOP 文档，但不完整或执行不一致 | Partial SOP documentation, incomplete or inconsistently followed | 有 SOP 但覆盖率 <60%；执行偏差常见；定期更新不足 |
| **4** | 高度标准化 Highly Standardized | 完善的 SOP 体系，规则清晰可执行 | Comprehensive SOP system, clear executable rules | SOP 覆盖率 >80%；定期审计更新；例外处理有流程 |
| **5** | 完全显性化 Fully Explicit | 规则已数字化编码，可直接转化为算法 | Rules digitally encoded, directly translatable to algorithms | 决策规则表/决策树已数字化；业务规则引擎已部署；版本管理完善 |

---

## 三、维度二: 数据模态 | Dimension 2: Data Modality

> 衡量相关数据的数字化程度、结构化水平和实时可用性。
> Measures the digitization level, structuredness, and real-time availability of relevant data.

| 评分 Score | 等级 Level | 中文描述 | English Description | 典型特征 Typical Traits |
|---|---|---|---|---|
| **1** | 无数字数据 No Digital Data | 无任何数字化数据，全部纸质或口头 | No digital data at all, entirely paper-based or verbal | 手写单据；电话/口头传递；无电子记录 |
| **2** | 碎片化数据 Fragmented Data | 有部分电子数据但极度分散，格式不统一 | Some electronic data but extremely scattered, inconsistent formats | Excel 文件散落各处；个人电脑存储；无命名规范 |
| **3** | 系统化数据 Systemized Data | 数据存储在业务系统中，但跨系统不通 | Data stored in business systems but siloed across systems | ERP/CRM 各自有数据；系统间靠手工导出；数据口径不一致 |
| **4** | 集成化数据 Integrated Data | 跨系统数据已集成，有统一数据仓库 | Cross-system data integrated, unified data warehouse exists | 数据仓库/数据湖已建设；ETL 流程自动化；主数据管理基本完善 |
| **5** | 实时结构化 Real-time Structured | 结构化实时数据流，高质量数据治理 | Structured real-time data streams, high-quality data governance | 实时数据管道 (Kafka/Flink)；数据质量监控；元数据管理完善 |

---

## 四、维度三: 决策频率 | Dimension 3: Decision Frequency

> 衡量该场景中决策发生的时间频率，频率越高 AI 替代价值越大。
> Measures how frequently decisions occur in the scenario. Higher frequency = greater AI substitution value.

| 评分 Score | 等级 Level | 中文描述 | English Description | 典型特征 Typical Traits |
|---|---|---|---|---|
| **1** | 年度决策 Yearly Strategic | 每年或每季度做一次的战略性决策 | Yearly or quarterly strategic decisions | 年度预算编制；战略规划；组织架构调整 |
| **2** | 月度决策 Monthly Tactical | 每月做一次的战术性决策 | Monthly tactical decisions | 月度排产计划；绩效评估；库存盘点决策 |
| **3** | 每日决策 Daily Operational | 每天需要做的运营性决策 | Daily operational decisions | 每日生产调度；日常审批；订单分配 |
| **4** | 每小时决策 Hourly Responsive | 每小时或更频繁的响应性决策 | Hourly or more frequent responsive decisions | 实时定价调整；客服工单分配；物流路径优化 |
| **5** | 实时决策 Real-time Per-second | 秒级或毫秒级的实时自动决策 | Per-second or millisecond real-time automatic decisions | 欺诈检测；设备异常预警；智能推荐；自动驾驶 |

---

## 五、数据基础设施系数 | Data Infrastructure Coefficient

> 整体数据基础设施的成熟度对所有 AI 场景的落地能力产生乘数效应。
> Overall data infrastructure maturity creates a multiplier effect on all AI scenario implementation ability.

| 状态 State | 描述 Description | 系数 Coefficient | 判定标准 Criteria |
|---|---|---|---|
| **无数据基础** No Data Foundation | 无统一数据管理，各部门各自为政 | **0.3** | 无数据仓库/数据湖；无数据治理流程；无数据团队 |
| **分散数据** Scattered Data | 有部分数据仓库但分散，质量不稳定 | **0.6** | 有局部数据仓库；数据质量不稳定；有兼职数据人员 |
| **结构化数据** Structured Data | 统一数据平台，数据质量可控 | **1.0** | 统一数据平台/中台；数据质量监控体系；专职数据团队 |

---

## 六、评分聚合方法 | Score Aggregation Method

### 6.1 单场景评分 | Single Scenario Scoring

```
场景最终得分 = (D1 × D2 × D3) × C

其中 Where:
  D1 = 规则显性度 Rule Explicitness (1-5)
  D2 = 数据模态 Data Modality (1-5)
  D3 = 决策频率 Decision Frequency (1-5)
  C  = 数据基础设施系数 Data Infrastructure Coefficient (0.3 / 0.6 / 1.0)
```

### 6.2 多场景排序 | Multi-Scenario Ranking

1. 计算每个场景的最终得分 | Calculate final score for each scenario
2. 按得分降序排列 | Sort by score descending
3. 分级推荐 | Tiered recommendations:

| 得分区间 Score Range | 推荐级别 Recommendation Level | 行动建议 Action |
|---|---|---|
| ≥ 60 | 优先启动 Immediate Priority | 立即启动 POC/试点 Start POC/pilot immediately |
| 30-59 | 短期规划 Short-term Plan | 6 个月内纳入规划 Include in 6-month plan |
| 10-29 | 中期储备 Mid-term Reserve | 持续关注，待条件成熟 Monitor, wait for readiness |
| < 10 | 暂缓 Defer | 暂不建议投入 AI Not recommended for AI investment now |

### 6.3 企业 AI 就绪度综合分 | Enterprise AI Readiness Composite Score

```
企业 AI 就绪度 = Top-3 场景平均分 × 数据基础设施系数 × 组织就绪系数
Enterprise AI Readiness = Avg(Top-3 Scenarios) × Data Infra Coeff × Org Readiness Coeff

组织就绪系数 Org Readiness Coefficient:
  无 AI 团队/经验 = 0.5
  有数据团队无 AI 经验 = 0.7
  有 AI 团队且有成功项目 = 1.0
```

---

## 七、实例演示 | Worked Examples

### 实例 1: 制造业质量检测 | Manufacturing Quality Inspection

**场景**: 生产线成品外观质量检测，当前由人工目视检查。

| 维度 Dimension | 评分 Score | 理由 Rationale |
|---|---|---|
| 规则显性度 Rule Explicitness | **4** | 有完善的质量标准文档 (外观缺陷分类表)，检测规则明确 |
| 数据模态 Data Modality | **3** | 有 MES 系统记录不良数据，但图像数据未数字化存储 |
| 决策频率 Decision Frequency | **5** | 每件产品都需判定，秒级频率 |
| 数据基础设施系数 | **0.6** | 有 MES 但图像数据基础薄弱，数据分散 |

```
最终得分 = (4 × 3 × 5) × 0.6 = 60 × 0.6 = 36.0
推荐级别: 短期规划 Short-term Plan
```

**建议**: 优先补齐图像数据采集基础设施 (工业相机+存储)，6 个月内启动 AI 视觉检测 POC。

---

### 实例 2: 财务月度报表 | Financial Monthly Reporting

**场景**: 每月编制管理报表，涉及多系统数据汇总和格式化。

| 维度 Dimension | 评分 Score | 理由 Rationale |
|---|---|---|
| 规则显性度 Rule Explicitness | **5** | 会计准则+公司制度完全标准化，报表格式固定 |
| 数据模态 Data Modality | **4** | ERP 财务模块数据完整，已有数据仓库 |
| 决策频率 Decision Frequency | **2** | 月度编制，频率较低 |
| 数据基础设施系数 | **1.0** | 财务数据基础设施成熟，统一平台 |

```
最终得分 = (5 × 4 × 2) × 1.0 = 40 × 1.0 = 40.0
推荐级别: 短期规划 Short-term Plan
```

**建议**: 虽然决策频率低导致总分不极高，但规则和数据条件极好。适合 RPA + AI 自动生成报表，投入小、见效快，可作为快赢项目。

---

### 实例 3: 客户服务智能应答 | Customer Service Intelligent Response

**场景**: 客服热线 + 在线客服，每日处理 500+ 咨询，涉及产品咨询、投诉、售后。

| 维度 Dimension | 评分 Score | 理由 Rationale |
|---|---|---|
| 规则显性度 Rule Explicitness | **3** | 有 FAQ 知识库但不完整，复杂问题依赖经验 |
| 数据模态 Data Modality | **4** | CRM 系统记录完整对话历史，有结构化工单数据 |
| 决策频率 Decision Frequency | **4** | 每小时数十次响应决策 |
| 数据基础设施系数 | **0.6** | CRM 数据完整但与其他系统 (订单/产品) 集成不足 |

```
最终得分 = (3 × 4 × 4) × 0.6 = 48 × 0.6 = 28.8
推荐级别: 中期储备 Mid-term Reserve
```

**建议**: 数据和频率条件较好，主要瓶颈在规则显性度和系统集成。建议先完善知识库、打通 CRM 与订单系统，再引入智能客服。

---

## 八、注意事项 | Important Notes

1. **评分应基于当前状态** — 评估"现在是什么样"，而非"将来想变成什么样"
   Score based on current state, not aspirational future state

2. **同一企业不同场景可能差异巨大** — 不要一刀切，逐场景独立评分
   Different scenarios within the same enterprise may vary greatly — score each independently

3. **数据基础设施系数是全局性的** — 影响所有场景的最终得分
   Data Infrastructure Coefficient is global — it affects all scenario final scores

4. **低分不代表不能做 AI** — 而是需要先补基础，再做 AI
   Low score doesn't mean AI is impossible — it means foundations need strengthening first

5. **评分是起点而非终点** — 用于优先级排序和投资决策，不是唯一依据
   Scoring is a starting point, not the final word — use for prioritization, not as sole basis

---

*AI 原生潜力评分标准 v0.5.0-beta | AI-Native Potential Scoring Criteria v0.5.0-beta*
