# 深略 · StratAlign — AI 原生潜力评分标准
# AI-Native Potential Scoring Criteria

<!-- LANGUAGE HANDLING INSTRUCTIONS:
This file contains bilingual content (Chinese + English) for all scoring criteria and examples.
The engine MUST respect the user's language selection:

- CHINESE MODE: Use Chinese descriptions, Chinese column headers, Chinese consultant notes.
  Keep English abbreviations/formulas as-is (e.g., "NPV", "D1×D2", "Cs").
- ENGLISH MODE: Use English descriptions, English column headers, English consultant notes.
  All formulas remain the same.

When generating the AI scoring matrix output:
  - Chinese: 维度/Dimension headers in Chinese, 推荐级别 in Chinese
  - English: Dimension headers in English, Tier recommendations in English
-->

---

## 一、评分模型概述 | Scoring Model Overview

AI 原生潜力评分采用**加权求和模型**，通过四个维度的加权合计衡量业务场景的 AI 化可行性与价值，再经场景级数据系数修正，得出最终得分（归一化至 0-100 分）。

The AI-Native Potential Score uses a **weighted additive model** across four dimensions to measure the feasibility and value of AI-enabling a business scenario. The weighted sum is then adjusted by a per-scenario data coefficient to produce the final score (normalized to 0-100).

### 为什么采用加权求和而非乘积模型 | Why Weighted Sum Instead of Multiplication

旧版模型采用纯乘积公式 (D1 x D2 x D3 x C)，存在严重的"短板放大"问题：任何一个维度得分低，就会将最终得分拉至谷底。例如一个场景在规则显性度、数据模态上表现优秀 (均为 5)，但决策频率仅为 1（年度战略决策），乘积模型给出 5 x 5 x 1 = 25，完全淹没了其他维度的优势。

The previous version used a pure multiplication formula (D1 x D2 x D3 x C), which suffered from severe "weak-link amplification": one low dimension would tank the entire score. For example, a scenario excelling in Rule Explicitness and Data Modality (both 5) but with Decision Frequency of 1 (yearly strategic) would yield 5 x 5 x 1 = 25, completely drowning out the strengths of other dimensions.

加权求和模型提供更平衡的视角——每个维度对最终评分贡献一个可控的权重比例，弱势维度会降低总分但不会"归零"整个评估。这更符合实际咨询场景中的多因素综合判断逻辑。

The weighted sum model provides a more balanced perspective — each dimension contributes a controlled weight proportion to the final score. A weak dimension lowers the total but does not "zero out" the entire assessment. This better reflects the multi-factor holistic judgment logic in real consulting engagements.

### 公式 Formula

```
AI 潜力得分 = (w1 x D1 + w2 x D2 + w3 x D3 + w4 x D4) x 4 x Cs
AI Potential Score = (w1 x D1 + w2 x D2 + w3 x D3 + w4 x D4) x 4 x Cs

其中 Where:
  D1 = 规则显性度 Rule Explicitness (1-5)
  D2 = 数据模态 Data Modality (1-5)
  D3 = 决策频率 Decision Frequency (1-5)
  D4 = 实施复杂度 Implementation Complexity (1-5, 分越高越容易实施)
  w1..w4 = 维度权重 Dimension Weights (合计 = 1.0)
  Cs = 场景级数据系数 Per-Scenario Data Coefficient (0.4 / 0.6 / 0.8 / 1.0)

加权和的理论范围 Weighted sum theoretical range: 1.0 - 5.0
乘以 4 归一化至 Multiply by 4 to normalize to: 4.0 - 20.0
再乘以 Cs 得出最终得分 Then multiply by Cs for final score:
  理论最高分 Theoretical Max = 5.0 x 4 x 1.0 = 20.0 -> 标准化为 100
  理论最低分 Theoretical Min = 1.0 x 4 x 0.4 = 1.6 -> 标准化为 8

标准化公式 Normalization:
  标准化得分 Normalized Score = [(加权和 Weighted Sum - 1) / (5 - 1)] x 100 x Cs
  即 i.e. = [(w1xD1 + w2xD2 + w3xD3 + w4xD4) - 1] / 4 x 100 x Cs

当所有维度 = 5 且 Cs = 1.0 时，得分 = 100
When all dimensions = 5 and Cs = 1.0, score = 100
当所有维度 = 1 且 Cs = 0.4 时，得分 = 0
When all dimensions = 1 and Cs = 0.4, score = 0
```

