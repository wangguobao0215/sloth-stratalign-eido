# 深略 · StratAlign — 战略对齐诊断报告
# Strategic Alignment Diagnostic Report

<!-- LANGUAGE HANDLING INSTRUCTIONS:
This template contains bilingual headers and consultant notes.
The engine MUST generate the report in the user's selected language:

- CHINESE MODE:
  - All section titles: use Chinese titles only (e.g., "高管摘要" not "高管摘要 | Executive Summary")
  - All table headers: Chinese only (e.g., "指标" not "指标 Metric")
  - All narrative text: written in Chinese
  - Consultant notes: interpret and apply in Chinese output
  - Keep English abbreviations where standard (e.g., BSC, ROI, NPV, KPI, CSAT, NPS)

- ENGLISH MODE:
  - All section titles: use English titles only (e.g., "Executive Summary" not "高管摘要 | Executive Summary")
  - All table headers: English only (e.g., "Metric" not "指标 Metric")
  - All narrative text: written in English
  - Consultant notes: interpret and apply in English output
  - Use standard English business/consulting terminology

- DELIVERABLE OVERRIDE: If user requests a specific language for the report
  (via "用英文生成" or "generate in Chinese"), use that language for the entire report
  regardless of session language.

The template variables ({{variable_name}}) remain the same regardless of language.
The engine fills them with content in the appropriate language.
-->

---

## 报告信息 | Report Information

- **企业名称 Client**: {{company_name}}
- **行业 Industry**: {{industry}}
- **报告日期 Date**: {{report_date}}
- **报告版本 Version**: v1.0.0
- **分析师 Analyst**: 深略 · StratAlign Engine
- **保密等级 Confidentiality**: 机密 — 仅限项目相关方 | Confidential — Project Stakeholders Only

---

<!-- ============================================================
     SECTION 0: EXECUTIVE SUMMARY
     ============================================================ -->

## 零、高管摘要 | Executive Summary

<!-- CONSULTANT NOTE:
This is the MOST IMPORTANT section. Write it LAST after all analysis is complete,
but place it FIRST. One page maximum. A busy executive who reads ONLY this page
should understand the situation, the core finding, the recommended action, and
the expected return. Use crisp, assertive language — no hedging.
Structure: Situation → Finding → Recommendation → Impact.
-->

### 情境 | Situation

{{company_name}} 正处于 {{situation_context}} 的关键时期。{{situation_narrative}}

<!-- CONSULTANT NOTE: 2-3 sentences. Set the stage: what is happening in the client's
market, what strategic inflection they face, and why this diagnostic was initiated. -->

### 核心发现 | Key Findings

{{key_findings_narrative}}

<!-- CONSULTANT NOTE: Write a 2-3 sentence synthesis paragraph FIRST, then the bullets.
The paragraph should tell the story; the bullets provide scannable proof points. -->

1. **{{finding_1_title}}** — {{finding_1_summary}}
2. **{{finding_2_title}}** — {{finding_2_summary}}
3. **{{finding_3_title}}** — {{finding_3_summary}}
4. **{{finding_4_title}}** — {{finding_4_summary}}
5. **{{finding_5_title}}** — {{finding_5_summary}}

### 首要建议 | Top Recommendation

> {{top_recommendation}}

<!-- CONSULTANT NOTE: One bold, specific, actionable recommendation. Not "improve digital
capabilities" but "Deploy an AI-powered demand forecasting engine in the supply chain
division within 6 months, targeting a 15% inventory cost reduction." -->

### 投资与回报概览 | Investment & Return Overview

| 指标 Metric | 数值 Value |
|---|---|
| 预估总投资 Estimated Total Investment | {{total_investment}} |
| 预期 ROI 区间 Expected ROI Range | {{roi_range_low}}% — {{roi_range_high}}% |
| 综合回收期 Blended Payback Period | {{payback_period}} |
| 首批价值交付 First Value Delivery | {{first_value_date}} |

### 关键风险警示 | Critical Risk

> ⚠️ {{critical_risk_statement}}

<!-- CONSULTANT NOTE: The single most important risk that could derail the entire program.
State it plainly. Example: "If the legacy ERP data migration is not completed by Q2,
all downstream AI initiatives will slip by 6+ months, eroding projected ROI by 40%." -->

---

<!-- ============================================================
     SECTION 1: STRATEGIC DECODING
     ============================================================ -->

## 一、战略解码 | Module 1: Strategic Decoding

<!-- CONSULTANT NOTE:
This section translates the client's stated strategy into a testable, structured
framework. Begin with a brief narrative paragraph that sets up WHY this decoding
matters — connect it to the findings in the Executive Summary. Every table should
be FOLLOWED by a "So What" insight paragraph that interprets the data for the reader.
Do not let data speak for itself — consultants speak for the data.
-->

{{strategic_decoding_intro_narrative}}

<!-- CONSULTANT NOTE: 3-4 sentences. Explain the approach: we decomposed the client's
strategy into BSC perspectives, identified causal hypotheses, and tested them for
internal consistency. State the headline finding for this section upfront. -->

### 1.1 愿景与使命 | Vision & Mission

| 项目 Item | 内容 Content |
|---|---|
| 愿景 Vision | {{vision}} |
| 使命 Mission | {{mission}} |
| 核心价值观 Core Values | {{core_values}} |

> **So What 洞察**: {{vision_mission_so_what}}

<!-- CONSULTANT NOTE: Does the vision provide clear directional guidance for technology
investment? Is the mission specific enough to derive measurable objectives? Flag any
ambiguity that will create alignment problems downstream. -->

### 1.2 战略主题 | Strategic Themes

| 编号 # | 战略主题 Theme | 优先级 Priority | 时间跨度 Horizon | 战略意图 Strategic Intent |
|---|---|---|---|---|
| ST-1 | {{theme_1}} | {{priority_1}} | {{horizon_1}} | {{intent_1}} |
| ST-2 | {{theme_2}} | {{priority_2}} | {{horizon_2}} | {{intent_2}} |
| ST-3 | {{theme_3}} | {{priority_3}} | {{horizon_3}} | {{intent_3}} |

> **So What 洞察**: {{themes_so_what}}

<!-- CONSULTANT NOTE: Are the themes MECE? Do they cover both growth and efficiency?
Is there a clear time-horizon balance (short/medium/long)? If all themes cluster in
one horizon, flag the strategic imbalance. -->

### 1.3 BSC 四维目标 | BSC Four-Perspective Objectives

#### 财务维度 | Financial Perspective

| 目标 Objective | KPI | 目标值 Target | 当前值 Current | 差距 Gap | 趋势 Trend |
|---|---|---|---|---|---|
| {{fin_obj_1}} | {{fin_kpi_1}} | {{fin_target_1}} | {{fin_current_1}} | {{fin_gap_1}} | {{fin_trend_1}} |
| {{fin_obj_2}} | {{fin_kpi_2}} | {{fin_target_2}} | {{fin_current_2}} | {{fin_gap_2}} | {{fin_trend_2}} |

> **So What 洞察**: {{financial_so_what}}

<!-- CONSULTANT NOTE: Are the financial targets achievable given current trajectory?
What is the gap closure rate? If targets require a step-change, say so — this sets up
the case for AI/digital investment. -->

#### 客户维度 | Customer Perspective

| 目标 Objective | KPI | 目标值 Target | 当前值 Current | 差距 Gap | 趋势 Trend |
|---|---|---|---|---|---|
| {{cust_obj_1}} | {{cust_kpi_1}} | {{cust_target_1}} | {{cust_current_1}} | {{cust_gap_1}} | {{cust_trend_1}} |
| {{cust_obj_2}} | {{cust_kpi_2}} | {{cust_target_2}} | {{cust_current_2}} | {{cust_gap_2}} | {{cust_trend_2}} |

> **So What 洞察**: {{customer_so_what}}

#### 内部流程维度 | Internal Process Perspective

| 目标 Objective | KPI | 目标值 Target | 当前值 Current | 差距 Gap | 趋势 Trend |
|---|---|---|---|---|---|
| {{proc_obj_1}} | {{proc_kpi_1}} | {{proc_target_1}} | {{proc_current_1}} | {{proc_gap_1}} | {{proc_trend_1}} |
| {{proc_obj_2}} | {{proc_kpi_2}} | {{proc_target_2}} | {{proc_current_2}} | {{proc_gap_2}} | {{proc_trend_2}} |

> **So What 洞察**: {{process_so_what}}

#### 学习与成长维度 | Learning & Growth Perspective

| 目标 Objective | KPI | 目标值 Target | 当前值 Current | 差距 Gap | 趋势 Trend |
|---|---|---|---|---|---|
| {{learn_obj_1}} | {{learn_kpi_1}} | {{learn_target_1}} | {{learn_current_1}} | {{learn_gap_1}} | {{learn_trend_1}} |
| {{learn_obj_2}} | {{learn_kpi_2}} | {{learn_target_2}} | {{learn_current_2}} | {{learn_gap_2}} | {{learn_trend_2}} |

> **So What 洞察**: {{learning_so_what}}

### 1.4 战略假设登记簿 | Strategy Hypothesis Register

<!-- CONSULTANT NOTE: Every strategy is built on assumptions. Make them explicit.
Select the top 5 most consequential hypotheses. Use If-Then-Because format to make
them testable. This becomes the intellectual backbone of the engagement. -->

{{hypothesis_register_narrative}}

| 编号 # | 假设 Hypothesis (If-Then-Because) | 置信度 Confidence | 验证方式 Validation Method | 状态 Status |
|---|---|---|---|---|
| H-1 | **If** {{h1_if}} **then** {{h1_then}} **because** {{h1_because}} | {{h1_confidence}} | {{h1_validation}} | {{h1_status}} |
| H-2 | **If** {{h2_if}} **then** {{h2_then}} **because** {{h2_because}} | {{h2_confidence}} | {{h2_validation}} | {{h2_status}} |
| H-3 | **If** {{h3_if}} **then** {{h3_then}} **because** {{h3_because}} | {{h3_confidence}} | {{h3_validation}} | {{h3_status}} |
| H-4 | **If** {{h4_if}} **then** {{h4_then}} **because** {{h4_because}} | {{h4_confidence}} | {{h4_validation}} | {{h4_status}} |
| H-5 | **If** {{h5_if}} **then** {{h5_then}} **because** {{h5_because}} | {{h5_confidence}} | {{h5_validation}} | {{h5_status}} |

> **So What 洞察**: {{hypothesis_so_what}}

### 1.5 战略地图 | Strategy Map

<!-- CONSULTANT NOTE: Render a strategy map showing causal linkages across BSC
perspectives. Use ASCII art for maximum compatibility. Each arrow represents a
hypothesized cause-effect relationship. Call out the 1-2 most critical causal chains
in the narrative below the map. -->

```
┌─────────────────────────────────────────────────────────────────┐
│                     财务 FINANCIAL                               │
│  {{fin_map_obj_1}}          {{fin_map_obj_2}}                   │
│        ▲                          ▲                             │
│        │                          │                             │
├────────┼──────────────────────────┼─────────────────────────────┤
│        │          客户 CUSTOMER   │                             │
│  {{cust_map_obj_1}}         {{cust_map_obj_2}}                  │
│        ▲                          ▲                             │
│        │                          │                             │
├────────┼──────────────────────────┼─────────────────────────────┤
│        │       内部流程 PROCESS   │                             │
│  {{proc_map_obj_1}}    →    {{proc_map_obj_2}}                  │
│        ▲                          ▲                             │
│        │                          │                             │
├────────┼──────────────────────────┼─────────────────────────────┤
│        │    学习与成长 LEARNING   │                             │
│  {{learn_map_obj_1}}        {{learn_map_obj_2}}                 │
└─────────────────────────────────────────────────────────────────┘
```

{{strategy_map_narrative}}

<!-- CONSULTANT NOTE: Explain the critical causal chains. Example: "The most important
causal chain runs from [data talent acquisition] → [AI-powered process automation] →
[customer response time reduction] → [market share growth]. If ANY link in this chain
breaks, the financial target is at risk." -->

### 1.6 矛盾检测结果 | Contradiction Detection Results

{{contradiction_intro_narrative}}

<!-- CONSULTANT NOTE: Begin with context — how many contradictions were found and what
this means for strategic coherence. A high count suggests the strategy was assembled
piecemeal; a zero count may mean the analysis lacked depth. Be honest about both. -->

**检测到的矛盾 Contradictions Detected**: {{contradiction_count}}

| 编号 # | 矛盾类型 Type | 涉及目标 Objectives | 严重程度 Severity | 说明 Description | 建议化解方案 Recommended Resolution |
|---|---|---|---|---|---|
| C-1 | {{c1_type}} | {{c1_obj_a}} ↔ {{c1_obj_b}} | {{c1_severity}} | {{c1_description}} | {{c1_resolution}} |
| C-2 | {{c2_type}} | {{c2_obj_a}} ↔ {{c2_obj_b}} | {{c2_severity}} | {{c2_description}} | {{c2_resolution}} |
| C-3 | {{c3_type}} | {{c3_obj_a}} ↔ {{c3_obj_b}} | {{c3_severity}} | {{c3_description}} | {{c3_resolution}} |

**因果链完整性 Causal Chain Completeness**: {{completeness_pct}}%

**缺失维度 Missing Perspectives**: {{missing_perspectives}}

> **So What 洞察**: {{contradiction_so_what}}

<!-- CONSULTANT NOTE: Connect contradictions to real business consequences. Example:
"The contradiction between aggressive cost cutting (F-2) and customer experience
investment (C-1) will force middle management to make ad-hoc tradeoffs unless the
executive team provides explicit prioritization guidance." -->

---

<!-- ============================================================
     SECTION 2: BOTTLENECK SCAN
     ============================================================ -->

## 二、瓶颈扫描 | Module 2: Bottleneck Scan

<!-- CONSULTANT NOTE:
This section moves from strategy to reality. The narrative should bridge the strategic
objectives above to the operational pain on the ground. Start with a synthesis paragraph
that names the systemic pattern — are bottlenecks clustered in one function, one process,
or one capability layer? Then provide the detail.
-->

{{bottleneck_intro_narrative}}

<!-- CONSULTANT NOTE: 3-4 sentences. Lead with the pattern, not the list. Example:
"Our analysis identified 12 pain points across 5 departments. However, the dominant
pattern is clear: 8 of 12 pain points trace back to a single root cause — fragmented
data across disconnected legacy systems." -->

### 2.1 业务流程痛点 | Business Process Pain Points

| 编号 # | 部门 Dept | 痛点 Pain Point | 影响程度 Impact | 频率 Freq | 根因/表象 Root Cause vs Symptom | 关联战略目标 Linked Objectives |
|---|---|---|---|---|---|---|
| BP-1 | {{bp1_dept}} | {{bp1_pain}} | {{bp1_impact}} | {{bp1_freq}} | {{bp1_root_or_symptom}} | {{bp1_linked_obj}} |
| BP-2 | {{bp2_dept}} | {{bp2_pain}} | {{bp2_impact}} | {{bp2_freq}} | {{bp2_root_or_symptom}} | {{bp2_linked_obj}} |
| BP-3 | {{bp3_dept}} | {{bp3_pain}} | {{bp3_impact}} | {{bp3_freq}} | {{bp3_root_or_symptom}} | {{bp3_linked_obj}} |
| BP-4 | {{bp4_dept}} | {{bp4_pain}} | {{bp4_impact}} | {{bp4_freq}} | {{bp4_root_or_symptom}} | {{bp4_linked_obj}} |
| BP-5 | {{bp5_dept}} | {{bp5_pain}} | {{bp5_impact}} | {{bp5_freq}} | {{bp5_root_or_symptom}} | {{bp5_linked_obj}} |

> **So What 洞察**: {{pain_points_so_what}}

<!-- CONSULTANT NOTE: Distinguish root causes from symptoms. If 3 departments report
"slow reporting," that is a symptom — the root cause may be manual data consolidation.
Explicitly call out which pain points are symptoms of deeper issues. This earns
credibility with the client's operational leaders. -->

### 2.2 跨职能影响分析 | Cross-Functional Impact Analysis

<!-- CONSULTANT NOTE: Pain points rarely stay within departmental boundaries. Map how
a bottleneck in one function cascades to others. This demonstrates systems thinking
and justifies enterprise-level (not point-solution) investment. -->

{{cross_functional_narrative}}