### 默认权重 Default Weights

| 维度 Dimension | 默认权重 Default Weight | 权重理由 Rationale |
|---|---|---|
| D1 规则显性度 Rule Explicitness | **25%** (w1 = 0.25) | 规则可编码性是 AI 落地的基础前提 |
| D2 数据模态 Data Modality | **30%** (w2 = 0.30) | 数据是 AI 模型的燃料，权重最大 |
| D3 决策频率 Decision Frequency | **20%** (w3 = 0.20) | 频率决定 ROI 放大倍数 |
| D4 实施复杂度 Implementation Complexity | **25%** (w4 = 0.25) | 落地可行性直接影响项目成败 |

> **顾问可调整权重**: 以上为默认配置。顾问可根据客户具体情况调整权重（例如：对于数据基础极度薄弱的企业，可提高 D2 权重至 40%；对于高度监管行业，可提高 D4 权重至 30%）。调整后权重总和必须等于 1.0。
>
> **Consultants may adjust weights**: The above are defaults. Consultants can adjust weights based on client context (e.g., raise D2 to 40% for enterprises with extremely weak data foundations; raise D4 to 30% for highly regulated industries). Adjusted weights must sum to 1.0.

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

## 五、维度四: 实施复杂度 | Dimension 4: Implementation Complexity

> 衡量在该场景中实际落地 AI 的工程与组织复杂度。**分数越高，实施越容易，AI 采纳前景越好。**
> Measures the engineering and organizational complexity of actually implementing AI for this scenario. **Higher score = easier to implement = more favorable for AI adoption.**

| 评分 Score | 等级 Level | 中文描述 | English Description | 典型特征 Typical Traits |
|---|---|---|---|---|
| **1** | 极端复杂 Extremely Complex | 需要跨组织变革、新建基础设施、监管审批 | Requires cross-org change, new infrastructure, regulatory approval | 涉及多部门流程再造；需全新 IT 基础设施；需行业监管审批（如医疗、金融）；实施周期 >18 个月 |
| **2** | 高复杂度 High Complexity | 多系统集成、显著流程变更 | Multi-system integration, significant process change | 需对接 3+ 个系统；涉及核心业务流程改造；需组建专项实施团队；实施周期 12-18 个月 |
| **3** | 中等复杂 Moderate | 单系统增强、部分流程调整 | Single system enhancement, some process adjustment | 在现有系统上扩展功能；影响 1-2 个部门工作流程；可用现有团队 + 外部支持；实施周期 6-12 个月 |
| **4** | 低复杂度 Low Complexity | 独立工具部署、最小流程变更 | Standalone tool deployment, minimal process change | 独立工具/模块；不改变核心业务流程；仅需小范围培训；实施周期 3-6 个月 |
| **5** | 即插即用 Plug-and-play | SaaS/API 接入，无需基础设施变更 | SaaS/API integration, no infrastructure change needed | 直接调用云服务 API；无需本地部署；按量付费；上线周期 < 1 个月 |

---

## 六、场景级数据系数 | Per-Scenario Data Coefficient

> 每个场景拥有独立的数据系数，反映**该具体场景**的数据就绪程度，而非企业整体数据基础设施水平。同一企业中不同场景的数据就绪度可能天差地别——财务数据可能非常完整，而车间图像数据可能尚未采集。
>
> Each scenario receives its own data coefficient reflecting the data readiness for **that specific scenario**, not the enterprise-level data infrastructure. Different scenarios within the same company may have vastly different data readiness — financial data may be comprehensive while shopfloor image data may not yet be collected.