| 源痛点 Source Pain Point | 直接影响部门 Directly Affected | 间接影响部门 Indirectly Affected | 估计年化成本 Est. Annual Cost |
|---|---|---|---|
| {{cf1_source}} | {{cf1_direct}} | {{cf1_indirect}} | {{cf1_cost}} |
| {{cf2_source}} | {{cf2_direct}} | {{cf2_indirect}} | {{cf2_cost}} |
| {{cf3_source}} | {{cf3_direct}} | {{cf3_indirect}} | {{cf3_cost}} |

> **So What 洞察**: {{cross_functional_so_what}}

### 2.3 能力差距分析 | Capability Gap Analysis

| 能力 Capability | 当前水平 Current (1-5) | 目标水平 Target (1-5) | 差距 Gap | 差距影响 Gap Impact |
|---|---|---|---|---|
| {{cap1_name}} | {{cap1_current}} | {{cap1_target}} | {{cap1_gap}} | {{cap1_impact}} |
| {{cap2_name}} | {{cap2_current}} | {{cap2_target}} | {{cap2_gap}} | {{cap2_impact}} |
| {{cap3_name}} | {{cap3_current}} | {{cap3_target}} | {{cap3_gap}} | {{cap3_impact}} |
| {{cap4_name}} | {{cap4_current}} | {{cap4_target}} | {{cap4_gap}} | {{cap4_impact}} |

> **So What 洞察**: {{capability_gap_so_what}}

### 2.4 技术与组织债务 | Technical & Organizational Debt

| 类型 Type | 描述 Description | 紧迫度 Urgency | 估计修复成本 Est. Fix Cost | 不修复的代价 Cost of Inaction |
|---|---|---|---|---|
| 技术债务 Tech Debt | {{tech_debt_1}} | {{td1_urgency}} | {{td1_cost}} | {{td1_inaction}} |
| 技术债务 Tech Debt | {{tech_debt_2}} | {{td2_urgency}} | {{td2_cost}} | {{td2_inaction}} |
| 组织债务 Org Debt | {{org_debt_1}} | {{od1_urgency}} | {{od1_cost}} | {{od1_inaction}} |
| 组织债务 Org Debt | {{org_debt_2}} | {{od2_urgency}} | {{od2_cost}} | {{od2_inaction}} |

> **So What 洞察**: {{debt_so_what}}

---

<!-- ============================================================
     SECTION 3: AI-NATIVE POTENTIAL TRIAGE
     ============================================================ -->

## 三、AI 原生潜力分诊 | Module 3: AI-Native Potential Triage

<!-- CONSULTANT NOTE:
This section is the analytical centerpiece. The narrative must explain WHY certain
scenarios score high — not just show the numbers. Use the weighted scoring model
(not simple multiplication). Each dimension is scored 1-5 with explicit weights.
Include Implementation Complexity as a 4th dimension.
After the scoring matrix, provide sensitivity analysis for the top 3 scenarios
and narrative recommendations for each.
-->

{{ai_triage_intro_narrative}}

<!-- CONSULTANT NOTE: 3-4 sentences. Explain the methodology shift: "We evaluated
{{scenario_count}} AI application scenarios across four weighted dimensions. Unlike
simple multiplication models, our weighted approach prevents a single low-scoring
dimension from zeroing out an otherwise strong opportunity." -->

### 3.1 加权评分模型 | Weighted Scoring Model

**评分公式 Scoring Formula**:

```
最终得分 = [ (规则显性度 × W_rule) + (数据模态 × W_data) + (决策频率 × W_freq)
            + (实施复杂度逆分 × W_impl) ] × 数据基础设施系数

Final Score = [ (Rule Explicitness × W_rule) + (Data Modality × W_data)
              + (Decision Frequency × W_freq) + (Impl. Simplicity × W_impl) ]
              × Data Infrastructure Coefficient

权重 Weights: W_rule = {{w_rule}}, W_data = {{w_data}}, W_freq = {{w_freq}}, W_impl = {{w_impl}}
(权重总和 Sum = 1.0)
```

### 3.2 评分矩阵总览 | Scoring Matrix Overview

| 场景 Scenario | 规则显性度 Rule (1-5) | 数据模态 Data (1-5) | 决策频率 Freq (1-5) | 实施简易度 Impl (1-5) | 加权原始分 Weighted Raw | 数据系数 Coeff | 最终得分 Final |
|---|---|---|---|---|---|---|---|
| {{s1_name}} | {{s1_rule}} | {{s1_data}} | {{s1_freq}} | {{s1_impl}} | {{s1_weighted}} | {{s1_coeff}} | **{{s1_final}}** |
| {{s2_name}} | {{s2_rule}} | {{s2_data}} | {{s2_freq}} | {{s2_impl}} | {{s2_weighted}} | {{s2_coeff}} | **{{s2_final}}** |
| {{s3_name}} | {{s3_rule}} | {{s3_data}} | {{s3_freq}} | {{s3_impl}} | {{s3_weighted}} | {{s3_coeff}} | **{{s3_final}}** |
| {{s4_name}} | {{s4_rule}} | {{s4_data}} | {{s4_freq}} | {{s4_impl}} | {{s4_weighted}} | {{s4_coeff}} | **{{s4_final}}** |
| {{s5_name}} | {{s5_rule}} | {{s5_data}} | {{s5_freq}} | {{s5_impl}} | {{s5_weighted}} | {{s5_coeff}} | **{{s5_final}}** |

### 3.3 AI 场景排序与建议 | AI Scenario Ranking & Recommendations

<!-- CONSULTANT NOTE: Do NOT just list rankings. For each of the top 3, write a
2-3 sentence narrative recommendation explaining WHY it ranked where it did, what
the client should do about it, and what conditions need to be true for success. -->

#### 🥇 第1名 | Rank 1: {{rank1_scenario}}

**得分 Score**: {{rank1_score}} | **推荐 Recommendation**: 立即启动 Immediate Start

{{rank1_narrative}}

<!-- CONSULTANT NOTE: Why is this #1? What makes it uniquely ready? What is the
expected business impact? What is the minimum viable deployment? -->

#### 🥈 第2名 | Rank 2: {{rank2_scenario}}

**得分 Score**: {{rank2_score}} | **推荐 Recommendation**: 短期规划 Short-term Plan

{{rank2_narrative}}

#### 🥉 第3名 | Rank 3: {{rank3_scenario}}

**得分 Score**: {{rank3_score}} | **推荐 Recommendation**: 中期储备 Mid-term Reserve

{{rank3_narrative}}

### 3.4 敏感性分析 | Sensitivity Analysis (Top 3 Scenarios)

<!-- CONSULTANT NOTE: Show how the scores change when individual dimension scores
shift by +/-1. This reveals which scenarios are robust and which are fragile —
a key input for risk-adjusted prioritization. -->

{{sensitivity_narrative}}

| 场景 Scenario | 基准得分 Base Score | 规则 ±1 影响 Rule ±1 | 数据 ±1 影响 Data ±1 | 频率 ±1 影响 Freq ±1 | 实施 ±1 影响 Impl ±1 | 最敏感维度 Most Sensitive |
|---|---|---|---|---|---|---|
| {{sens1_name}} | {{sens1_base}} | {{sens1_rule_delta}} | {{sens1_data_delta}} | {{sens1_freq_delta}} | {{sens1_impl_delta}} | {{sens1_sensitive}} |
| {{sens2_name}} | {{sens2_base}} | {{sens2_rule_delta}} | {{sens2_data_delta}} | {{sens2_freq_delta}} | {{sens2_impl_delta}} | {{sens2_sensitive}} |
| {{sens3_name}} | {{sens3_base}} | {{sens3_rule_delta}} | {{sens3_data_delta}} | {{sens3_freq_delta}} | {{sens3_impl_delta}} | {{sens3_sensitive}} |

> **So What 洞察**: {{sensitivity_so_what}}

### 3.5 假设情景分析 | "What-If" Scenarios

<!-- CONSULTANT NOTE: Show the client how their AI readiness scores would change
under different investment assumptions. This directly supports the investment case
in Section 5 — "if you build the data infrastructure, THESE opportunities unlock." -->

{{what_if_narrative}}

| 假设条件 What-If Condition | 受影响场景 Affected Scenarios | 当前得分 Current Scores | 调整后得分 Adjusted Scores | 净变化 Net Change |
|---|---|---|---|---|
| {{wif1_condition}} | {{wif1_scenarios}} | {{wif1_current}} | {{wif1_adjusted}} | {{wif1_delta}} |
| {{wif2_condition}} | {{wif2_scenarios}} | {{wif2_current}} | {{wif2_adjusted}} | {{wif2_delta}} |
| {{wif3_condition}} | {{wif3_scenarios}} | {{wif3_current}} | {{wif3_adjusted}} | {{wif3_delta}} |

> **So What 洞察**: {{what_if_so_what}}

### 3.6 数据基础设施评估 | Data Infrastructure Assessment

| 数据域 Data Domain | 当前状态 Current State | 系数 Coefficient | 改进建议 Improvement | 改进后系数 Post-Fix Coeff |
|---|---|---|---|---|
| {{di1_domain}} | {{di1_state}} | {{di1_coeff}} | {{di1_suggestion}} | {{di1_post_coeff}} |
| {{di2_domain}} | {{di2_state}} | {{di2_coeff}} | {{di2_suggestion}} | {{di2_post_coeff}} |
| {{di3_domain}} | {{di3_state}} | {{di3_coeff}} | {{di3_suggestion}} | {{di3_post_coeff}} |

> **So What 洞察**: {{data_infra_so_what}}

---

<!-- ============================================================
     SECTION 4: COVERAGE ANALYSIS
     ============================================================ -->

## 四、覆盖分析 | Module 4: Coverage Analysis

<!-- CONSULTANT NOTE:
This section maps the current IT landscape against required business capabilities.
The narrative should tell a story about architectural health — not just list systems.
Lead with the overall coverage verdict, then drill into the details.
-->

{{coverage_intro_narrative}}

<!-- CONSULTANT NOTE: 3-4 sentences. Example: "The current application portfolio
covers 62% of required business capabilities, but coverage quality varies dramatically.
Core transactional processes are well-served by the existing ERP, while customer-facing
and analytics capabilities show critical gaps that directly constrain the strategic
themes identified in Section 1." -->

### 4.1 现有 IT 系统清单 | Current IT System Inventory

| 系统 System | 类型 Type | 覆盖业务 Coverage | 状态 Status | 上线年份 Year | 技术健康度 Tech Health (1-5) |
|---|---|---|---|---|---|
| {{sys1_name}} | {{sys1_type}} | {{sys1_coverage}} | {{sys1_status}} | {{sys1_year}} | {{sys1_health}} |
| {{sys2_name}} | {{sys2_type}} | {{sys2_coverage}} | {{sys2_status}} | {{sys2_year}} | {{sys2_health}} |
| {{sys3_name}} | {{sys3_type}} | {{sys3_coverage}} | {{sys3_status}} | {{sys3_year}} | {{sys3_health}} |
| {{sys4_name}} | {{sys4_type}} | {{sys4_coverage}} | {{sys4_status}} | {{sys4_year}} | {{sys4_health}} |
| {{sys5_name}} | {{sys5_type}} | {{sys5_coverage}} | {{sys5_status}} | {{sys5_year}} | {{sys5_health}} |

### 4.2 业务能力 → IT 能力映射 | Business → IT Capability Mapping

| 业务能力 Biz Capability (L1) | 子能力 Sub-Capability (L2) | IT 系统 IT System | 覆盖度 Coverage | 空白说明 Gap Description |
|---|---|---|---|---|
| {{map1_l1}} | {{map1_l2}} | {{map1_system}} | {{map1_coverage}} | {{map1_gap}} |
| {{map2_l1}} | {{map2_l2}} | {{map2_system}} | {{map2_coverage}} | {{map2_gap}} |
| {{map3_l1}} | {{map3_l2}} | {{map3_system}} | {{map3_coverage}} | {{map3_gap}} |
| {{map4_l1}} | {{map4_l2}} | {{map4_system}} | {{map4_coverage}} | {{map4_gap}} |
| {{map5_l1}} | {{map5_l2}} | {{map5_system}} | {{map5_coverage}} | {{map5_gap}} |

### 4.3 L1-L2 能力热力图参考 | L1-L2 Capability Heat Map

<!-- CONSULTANT NOTE: Summarize the heat map findings. Use text-based indicators since
visual heat maps cannot be rendered in markdown. The narrative should highlight the
"hot zones" (over-served) and "cold zones" (under-served). -->

{{capability_heatmap_narrative}}

| L1 能力域 Capability Domain | 覆盖强度 Coverage Intensity | 关键缺口 Key Gaps | 冗余风险 Redundancy Risk |
|---|---|---|---|
| {{hm1_domain}} | {{hm1_intensity}} | {{hm1_gaps}} | {{hm1_redundancy}} |
| {{hm2_domain}} | {{hm2_intensity}} | {{hm2_gaps}} | {{hm2_redundancy}} |
| {{hm3_domain}} | {{hm3_intensity}} | {{hm3_gaps}} | {{hm3_redundancy}} |

### 4.4 应用组合健康度象限 | Application Portfolio Health Quadrant

<!-- CONSULTANT NOTE: Classify each application into one of four quadrants based on
business value (vertical axis) and technical health (horizontal axis). This drives
the invest/tolerate/migrate/eliminate conversation with IT leadership. -->

{{portfolio_health_narrative}}

```
                        高业务价值 High Business Value
                                    │
              投资 INVEST            │           维护 MAINTAIN
        (高价值 + 低技术健康度)       │      (高价值 + 高技术健康度)
        {{invest_systems}}           │      {{maintain_systems}}
                                    │
   ─────────────────────────────────┼──────────────────────────────
                                    │
              淘汰 ELIMINATE         │           容忍 TOLERATE
        (低价值 + 低技术健康度)       │      (低价值 + 高技术健康度)
        {{eliminate_systems}}        │      {{tolerate_systems}}
                                    │
                        低业务价值 Low Business Value
```

> **So What 洞察**: {{portfolio_health_so_what}}

### 4.5 架构债务 | Architecture Debt

<!-- CONSULTANT NOTE: This is distinct from technical debt in Section 2. Architecture
debt refers to systemic structural problems: point-to-point integrations, missing
middleware, data silos, absence of API layers, etc. These are the structural barriers
that will slow or prevent AI adoption. -->

{{architecture_debt_narrative}}

### 4.6 覆盖率汇总与改进优先级 | Coverage Summary & Improvement Priority

- **整体覆盖率 Overall Coverage**: {{overall_pct}}%
- **关键空白 Critical Gaps**: {{critical_gaps}}
- **冗余系统 Redundant Systems**: {{redundant_count}}

**覆盖改进优先级 Coverage Improvement Priority**:

| 优先级 Priority | 能力缺口 Capability Gap | 改进理由 Rationale | 建议方案 Recommended Approach | 关联投资项目 Linked Investment |
|---|---|---|---|---|
| P1 | {{cp1_gap}} | {{cp1_rationale}} | {{cp1_approach}} | {{cp1_project}} |
| P2 | {{cp2_gap}} | {{cp2_rationale}} | {{cp2_approach}} | {{cp2_project}} |
| P3 | {{cp3_gap}} | {{cp3_rationale}} | {{cp3_approach}} | {{cp3_project}} |

> **So What 洞察**: {{coverage_so_what}}

---

<!-- ============================================================
     SECTION 5: INVESTMENT PORTFOLIO
     ============================================================ -->

## 五、投资组合 | Module 5: Investment Portfolio

<!-- CONSULTANT NOTE:
This is where analysis becomes action. The narrative must build an "investment thesis"
— a coherent argument for WHY this specific portfolio of projects, in this sequence,
at this investment level, is the right answer. Show the math. Every number should be
traceable to an assumption. Use the ROI calculation framework consistently across
all projects.
-->

### 5.1 投资论点 | Investment Thesis

{{investment_thesis_narrative}}

<!-- CONSULTANT NOTE: 1 full paragraph. This is the core argument. Example:
"We recommend a phased investment of {{total_investment}} across 3 project categories
over 24 months. The portfolio is designed around a central thesis: by building a unified
data foundation (Phase 0-1) and deploying targeted AI applications on top of it
(Phase 2-3), {{company_name}} can close the capability gaps identified in Section 2
while generating measurable ROI from AI scenarios prioritized in Section 3. The portfolio
is sequenced so that early quick wins fund later strategic bets, reducing peak cash
outflow and building organizational confidence." -->

### 5.2 项目分组与 ROI 详算 | Project Grouping with Full ROI Calculation

<!-- CONSULTANT NOTE: For EACH project, show the complete cost breakdown and benefit
calculation. Do NOT just show final ROI numbers — clients and their CFOs need to see
the math to trust the numbers. Use consistent categories across all projects. -->