| 系数 Coefficient | 数据状态 Data State | 中文描述 | English Description | 判定标准 Criteria |
|---|---|---|---|---|
| **0.4** | 无相关数据 No Relevant Data | 该场景无可用的数字化数据 | No usable digital data for this scenario | 该场景的核心数据尚未采集或数字化；需从零建设数据管道 |
| **0.6** | 分散/部分数据 Scattered/Partial | 有部分数据但分散、不完整 | Some data exists but scattered, incomplete | 数据分散在多处（Excel、邮件、个人电脑）；覆盖率 <50%；质量不稳定 |
| **0.8** | 已集成但有缺口 Integrated with Gaps | 数据已基本集成但存在质量或覆盖缺口 | Data largely integrated but quality/coverage gaps exist | 有集中存储；核心字段覆盖率 >70%；部分数据质量问题待解决 |
| **1.0** | 完整结构化 Complete Structured | 该场景数据完整、结构化、高质量 | Complete, structured, high-quality data for this scenario | 数据完整且有质量保障；已有自动化数据管道；可直接用于模型训练/推理 |

---

## 七、评分聚合方法 | Score Aggregation Method

### 7.1 单场景评分 | Single Scenario Scoring

```
步骤 Steps:

1. 四维度评分 Score four dimensions:
   D1 = 规则显性度 (1-5)
   D2 = 数据模态 (1-5)
   D3 = 决策频率 (1-5)
   D4 = 实施复杂度 (1-5)

2. 加权求和 Weighted sum:
   加权和 WS = w1 x D1 + w2 x D2 + w3 x D3 + w4 x D4
   (默认 Default: WS = 0.25 x D1 + 0.30 x D2 + 0.20 x D3 + 0.25 x D4)

3. 归一化 Normalize to 0-100:
   基础分 Base Score = (WS - 1) / 4 x 100

4. 场景数据系数修正 Apply per-scenario data coefficient:
   最终得分 Final Score = Base Score x Cs
```

### 7.2 多场景排序与分级 | Multi-Scenario Ranking and Tiering

1. 计算每个场景的最终得分 | Calculate final score for each scenario
2. 按得分降序排列 | Sort by score descending
3. 分级推荐 | Tiered recommendations:

| 得分区间 Score Range | 推荐级别 Tier | 行动建议 Action |
|---|---|---|
| **>= 75** | **Tier 1: 立即启动** Immediate Priority | 高度适合 AI 化，立即启动 POC/试点项目 — Highly suited for AI, start POC/pilot immediately |
| **50 - 74** | **Tier 2: 短期规划** Short-term Plan | 条件基本具备，6 个月内纳入实施规划 — Conditions largely met, include in 6-month implementation plan |
| **25 - 49** | **Tier 3: 夯实基础** Foundation First | 存在关键短板需先补齐，制定 6-12 个月基础建设路线图 — Key gaps need filling first, create 6-12 month foundation roadmap |
| **< 25** | **Tier 4: 暂缓** Defer | 当前条件不成熟，暂不建议投入 AI，持续关注 — Conditions not yet mature, not recommended for AI investment now, monitor |

### 7.3 企业 AI 就绪度综合分 | Enterprise AI Readiness Composite Score

```
企业 AI 就绪度 = Avg(Top-3 场景最终得分) x 组织就绪系数
Enterprise AI Readiness = Avg(Top-3 Scenario Final Scores) x Org Readiness Coefficient

组织就绪系数 Org Readiness Coefficient:
  无 AI 团队/经验 No AI team or experience           = 0.6
  有数据团队无 AI 经验 Data team, no AI experience    = 0.8
  有 AI 团队且有成功项目 AI team with success record  = 1.0
```

> 注: 场景最终得分已包含各自的场景级数据系数，因此企业级公式中不再重复乘以数据基础设施系数。
> Note: Scenario final scores already incorporate their per-scenario data coefficients, so the enterprise formula does not multiply by a data infrastructure coefficient again.

---

## 八、敏感性分析 | Sensitivity Analysis

> 敏感性分析帮助顾问和决策者理解评分的稳健性：哪些维度的变化对最终得分影响最大？评分是否处于级别边界附近？是否存在一个维度的微小变化就会改变推荐级别的风险？
>
> Sensitivity analysis helps consultants and decision-makers understand score robustness: which dimensions have the greatest impact on the final score? Is the score near a tier boundary? Is there a risk that a small change in one dimension could flip the recommendation?

### 8.1 单维度影响分析模板 | Single-Dimension Impact Analysis Template

对于已评分的场景，逐维度计算 +/-1 分的影响:

For a scored scenario, calculate the impact of +/-1 point change per dimension:

| 维度 Dimension | 当前分 Current | -1 分后得分 Score at -1 | +1 分后得分 Score at +1 | 得分变化幅度 Score Delta | 是否跨级 Tier Change? |
|---|---|---|---|---|---|
| D1 规则显性度 | _ | _ | _ | _ | _ |
| D2 数据模态 | _ | _ | _ | _ | _ |
| D3 决策频率 | _ | _ | _ | _ | _ |
| D4 实施复杂度 | _ | _ | _ | _ | _ |

**计算方法 Calculation method**: 将目标维度增减 1 分（不超过 1-5 范围），其余维度和 Cs 保持不变，重新计算最终得分。

Change the target dimension by +/-1 (clamped to 1-5 range), keep all other dimensions and Cs unchanged, recalculate the final score.

### 8.2 龙卷风图概念 | Tornado Diagram Concept

龙卷风图以条形图形式直观展示每个维度的影响力排序。条越长，说明该维度对最终得分的影响越大。

A tornado diagram visually ranks each dimension's influence as horizontal bars. The longer the bar, the greater that dimension's impact on the final score.

在默认权重下，单维度变化 1 分对最终得分的影响:

Under default weights, the impact of a 1-point change in a single dimension on the final score:

```
影响力排序 (默认权重, Cs = 1.0):
Impact ranking (default weights, Cs = 1.0):

  D2 数据模态 (30%)     : +/- 7.5 分 points   ████████████████
  D1 规则显性度 (25%)    : +/- 6.25 分 points  █████████████
  D4 实施复杂度 (25%)    : +/- 6.25 分 points  █████████████
  D3 决策频率 (20%)      : +/- 5.0 分 points   ██████████

  注: 实际影响需乘以 Cs。例如 Cs=0.6 时，D2 的影响为 +/- 4.5 分
  Note: Actual impact is multiplied by Cs. E.g., with Cs=0.6, D2 impact = +/- 4.5 points
```

### 8.3 盈亏平衡分析 | Break-even Analysis

当场景得分接近级别边界时（75、50、25），需要回答：**"哪个维度需要变化多少分才会改变推荐级别？"**

When a scenario score is near a tier boundary (75, 50, 25), the key question is: **"Which dimension needs to change by how much to flip the recommendation tier?"**

**方法 Method:**

```
1. 确定当前得分与最近级别边界的差值 Delta
   Determine the gap (Delta) between current score and the nearest tier boundary

2. 对每个维度计算: 需要变化几分才能弥补 Delta
   For each dimension: how many points of change are needed to bridge Delta

   所需变化 = Delta / (wi / 4 x 100 x Cs)
   Required change = Delta / (wi / 4 x 100 x Cs)

3. 若所需变化 < 1 分，标记为"高敏感"——评估误差可能导致级别翻转
   If required change < 1 point, flag as "high sensitivity" — scoring error could flip the tier
```

---