#### Phase 0: 基础建设 Foundation (月 0-3)

##### 项目 {{f_proj1_name}}

{{f_proj1_narrative}}

**成本分解 Cost Breakdown**:

| 成本项 Cost Item | 金额 Amount | 说明 Notes |
|---|---|---|
| 许可/订阅 License / Subscription | {{f_p1_license}} | {{f_p1_license_note}} |
| 实施交付 Implementation | {{f_p1_impl}} | {{f_p1_impl_note}} |
| 集成开发 Integration | {{f_p1_integ}} | {{f_p1_integ_note}} |
| 培训/变革管理 Training / Change Mgmt | {{f_p1_training}} | {{f_p1_training_note}} |
| 年运营成本 Annual Ops | {{f_p1_ops}} | {{f_p1_ops_note}} |
| **小计 Subtotal** | **{{f_p1_total_cost}}** | |

**收益估算 Benefit Estimation**:

| 收益类型 Benefit Type | 年化金额 Annual Amount | 置信度 Confidence | 计算依据 Calculation Basis |
|---|---|---|---|
| 直接节约 Direct Savings | {{f_p1_savings}} | {{f_p1_sav_conf}} | {{f_p1_sav_basis}} |
| 收入提升 Revenue Uplift | {{f_p1_revenue}} | {{f_p1_rev_conf}} | {{f_p1_rev_basis}} |
| 风险规避 Risk Avoidance | {{f_p1_risk_avoid}} | {{f_p1_risk_conf}} | {{f_p1_risk_basis}} |
| **年化总收益 Total Annual Benefit** | **{{f_p1_total_benefit}}** | | |

**投资回报 ROI Metrics**:

| 指标 Metric | 数值 Value |
|---|---|
| NPV (3年, 折现率 {{discount_rate}}%) | {{f_p1_npv}} |
| 回收期 Payback Period | {{f_p1_payback}} |
| 3年 ROI | {{f_p1_roi_3yr}}% |

---

#### Phase 1: 快赢项目 Quick Wins (月 3-9)

<!-- CONSULTANT NOTE: Repeat the same cost/benefit/ROI structure for each project.
Quick Wins should show fast payback (< 12 months) and high confidence benefits.
These build credibility for the larger strategic investments. -->

##### 项目 {{qw_proj1_name}}

{{qw_proj1_narrative}}

**成本分解 Cost Breakdown**:

| 成本项 Cost Item | 金额 Amount | 说明 Notes |
|---|---|---|
| 许可/订阅 License / Subscription | {{qw_p1_license}} | {{qw_p1_license_note}} |
| 实施交付 Implementation | {{qw_p1_impl}} | {{qw_p1_impl_note}} |
| 集成开发 Integration | {{qw_p1_integ}} | {{qw_p1_integ_note}} |
| 培训/变革管理 Training / Change Mgmt | {{qw_p1_training}} | {{qw_p1_training_note}} |
| 年运营成本 Annual Ops | {{qw_p1_ops}} | {{qw_p1_ops_note}} |
| **小计 Subtotal** | **{{qw_p1_total_cost}}** | |

**收益估算 Benefit Estimation**:

| 收益类型 Benefit Type | 年化金额 Annual Amount | 置信度 Confidence | 计算依据 Calculation Basis |
|---|---|---|---|
| 直接节约 Direct Savings | {{qw_p1_savings}} | {{qw_p1_sav_conf}} | {{qw_p1_sav_basis}} |
| 收入提升 Revenue Uplift | {{qw_p1_revenue}} | {{qw_p1_rev_conf}} | {{qw_p1_rev_basis}} |
| 风险规避 Risk Avoidance | {{qw_p1_risk_avoid}} | {{qw_p1_risk_conf}} | {{qw_p1_risk_basis}} |
| **年化总收益 Total Annual Benefit** | **{{qw_p1_total_benefit}}** | | |

**投资回报 ROI Metrics**:

| 指标 Metric | 数值 Value |
|---|---|
| NPV (3年, 折现率 {{discount_rate}}%) | {{qw_p1_npv}} |
| 回收期 Payback Period | {{qw_p1_payback}} |
| 3年 ROI | {{qw_p1_roi_3yr}}% |

##### 项目 {{qw_proj2_name}}

{{qw_proj2_narrative}}

**成本分解 Cost Breakdown**:

| 成本项 Cost Item | 金额 Amount | 说明 Notes |
|---|---|---|
| 许可/订阅 License / Subscription | {{qw_p2_license}} | {{qw_p2_license_note}} |
| 实施交付 Implementation | {{qw_p2_impl}} | {{qw_p2_impl_note}} |
| 集成开发 Integration | {{qw_p2_integ}} | {{qw_p2_integ_note}} |
| 培训/变革管理 Training / Change Mgmt | {{qw_p2_training}} | {{qw_p2_training_note}} |
| 年运营成本 Annual Ops | {{qw_p2_ops}} | {{qw_p2_ops_note}} |
| **小计 Subtotal** | **{{qw_p2_total_cost}}** | |

**收益估算 Benefit Estimation**:

| 收益类型 Benefit Type | 年化金额 Annual Amount | 置信度 Confidence | 计算依据 Calculation Basis |
|---|---|---|---|
| 直接节约 Direct Savings | {{qw_p2_savings}} | {{qw_p2_sav_conf}} | {{qw_p2_sav_basis}} |
| 收入提升 Revenue Uplift | {{qw_p2_revenue}} | {{qw_p2_rev_conf}} | {{qw_p2_rev_basis}} |
| 风险规避 Risk Avoidance | {{qw_p2_risk_avoid}} | {{qw_p2_risk_conf}} | {{qw_p2_risk_basis}} |
| **年化总收益 Total Annual Benefit** | **{{qw_p2_total_benefit}}** | | |

**投资回报 ROI Metrics**:

| 指标 Metric | 数值 Value |
|---|---|
| NPV (3年, 折现率 {{discount_rate}}%) | {{qw_p2_npv}} |
| 回收期 Payback Period | {{qw_p2_payback}} |
| 3年 ROI | {{qw_p2_roi_3yr}}% |

---

#### Phase 2: 战略项目 Strategic (月 9-18)

##### 项目 {{st_proj1_name}}

{{st_proj1_narrative}}

**成本分解 Cost Breakdown**:

| 成本项 Cost Item | 金额 Amount | 说明 Notes |
|---|---|---|
| 许可/订阅 License / Subscription | {{st_p1_license}} | {{st_p1_license_note}} |
| 实施交付 Implementation | {{st_p1_impl}} | {{st_p1_impl_note}} |
| 集成开发 Integration | {{st_p1_integ}} | {{st_p1_integ_note}} |
| 培训/变革管理 Training / Change Mgmt | {{st_p1_training}} | {{st_p1_training_note}} |
| 年运营成本 Annual Ops | {{st_p1_ops}} | {{st_p1_ops_note}} |
| **小计 Subtotal** | **{{st_p1_total_cost}}** | |

**收益估算 Benefit Estimation**:

| 收益类型 Benefit Type | 年化金额 Annual Amount | 置信度 Confidence | 计算依据 Calculation Basis |
|---|---|---|---|
| 直接节约 Direct Savings | {{st_p1_savings}} | {{st_p1_sav_conf}} | {{st_p1_sav_basis}} |
| 收入提升 Revenue Uplift | {{st_p1_revenue}} | {{st_p1_rev_conf}} | {{st_p1_rev_basis}} |
| 风险规避 Risk Avoidance | {{st_p1_risk_avoid}} | {{st_p1_risk_conf}} | {{st_p1_risk_basis}} |
| **年化总收益 Total Annual Benefit** | **{{st_p1_total_benefit}}** | | |

**投资回报 ROI Metrics**:

| 指标 Metric | 数值 Value |
|---|---|
| NPV (3年, 折现率 {{discount_rate}}%) | {{st_p1_npv}} |
| 回收期 Payback Period | {{st_p1_payback}} |
| 3年 ROI | {{st_p1_roi_3yr}}% |

---

#### Phase 3: 规模化推广 Scale (月 18-30)

##### 项目 {{sc_proj1_name}}

{{sc_proj1_narrative}}

**成本分解 Cost Breakdown**:

| 成本项 Cost Item | 金额 Amount | 说明 Notes |
|---|---|---|
| 许可/订阅 License / Subscription | {{sc_p1_license}} | {{sc_p1_license_note}} |
| 实施交付 Implementation | {{sc_p1_impl}} | {{sc_p1_impl_note}} |
| 集成开发 Integration | {{sc_p1_integ}} | {{sc_p1_integ_note}} |
| 培训/变革管理 Training / Change Mgmt | {{sc_p1_training}} | {{sc_p1_training_note}} |
| 年运营成本 Annual Ops | {{sc_p1_ops}} | {{sc_p1_ops_note}} |
| **小计 Subtotal** | **{{sc_p1_total_cost}}** | |

**收益估算 Benefit Estimation**:

| 收益类型 Benefit Type | 年化金额 Annual Amount | 置信度 Confidence | 计算依据 Calculation Basis |
|---|---|---|---|
| 直接节约 Direct Savings | {{sc_p1_savings}} | {{sc_p1_sav_conf}} | {{sc_p1_sav_basis}} |
| 收入提升 Revenue Uplift | {{sc_p1_revenue}} | {{sc_p1_rev_conf}} | {{sc_p1_rev_basis}} |
| 风险规避 Risk Avoidance | {{sc_p1_risk_avoid}} | {{sc_p1_risk_conf}} | {{sc_p1_risk_basis}} |
| **年化总收益 Total Annual Benefit** | **{{sc_p1_total_benefit}}** | | |

**投资回报 ROI Metrics**:

| 指标 Metric | 数值 Value |
|---|---|
| NPV (3年, 折现率 {{discount_rate}}%) | {{sc_p1_npv}} |
| 回收期 Payback Period | {{sc_p1_payback}} |
| 3年 ROI | {{sc_p1_roi_3yr}}% |

### 5.3 组合 ROI 汇总 | Portfolio ROI Summary

| 类别 Category | 项目数 # Projects | 总投资 Total Investment | 年化收益 Annual Benefit | 加权 ROI | 加权回收期 Payback |
|---|---|---|---|---|---|
| 基础建设 Foundation | {{f_count}} | {{f_total_inv}} | {{f_total_benefit}} | {{f_roi}}% | {{f_payback}} |
| 快赢 Quick Win | {{qw_count}} | {{qw_total_inv}} | {{qw_total_benefit}} | {{qw_roi}}% | {{qw_payback}} |
| 战略 Strategic | {{st_count}} | {{st_total_inv}} | {{st_total_benefit}} | {{st_roi}}% | {{st_payback}} |
| 规模化 Scale | {{sc_count}} | {{sc_total_inv}} | {{sc_total_benefit}} | {{sc_roi}}% | {{sc_payback}} |
| **合计 Total** | **{{total_count}}** | **{{total_investment}}** | **{{total_annual_benefit}}** | **{{portfolio_roi}}%** | **{{portfolio_payback}}** |

### 5.4 现金流时间线 | Cash Flow Timeline (Year 0-3)

<!-- CONSULTANT NOTE: Show cumulative investment outflow vs. cumulative benefit inflow.
This visualization is critical for CFO buy-in — it shows when the portfolio "crosses
zero" and starts generating net positive returns. -->

{{cashflow_narrative}}

| 时间 Period | 累计投资 Cumulative Investment | 累计收益 Cumulative Benefit | 净现金流 Net Cash Flow | 备注 Notes |
|---|---|---|---|---|
| Year 0 (H1) | {{cf_y0h1_inv}} | {{cf_y0h1_ben}} | {{cf_y0h1_net}} | {{cf_y0h1_note}} |
| Year 0 (H2) | {{cf_y0h2_inv}} | {{cf_y0h2_ben}} | {{cf_y0h2_net}} | {{cf_y0h2_note}} |
| Year 1 (H1) | {{cf_y1h1_inv}} | {{cf_y1h1_ben}} | {{cf_y1h1_net}} | {{cf_y1h1_note}} |
| Year 1 (H2) | {{cf_y1h2_inv}} | {{cf_y1h2_ben}} | {{cf_y1h2_net}} | {{cf_y1h2_note}} |
| Year 2 (H1) | {{cf_y2h1_inv}} | {{cf_y2h1_ben}} | {{cf_y2h1_net}} | {{cf_y2h1_note}} |
| Year 2 (H2) | {{cf_y2h2_inv}} | {{cf_y2h2_ben}} | {{cf_y2h2_net}} | {{cf_y2h2_note}} |
| Year 3 | {{cf_y3_inv}} | {{cf_y3_ben}} | {{cf_y3_net}} | {{cf_y3_note}} |

### 5.5 组合敏感性分析 | Portfolio Sensitivity Analysis

<!-- CONSULTANT NOTE: Present three scenarios for the TOTAL portfolio. Vary the key
assumptions (adoption rate, benefit realization %, timeline slippage) to show the
range of possible outcomes. This builds credibility — it shows you have thought about
what could go wrong. -->

{{portfolio_sensitivity_narrative}}

| 情景 Scenario | 假设 Assumptions | 总投资 Investment | 总收益 (3yr) Benefit | ROI | 回收期 Payback |
|---|---|---|---|---|---|
| 乐观 Optimistic | {{opt_assumptions}} | {{opt_investment}} | {{opt_benefit}} | {{opt_roi}}% | {{opt_payback}} |
| **基准 Base** | **{{base_assumptions}}** | **{{base_investment}}** | **{{base_benefit}}** | **{{base_roi}}%** | **{{base_payback}}** |
| 悲观 Pessimistic | {{pes_assumptions}} | {{pes_investment}} | {{pes_benefit}} | {{pes_roi}}% | {{pes_payback}} |

> **So What 洞察**: {{portfolio_sensitivity_so_what}}

### 5.6 投资组合风险登记簿 | Portfolio Risk Register (Top 3)

<!-- CONSULTANT NOTE: Identify the top 3 risks to the investment portfolio and provide
specific, actionable mitigation strategies. These are not generic risks — they should
be specific to THIS client's situation and THIS portfolio of projects. -->

| 排名 # | 风险 Risk | 概率 Probability | 影响 Impact | 风险等级 Rating | 缓解策略 Mitigation Strategy | 责任方 Owner |
|---|---|---|---|---|---|---|
| R-1 | {{pr1_risk}} | {{pr1_prob}} | {{pr1_impact}} | {{pr1_rating}} | {{pr1_mitigation}} | {{pr1_owner}} |
| R-2 | {{pr2_risk}} | {{pr2_prob}} | {{pr2_impact}} | {{pr2_rating}} | {{pr2_mitigation}} | {{pr2_owner}} |
| R-3 | {{pr3_risk}} | {{pr3_prob}} | {{pr3_impact}} | {{pr3_rating}} | {{pr3_mitigation}} | {{pr3_owner}} |

> **So What 洞察**: {{portfolio_risk_so_what}}

---

<!-- ============================================================
     SECTION 6: BIDIRECTIONAL VERIFICATION
     ============================================================ -->

## 六、双向验证 | Module 6: Bidirectional Verification

<!-- CONSULTANT NOTE:
This section is the quality assurance checkpoint. It tests whether the entire report
is internally consistent — does every investment trace back to a bottleneck, to a
strategic objective? If not, either the analysis missed something or there is an
unjustified project in the portfolio. Be transparent about any gaps found.
-->

{{verification_intro_narrative}}

<!-- CONSULTANT NOTE: 2-3 sentences. Explain the purpose: "Bidirectional verification
ensures that our recommendations form an unbroken chain from strategic intent to
investment action. We test this chain in both directions." -->

### 自顶向下 Top-Down (战略 → 瓶颈 → AI场景 → IT覆盖 → 投资)

| 验证链 Verification Link | 关联度 Alignment | 状态 Status | 说明 Notes |
|---|---|---|---|
| 战略目标 → 瓶颈关联度 Strategy → Bottleneck | {{td_score_1}}% | {{td_status_1}} | {{td_note_1}} |
| 瓶颈 → AI场景覆盖度 Bottleneck → AI Scenario | {{td_score_2}}% | {{td_status_2}} | {{td_note_2}} |
| AI场景 → IT覆盖关联度 AI Scenario → IT Coverage | {{td_score_3}}% | {{td_status_3}} | {{td_note_3}} |
| IT覆盖 → 投资关联度 IT Coverage → Investment | {{td_score_4}}% | {{td_status_4}} | {{td_note_4}} |

### 自底向上 Bottom-Up (投资 → IT系统 → 瓶颈 → 战略)