> ### 顾问指引 | Consultant Guidance
>
> **如何使用本评分体系 How to use this scoring system:**
>
> 1. **权重调整 Weight adjustment**: 默认权重适用于大多数场景。如需调整，应在项目启动阶段与客户对齐并记录理由，且同一次评估中的所有场景必须使用相同权重，以保证可比性。
>    Default weights work for most scenarios. If adjusting, align with the client at project kickoff and document rationale. All scenarios within the same assessment must use identical weights to ensure comparability.
>
> 2. **何时覆盖得分 When to override scores**: 以下情况顾问可标注"手动覆盖"并记录理由: (a) 得分处于级别边界且敏感性分析显示高不确定性; (b) 存在模型未覆盖的关键外部因素（如政策变化、已签约合作伙伴）; (c) 客户高层有明确战略意图且愿承担风险。所有覆盖必须在交付报告中注明。
>    Consultants may mark "manual override" with documented rationale when: (a) score is at a tier boundary and sensitivity analysis shows high uncertainty; (b) critical external factors not captured by the model exist (e.g., policy changes, committed partners); (c) client leadership has clear strategic intent and accepts the risk. All overrides must be noted in the deliverable report.
>
> 3. **危险信号 Red flags to watch for**:
>    - 客户对多个场景评分高度一致（如全部 3-3-3-3）——可能是缺乏独立思考的"安全评分"，需要用具体案例逐场景挑战
>      Uniformly similar scores across many scenarios (e.g., all 3-3-3-3) — likely "safe scoring" without independent thought, challenge with specific examples per scenario
>    - D1 评分 >= 4 但无法提供实际 SOP 文档——高估规则显性度是最常见的偏差
>      D1 scored >= 4 but no actual SOP documents available — overestimating rule explicitness is the most common bias
>    - D4 评分 = 5 但场景涉及核心业务系统——可能低估了集成复杂度
>      D4 scored 5 but scenario involves core business systems — likely underestimating integration complexity
>    - Cs = 1.0 但企业没有统一数据平台——需要用数据采样验证
>      Cs = 1.0 but enterprise has no unified data platform — verify with data sampling
>    - 客户回避敏感性分析讨论——可能对评估结果缺乏信心
>      Client avoids sensitivity analysis discussion — may lack confidence in assessment results

---

## 九、实例演示 | Worked Examples

### 实例 1: 制造业质量检测 | Manufacturing Quality Inspection

**场景**: 生产线成品外观质量检测，当前由人工目视检查。
**Scenario**: Final product appearance quality inspection on production line, currently done by manual visual inspection.

| 维度 Dimension | 评分 Score | 理由 Rationale |
|---|---|---|
| D1 规则显性度 Rule Explicitness | **4** | 有完善的质量标准文档（外观缺陷分类表），检测规则明确 — Comprehensive quality standard docs (defect classification table), clear inspection rules |
| D2 数据模态 Data Modality | **3** | 有 MES 系统记录不良数据，但图像数据未数字化存储 — MES records defect data, but image data not digitally stored |
| D3 决策频率 Decision Frequency | **5** | 每件产品都需判定，秒级频率 — Every product requires judgment, per-second frequency |
| D4 实施复杂度 Implementation Complexity | **3** | 需加装工业相机和采集系统，但不改变产线核心流程 — Requires adding industrial cameras and collection system, but does not change core production flow |
| Cs 场景数据系数 | **0.6** | MES 数据可用但图像数据基础薄弱，需新建采集管道 — MES data available but image data foundation weak, new collection pipeline needed |

**计算 Calculation:**

```
加权和 Weighted Sum = 0.25 x 4 + 0.30 x 3 + 0.20 x 5 + 0.25 x 3
                    = 1.00 + 0.90 + 1.00 + 0.75
                    = 3.65

基础分 Base Score = (3.65 - 1) / 4 x 100 = 66.25

最终得分 Final Score = 66.25 x 0.6 = 39.75

推荐级别 Tier: Tier 3 — 夯实基础 Foundation First
```

**建议**: 优先补齐图像数据采集基础设施（工业相机 + 存储），将 Cs 提升至 0.8 后得分可达 53.0（进入 Tier 2 短期规划），届时可启动 AI 视觉检测 POC。

**Recommendation**: Prioritize building image data collection infrastructure (industrial cameras + storage). Once Cs improves to 0.8, the score would reach 53.0 (entering Tier 2 Short-term Plan), at which point an AI visual inspection POC can be initiated.

---

### 实例 2: 财务月度报表 | Financial Monthly Reporting

**场景**: 每月编制管理报表，涉及多系统数据汇总和格式化。
**Scenario**: Monthly management report preparation, involving multi-system data aggregation and formatting.

| 维度 Dimension | 评分 Score | 理由 Rationale |
|---|---|---|
| D1 规则显性度 Rule Explicitness | **5** | 会计准则 + 公司制度完全标准化，报表格式固定 — Accounting standards + company policies fully standardized, report format fixed |
| D2 数据模态 Data Modality | **4** | ERP 财务模块数据完整，已有数据仓库 — ERP financial module data complete, data warehouse exists |
| D3 决策频率 Decision Frequency | **2** | 月度编制，频率较低 — Monthly preparation, relatively low frequency |
| D4 实施复杂度 Implementation Complexity | **4** | 可基于现有 ERP + 数据仓库搭建自动化报表工具，不改变核心财务流程 — Can build automated reporting tool on existing ERP + data warehouse, no core process change |
| Cs 场景数据系数 | **1.0** | 财务数据完整、结构化，质量有保障 — Financial data complete, structured, quality assured |

**计算 Calculation:**

```
加权和 Weighted Sum = 0.25 x 5 + 0.30 x 4 + 0.20 x 2 + 0.25 x 4
                    = 1.25 + 1.20 + 0.40 + 1.00
                    = 3.85

基础分 Base Score = (3.85 - 1) / 4 x 100 = 71.25

最终得分 Final Score = 71.25 x 1.0 = 71.25

推荐级别 Tier: Tier 2 — 短期规划 Short-term Plan
```

**建议**: 虽然决策频率低拉低了总分，但规则、数据、实施条件均极好。适合 RPA + AI 自动生成报表，投入小、见效快，可作为快赢项目。

**Recommendation**: Although low decision frequency drags down the total, rules, data, and implementation conditions are all excellent. Suitable for RPA + AI automated report generation — low investment, quick wins, ideal as a quick-win project.

#### 实例 2 敏感性分析 | Sensitivity Analysis for Example 2

| 维度 Dimension | 当前分 Current | -1 后得分 Score at -1 | +1 后得分 Score at +1 | 变化幅度 Delta | 跨级? Tier Change? |
|---|---|---|---|---|---|
| D1 规则显性度 (4->5 capped) | 5 | **65.00** | N/A (capped) | -6.25 | **Yes: 71.25 -> 65.00, Tier 2 stays** |
| D2 数据模态 | 4 | **63.75** | **78.75** | +/-7.50 | **+1: Yes, 71.25 -> 78.75, Tier 2 -> Tier 1!** |
| D3 决策频率 | 2 | **66.25** | **76.25** | +/-5.00 | **+1: Yes, 71.25 -> 76.25, Tier 2 -> Tier 1!** |
| D4 实施复杂度 (4->5 cap) | 4 | **65.00** | **77.50** | +/-6.25 | **+1: Yes, 71.25 -> 77.50, Tier 2 -> Tier 1!** |

**盈亏平衡分析 Break-even analysis**: 当前得分 71.25，距离 Tier 1 边界 (75) 仅差 3.75 分。在 Cs = 1.0 的条件下:
- D2 需提升 +0.50 分（不到 1 个评分等级）即可跨入 Tier 1
- D3 需提升 +0.75 分（不到 1 个评分等级）即可跨入 Tier 1
- D4 需提升 +0.60 分（不到 1 个评分等级）即可跨入 Tier 1

**结论**: 该场景得分高度敏感于 Tier 1 边界。D2、D3、D4 任一维度的评分若在边界情况下偏高半分，结论即可能翻转。顾问应重点核实这三个维度的评分准确性。

**Conclusion**: This scenario's score is highly sensitive to the Tier 1 boundary. If D2, D3, or D4 scores shift by less than 1 point, the recommendation could flip. The consultant should carefully verify the accuracy of these three dimension scores.

---

### 实例 3: 客户服务智能应答 | Customer Service Intelligent Response

**场景**: 客服热线 + 在线客服，每日处理 500+ 咨询，涉及产品咨询、投诉、售后。
**Scenario**: Customer service hotline + online support, handling 500+ inquiries daily, covering product inquiries, complaints, and after-sales.