| 验证链 Verification Link | 可追溯率 Traceability | 状态 Status | 说明 Notes |
|---|---|---|---|
| 投资项目 → IT系统 Investment → IT System | {{bu_score_1}}% | {{bu_status_1}} | {{bu_note_1}} |
| IT系统 → 瓶颈 IT System → Bottleneck | {{bu_score_2}}% | {{bu_status_2}} | {{bu_note_2}} |
| 瓶颈 → 战略目标 Bottleneck → Strategy | {{bu_score_3}}% | {{bu_status_3}} | {{bu_note_3}} |

### 缺口分析 | Gap Analysis

{{verification_gap_narrative}}

<!-- CONSULTANT NOTE: If any verification link scores below 80%, explain WHY there is
a gap. Common reasons: orphan projects (investment without strategic linkage), unaddressed
bottlenecks (bottleneck without investment), or capability overlaps (multiple projects
solving the same problem). Be specific and prescriptive. -->

| 缺口类型 Gap Type | 具体说明 Description | 建议措施 Recommended Action |
|---|---|---|
| {{gap1_type}} | {{gap1_description}} | {{gap1_action}} |
| {{gap2_type}} | {{gap2_description}} | {{gap2_action}} |

> **So What 洞察**: {{verification_so_what}}

---

<!-- ============================================================
     SECTION 7: RISK SCENARIO ANALYSIS (NEW)
     ============================================================ -->

## 七、风险情景分析 | Module 7: Risk Scenario Analysis

<!-- CONSULTANT NOTE:
This section is ENTIRELY NEW and addresses a critical gap in the previous template.
Clients need to understand not just the expected outcome but the range of possible
outcomes. Present three fully developed scenarios with internally consistent
assumptions. This is NOT the same as the sensitivity analysis in Section 5 — that
varies individual parameters; this section constructs coherent alternative futures.
-->

{{risk_scenario_intro_narrative}}

<!-- CONSULTANT NOTE: 3-4 sentences. Frame the purpose: "Strategy execution does not
occur in a vacuum. Market conditions, organizational readiness, and technology maturity
can shift the outcome of this transformation program significantly. We model three
coherent scenarios to bound the range of likely outcomes and identify the decision
points that determine which scenario materializes." -->

### 7.1 情景建模 | Scenario Modeling

#### 最佳情景 Best Case

{{best_case_narrative}}

| 维度 Dimension | 假设 Assumption | 影响 Impact |
|---|---|---|
| 时间线 Timeline | {{bc_timeline_assumption}} | {{bc_timeline_impact}} |
| 预算 Budget | {{bc_budget_assumption}} | {{bc_budget_impact}} |
| ROI | {{bc_roi_assumption}} | {{bc_roi_impact}} |
| 组织就绪度 Org Readiness | {{bc_org_assumption}} | {{bc_org_impact}} |

#### 基准情景 Base Case

{{base_case_narrative}}

| 维度 Dimension | 假设 Assumption | 影响 Impact |
|---|---|---|
| 时间线 Timeline | {{basec_timeline_assumption}} | {{basec_timeline_impact}} |
| 预算 Budget | {{basec_budget_assumption}} | {{basec_budget_impact}} |
| ROI | {{basec_roi_assumption}} | {{basec_roi_impact}} |
| 组织就绪度 Org Readiness | {{basec_org_assumption}} | {{basec_org_impact}} |

#### 最差情景 Worst Case

{{worst_case_narrative}}

| 维度 Dimension | 假设 Assumption | 影响 Impact |
|---|---|---|
| 时间线 Timeline | {{wc_timeline_assumption}} | {{wc_timeline_impact}} |
| 预算 Budget | {{wc_budget_assumption}} | {{wc_budget_impact}} |
| ROI | {{wc_roi_assumption}} | {{wc_roi_impact}} |
| 组织就绪度 Org Readiness | {{wc_org_assumption}} | {{wc_org_impact}} |

### 7.2 风险登记簿 | Risk Register (Top 5)

<!-- CONSULTANT NOTE: These are PROGRAM-LEVEL risks, broader than the portfolio risks
in Section 5.6. Include external risks (market, regulatory, competitive) as well as
internal risks (talent, change management, technology). -->

| 编号 # | 风险 Risk | 类别 Category | 概率 Prob (1-5) | 影响 Impact (1-5) | 风险分 Score | 缓解策略 Mitigation | 触发指标 Trigger |
|---|---|---|---|---|---|---|---|
| R-1 | {{rr1_risk}} | {{rr1_category}} | {{rr1_prob}} | {{rr1_impact}} | {{rr1_score}} | {{rr1_mitigation}} | {{rr1_trigger}} |
| R-2 | {{rr2_risk}} | {{rr2_category}} | {{rr2_prob}} | {{rr2_impact}} | {{rr2_score}} | {{rr2_mitigation}} | {{rr2_trigger}} |
| R-3 | {{rr3_risk}} | {{rr3_category}} | {{rr3_prob}} | {{rr3_impact}} | {{rr3_score}} | {{rr3_mitigation}} | {{rr3_trigger}} |
| R-4 | {{rr4_risk}} | {{rr4_category}} | {{rr4_prob}} | {{rr4_impact}} | {{rr4_score}} | {{rr4_mitigation}} | {{rr4_trigger}} |
| R-5 | {{rr5_risk}} | {{rr5_category}} | {{rr5_prob}} | {{rr5_impact}} | {{rr5_score}} | {{rr5_mitigation}} | {{rr5_trigger}} |

### 7.3 概率-影响矩阵 | Probability-Impact Matrix

```
影响 Impact →    1 低       2         3 中       4         5 高
概率                                                           
Prob ↓                                                         
5 高           |         |         |         | {{pi_54}} | {{pi_55}} |
4              |         |         | {{pi_43}} | {{pi_44}} | {{pi_45}} |
3 中           |         | {{pi_32}} | {{pi_33}} | {{pi_34}} |         |
2              | {{pi_21}} | {{pi_22}} | {{pi_23}} |         |         |
1 低           | {{pi_11}} | {{pi_12}} |         |         |         |
```

### 7.4 预警指标 | Early Warning Indicators

<!-- CONSULTANT NOTE: These are leading indicators that signal which scenario is
materializing. Define specific, measurable thresholds that trigger escalation or
course correction. This gives the client a monitoring framework — not just a plan. -->

{{early_warning_narrative}}

| 编号 # | 预警指标 Indicator | 监测频率 Monitoring Freq | 绿灯阈值 Green Threshold | 黄灯阈值 Yellow Threshold | 红灯阈值 Red Threshold | 响应措施 Response Action |
|---|---|---|---|---|---|---|
| EW-1 | {{ew1_indicator}} | {{ew1_freq}} | {{ew1_green}} | {{ew1_yellow}} | {{ew1_red}} | {{ew1_action}} |
| EW-2 | {{ew2_indicator}} | {{ew2_freq}} | {{ew2_green}} | {{ew2_yellow}} | {{ew2_red}} | {{ew2_action}} |
| EW-3 | {{ew3_indicator}} | {{ew3_freq}} | {{ew3_green}} | {{ew3_yellow}} | {{ew3_red}} | {{ew3_action}} |
| EW-4 | {{ew4_indicator}} | {{ew4_freq}} | {{ew4_green}} | {{ew4_yellow}} | {{ew4_red}} | {{ew4_action}} |
| EW-5 | {{ew5_indicator}} | {{ew5_freq}} | {{ew5_green}} | {{ew5_yellow}} | {{ew5_red}} | {{ew5_action}} |

> **So What 洞察**: {{risk_scenario_so_what}}

---

<!-- ============================================================
     SECTION 8: IMPLEMENTATION ROADMAP
     ============================================================ -->

## 八、实施路线图 | Module 8: Implementation Roadmap

<!-- CONSULTANT NOTE:
Use a phase-gate approach. Each phase has clear deliverables, decision criteria, and
resource requirements. The Go/No-Go gates force explicit executive decisions — this
prevents scope creep and ensures continued alignment with strategic intent.
-->

{{roadmap_intro_narrative}}

<!-- CONSULTANT NOTE: 3-4 sentences. Frame the sequencing logic: why this order? What
dependencies drive the phasing? What is the critical path? -->

### 8.1 阶段总览 | Phase Overview

```
月 Month   0    3    6    9    12   15   18   21   24   27   30
           │    │    │    │    │    │    │    │    │    │    │
Phase 0    ├────┤ 基础建设 Foundation
           │    Gate 1
Phase 1    │    ├─────────┤ 快赢 Quick Wins
           │    │         Gate 2
Phase 2    │    │         ├──────────────────┤ 战略项目 Strategic
           │    │         │                  Gate 3
Phase 3    │    │         │                  ├──────────────────┤ 规模化 Scale
           │    │         │                  │                  │
           ▼    ▼         ▼                  ▼                  ▼
```

### 8.2 Phase 0: 基础建设 Foundation (月 0-3)

**目标 Objective**: {{p0_objective}}

**关键交付物 Key Deliverables**:
{{p0_deliverables}}

**项目 Projects**: {{p0_projects}}

**资源需求 Resource Requirements**:

| 角色 Role | 人数 Headcount | 内部/外部 Internal/External | 说明 Notes |
|---|---|---|---|
| {{p0_r1_role}} | {{p0_r1_count}} | {{p0_r1_source}} | {{p0_r1_note}} |
| {{p0_r2_role}} | {{p0_r2_count}} | {{p0_r2_source}} | {{p0_r2_note}} |

**依赖 Dependencies**: {{p0_dependencies}}

#### Gate 1: 启动决策 | Go/No-Go Decision

| 决策标准 Criteria | 通过条件 Pass Condition | 状态 Status |
|---|---|---|
| {{g1_c1_criteria}} | {{g1_c1_condition}} | {{g1_c1_status}} |
| {{g1_c2_criteria}} | {{g1_c2_condition}} | {{g1_c2_status}} |
| {{g1_c3_criteria}} | {{g1_c3_condition}} | {{g1_c3_status}} |

---

### 8.3 Phase 1: 快赢项目 Quick Wins (月 3-9)

**目标 Objective**: {{p1_objective}}

**关键交付物 Key Deliverables**:
{{p1_deliverables}}

**项目 Projects**: {{p1_projects}}

**资源需求 Resource Requirements**:

| 角色 Role | 人数 Headcount | 内部/外部 Internal/External | 说明 Notes |
|---|---|---|---|
| {{p1_r1_role}} | {{p1_r1_count}} | {{p1_r1_source}} | {{p1_r1_note}} |
| {{p1_r2_role}} | {{p1_r2_count}} | {{p1_r2_source}} | {{p1_r2_note}} |
| {{p1_r3_role}} | {{p1_r3_count}} | {{p1_r3_source}} | {{p1_r3_note}} |

**依赖 Dependencies**: {{p1_dependencies}}

#### Gate 2: 扩展决策 | Go/No-Go Decision

| 决策标准 Criteria | 通过条件 Pass Condition | 状态 Status |
|---|---|---|
| {{g2_c1_criteria}} | {{g2_c1_condition}} | {{g2_c1_status}} |
| {{g2_c2_criteria}} | {{g2_c2_condition}} | {{g2_c2_status}} |
| {{g2_c3_criteria}} | {{g2_c3_condition}} | {{g2_c3_status}} |

---

### 8.4 Phase 2: 战略项目 Strategic (月 9-18)

**目标 Objective**: {{p2_objective}}

**关键交付物 Key Deliverables**:
{{p2_deliverables}}

**项目 Projects**: {{p2_projects}}

**资源需求 Resource Requirements**:

| 角色 Role | 人数 Headcount | 内部/外部 Internal/External | 说明 Notes |
|---|---|---|---|
| {{p2_r1_role}} | {{p2_r1_count}} | {{p2_r1_source}} | {{p2_r1_note}} |
| {{p2_r2_role}} | {{p2_r2_count}} | {{p2_r2_source}} | {{p2_r2_note}} |
| {{p2_r3_role}} | {{p2_r3_count}} | {{p2_r3_source}} | {{p2_r3_note}} |

**依赖 Dependencies**: {{p2_dependencies}}

#### Gate 3: 规模化决策 | Go/No-Go Decision

| 决策标准 Criteria | 通过条件 Pass Condition | 状态 Status |
|---|---|---|
| {{g3_c1_criteria}} | {{g3_c1_condition}} | {{g3_c1_status}} |
| {{g3_c2_criteria}} | {{g3_c2_condition}} | {{g3_c2_status}} |
| {{g3_c3_criteria}} | {{g3_c3_condition}} | {{g3_c3_status}} |

---

### 8.5 Phase 3: 规模化推广 Scale (月 18-30)

**目标 Objective**: {{p3_objective}}

**关键交付物 Key Deliverables**:
{{p3_deliverables}}

**项目 Projects**: {{p3_projects}}

**资源需求 Resource Requirements**:

| 角色 Role | 人数 Headcount | 内部/外部 Internal/External | 说明 Notes |
|---|---|---|---|
| {{p3_r1_role}} | {{p3_r1_count}} | {{p3_r1_source}} | {{p3_r1_note}} |
| {{p3_r2_role}} | {{p3_r2_count}} | {{p3_r2_source}} | {{p3_r2_note}} |
| {{p3_r3_role}} | {{p3_r3_count}} | {{p3_r3_source}} | {{p3_r3_note}} |

**依赖 Dependencies**: {{p3_dependencies}}

### 8.6 项目间依赖 | Inter-Project Dependencies

<!-- CONSULTANT NOTE: Map the critical dependencies between projects. A dependency
failure in Phase 0 can cascade through the entire program. Be explicit about which
dependencies are hard (blocking) vs. soft (preferred but not blocking). -->

{{dependencies_narrative}}

| 上游项目 Upstream | 下游项目 Downstream | 依赖类型 Type | 说明 Description |
|---|---|---|---|
| {{dep1_upstream}} | {{dep1_downstream}} | {{dep1_type}} | {{dep1_desc}} |
| {{dep2_upstream}} | {{dep2_downstream}} | {{dep2_type}} | {{dep2_desc}} |
| {{dep3_upstream}} | {{dep3_downstream}} | {{dep3_type}} | {{dep3_desc}} |
| {{dep4_upstream}} | {{dep4_downstream}} | {{dep4_type}} | {{dep4_desc}} |

> **So What 洞察**: {{roadmap_so_what}}

---

<!-- ============================================================
     APPENDIX
     ============================================================ -->

## 附录 | Appendix

### A. 术语表 | Glossary

参见 → `term-dictionary.md`

### B. 方法论 | Methodology

参见 → `methodology.md`

### C. AI 评分标准 | AI Scoring Criteria

参见 → `ai-native-scoring.md`

### D. 数据来源与假设清单 | Data Sources & Assumptions Register

<!-- CONSULTANT NOTE: Transparency about data sources and assumptions is a hallmark of
credible consulting work. List every material assumption and its source. -->

| 编号 # | 假设/数据 Assumption / Data Point | 来源 Source | 置信度 Confidence | 敏感性 Sensitivity |
|---|---|---|---|---|
| A-1 | {{a1_assumption}} | {{a1_source}} | {{a1_confidence}} | {{a1_sensitivity}} |
| A-2 | {{a2_assumption}} | {{a2_source}} | {{a2_confidence}} | {{a2_sensitivity}} |
| A-3 | {{a3_assumption}} | {{a3_source}} | {{a3_confidence}} | {{a3_sensitivity}} |
| A-4 | {{a4_assumption}} | {{a4_source}} | {{a4_confidence}} | {{a4_sensitivity}} |
| A-5 | {{a5_assumption}} | {{a5_source}} | {{a5_confidence}} | {{a5_sensitivity}} |

### E. 参考文件清单 | Reference Documents

| 文件 Document | 提供方 Provided By | 日期 Date |
|---|---|---|
| {{ref1_doc}} | {{ref1_provider}} | {{ref1_date}} |
| {{ref2_doc}} | {{ref2_provider}} | {{ref2_date}} |
| {{ref3_doc}} | {{ref3_provider}} | {{ref3_date}} |

---

*报告由 深略 · StratAlign v1.1.0 生成 | Generated by StratAlign Engine v1.1.0*
*支持中英双语报告输出 | Bilingual report output supported*

*本报告所含分析基于所提供的信息和既定假设。实际结果可能因市场条件、执行质量及其他外部因素而异。建议定期审视关键假设并根据实际进展调整规划。*

*This report is based on information provided and stated assumptions. Actual results may vary due to market conditions, execution quality, and other external factors. We recommend periodic review of key assumptions and adjustment of plans based on actual progress.*