| 维度 Dimension | 评分 Score | 理由 Rationale |
|---|---|---|
| D1 规则显性度 Rule Explicitness | **3** | 有 FAQ 知识库但不完整，复杂问题依赖经验 — FAQ knowledge base exists but incomplete, complex issues depend on experience |
| D2 数据模态 Data Modality | **4** | CRM 系统记录完整对话历史，有结构化工单数据 — CRM records complete conversation history, structured ticket data available |
| D3 决策频率 Decision Frequency | **4** | 每小时数十次响应决策 — Dozens of response decisions per hour |
| D4 实施复杂度 Implementation Complexity | **3** | 需对接 CRM + 订单 + 产品系统，涉及客服流程调整 — Requires CRM + order + product system integration, involves service process adjustment |
| Cs 场景数据系数 | **0.8** | CRM 对话数据完整，但与订单/产品系统的集成数据存在缺口 — CRM conversation data complete, but integrated data with order/product systems has gaps |

**计算 Calculation:**

```
加权和 Weighted Sum = 0.25 x 3 + 0.30 x 4 + 0.20 x 4 + 0.25 x 3
                    = 0.75 + 1.20 + 0.80 + 0.75
                    = 3.50

基础分 Base Score = (3.50 - 1) / 4 x 100 = 62.50

最终得分 Final Score = 62.50 x 0.8 = 50.00

推荐级别 Tier: Tier 2 — 短期规划 Short-term Plan (恰好在边界上 exactly at boundary)
```

**建议**: 数据和频率条件较好，主要瓶颈在规则显性度和实施复杂度。建议先完善知识库（提升 D1）、打通 CRM 与订单系统（提升 Cs 至 1.0），再引入智能客服。注意该场景得分恰好在 Tier 2/Tier 3 边界（50 分），任何一个维度评分稍有偏差都可能改变推荐级别，顾问应格外审慎。

**Recommendation**: Data and frequency conditions are good; the main bottlenecks are rule explicitness and implementation complexity. Recommend first improving the knowledge base (raise D1) and integrating CRM with order systems (raise Cs to 1.0), then introduce intelligent customer service. Note this scenario scores exactly at the Tier 2/Tier 3 boundary (50 points) — any small deviation in dimension scoring could change the recommendation tier. The consultant should exercise extra caution.

---

## 十、注意事项 | Important Notes

1. **评分应基于当前状态** — 评估"现在是什么样"，而非"将来想变成什么样"。
   Score based on current state, not aspirational future state.

2. **同一企业不同场景可能差异巨大** — 不要一刀切，逐场景独立评分，尤其是场景数据系数 Cs 必须逐场景独立评定。
   Different scenarios within the same enterprise may vary greatly — score each independently. In particular, the per-scenario data coefficient Cs must be assessed independently per scenario.

3. **低分不代表不能做 AI** — 而是需要先补基础，再做 AI。Tier 3 (夯实基础) 正是为此设计。
   Low score does not mean AI is impossible — it means foundations need strengthening first. Tier 3 (Foundation First) is designed exactly for this.

4. **评分是起点而非终点** — 用于优先级排序和投资决策参考，不是唯一依据。务必结合敏感性分析解读得分的稳健性。
   Scoring is a starting point, not the final word — use for prioritization and investment decision reference, not as the sole basis. Always interpret scores alongside sensitivity analysis for robustness.

5. **权重调整需文档化** — 如果调整了默认权重，必须记录调整理由，并确保同一批评估的所有场景使用相同权重集。
   Weight adjustments must be documented — if default weights are changed, record the rationale and ensure all scenarios in the same assessment batch use the same weight set.

6. **敏感性分析不可省略** — 对于得分接近级别边界的场景（距边界 < 10 分），必须执行敏感性分析并在报告中呈现。
   Sensitivity analysis must not be skipped — for scenarios scoring close to a tier boundary (within 10 points), sensitivity analysis must be performed and presented in the report.

---

*深略 StratAlign — AI 原生潜力评分标准 v1.1.0 | AI-Native Potential Scoring Criteria v1.1.0*
*支持中英双语输出 | Bilingual (Chinese/English) output supported*
