# 同辙 · StratAlign — 完整诊断报告模板
# Full Diagnostic Report Template

---

## 报告信息 | Report Information

- **企业名称 Company**: {{company_name}}
- **行业 Industry**: {{industry}}
- **报告日期 Date**: {{report_date}}
- **报告版本 Version**: v0.5.0-beta
- **分析师 Analyst**: 同辙 · StratAlign Engine

---

## 一、战略解码 | Module 1: Strategic Decoding

### 1.1 愿景与使命 | Vision & Mission

| 项目 Item | 内容 Content |
|---|---|
| 愿景 Vision | {{vision}} |
| 使命 Mission | {{mission}} |
| 核心价值观 Core Values | {{core_values}} |

### 1.2 战略主题 | Strategic Themes

| 编号 # | 战略主题 Theme | 优先级 Priority | 时间跨度 Horizon |
|---|---|---|---|
| ST-1 | {{theme_1}} | {{priority}} | {{horizon}} |
| ST-2 | {{theme_2}} | {{priority}} | {{horizon}} |
| ST-3 | {{theme_3}} | {{priority}} | {{horizon}} |

### 1.3 BSC 四维目标 | BSC Four-Perspective Objectives

#### 财务维度 | Financial Perspective
| 目标 Objective | KPI | 目标值 Target | 当前值 Current |
|---|---|---|---|
| {{fin_obj_1}} | {{kpi}} | {{target}} | {{current}} |

#### 客户维度 | Customer Perspective
| 目标 Objective | KPI | 目标值 Target | 当前值 Current |
|---|---|---|---|
| {{cust_obj_1}} | {{kpi}} | {{target}} | {{current}} |

#### 内部流程维度 | Internal Process Perspective
| 目标 Objective | KPI | 目标值 Target | 当前值 Current |
|---|---|---|---|
| {{proc_obj_1}} | {{kpi}} | {{target}} | {{current}} |

#### 学习与成长维度 | Learning & Growth Perspective
| 目标 Objective | KPI | 目标值 Target | 当前值 Current |
|---|---|---|---|
| {{learn_obj_1}} | {{kpi}} | {{target}} | {{current}} |

### 1.4 矛盾检测结果 | Contradiction Detection Results

⚠️ **检测到的矛盾 Contradictions Detected**: {{contradiction_count}}

| 编号 # | 矛盾类型 Type | 涉及目标 Objectives | 严重程度 Severity | 说明 Description |
|---|---|---|---|---|
| C-1 | {{type}} | {{obj_a}} ↔ {{obj_b}} | 🔴 高 / 🟡 中 / 🟢 低 | {{description}} |

**因果链完整性 Causal Chain Completeness**: {{completeness_pct}}%

**缺失维度 Missing Perspectives**: {{missing_perspectives}}

---

## 二、瓶颈扫描 | Module 2: Bottleneck Scan

### 2.1 业务流程痛点 | Business Process Pain Points

| 编号 # | 部门 Department | 痛点 Pain Point | 影响程度 Impact | 发生频率 Frequency |
|---|---|---|---|---|
| BP-1 | {{dept}} | {{pain_point}} | 高/中/低 | 日/周/月 |

### 2.2 能力差距分析 | Capability Gap Analysis

| 能力 Capability | 当前水平 Current (1-5) | 目标水平 Target (1-5) | 差距 Gap |
|---|---|---|---|
| {{capability}} | {{current}} | {{target}} | {{gap}} |

### 2.3 技术与组织债务 | Technical & Organizational Debt

| 类型 Type | 描述 Description | 紧迫度 Urgency | 估计修复成本 Est. Fix Cost |
|---|---|---|---|
| 技术债务 | {{tech_debt}} | {{urgency}} | {{cost}} |
| 组织债务 | {{org_debt}} | {{urgency}} | {{cost}} |

---

## 三、AI 原生潜力分诊 | Module 2.5: AI-Native Potential Triage

### 3.1 评分矩阵总览 | Scoring Matrix Overview

| 场景 Scenario | 规则显性度 Rule (1-5) | 数据模态 Data (1-5) | 决策频率 Freq (1-5) | AI原始分 Raw | 基础设施系数 Coeff | 最终得分 Final |
|---|---|---|---|---|---|---|
| {{scenario_1}} | {{rule}} | {{data}} | {{freq}} | {{raw}} | {{coeff}} | **{{final}}** |
| {{scenario_2}} | {{rule}} | {{data}} | {{freq}} | {{raw}} | {{coeff}} | **{{final}}** |
| {{scenario_3}} | {{rule}} | {{data}} | {{freq}} | {{raw}} | {{coeff}} | **{{final}}** |

> 公式 Formula: 最终得分 = (规则显性度 × 数据模态 × 决策频率) × 数据基础设施系数
> Final Score = (Rule Explicitness × Data Modality × Decision Frequency) × Data Infrastructure Coefficient

### 3.2 AI 场景排序 | AI Scenario Ranking

| 排名 Rank | 场景 Scenario | 最终得分 Score | 推荐级别 Recommendation |
|---|---|---|---|
| 🥇 1 | {{top_scenario}} | {{score}} | 立即启动 Immediate Start |
| 🥈 2 | {{second_scenario}} | {{score}} | 短期规划 Short-term Plan |
| 🥉 3 | {{third_scenario}} | {{score}} | 中期储备 Mid-term Reserve |

### 3.3 数据基础设施评估 | Data Infrastructure Assessment

| 数据域 Data Domain | 当前状态 Current State | 系数 Coefficient | 改进建议 Improvement |
|---|---|---|---|
| {{domain}} | 无/分散/结构化 | {{coeff}} | {{suggestion}} |

---

## 四、覆盖分析 | Module 3: Coverage Analysis

### 4.1 现有 IT 系统清单 | Current IT System Inventory

| 系统 System | 类型 Type | 覆盖业务 Coverage | 状态 Status | 上线年份 Year |
|---|---|---|---|---|
| {{system}} | ERP/CRM/MES/... | {{coverage}} | 运行中/待替换/待升级 | {{year}} |

### 4.2 业务能力 → IT 能力映射 | Business → IT Capability Mapping

| 业务能力 Biz Capability | IT 系统 IT System | 覆盖度 Coverage | 空白 Gap |
|---|---|---|---|
| {{biz_cap}} | {{it_system}} | ██░░░ {{pct}}% | {{gap_desc}} |

### 4.3 覆盖率汇总 | Coverage Summary

- **整体覆盖率 Overall Coverage**: {{overall_pct}}%
- **关键空白 Critical Gaps**: {{critical_gaps}}
- **冗余系统 Redundant Systems**: {{redundant_count}}

---

## 五、投资组合 | Module 4: Investment Portfolio

### 5.1 项目分组 | Project Grouping

#### 快赢项目 Quick Wins (0-6 月)
| 项目 Project | 预算 Budget | 预期 ROI | 风险 Risk | AI 得分 Score |
|---|---|---|---|---|
| {{project}} | {{budget}} | {{roi}} | 低/中/高 | {{ai_score}} |

#### 战略项目 Strategic (6-18 月)
| 项目 Project | 预算 Budget | 预期 ROI | 风险 Risk | AI 得分 Score |
|---|---|---|---|---|
| {{project}} | {{budget}} | {{roi}} | 低/中/高 | {{ai_score}} |

#### 基础项目 Foundation (持续)
| 项目 Project | 预算 Budget | 预期 ROI | 风险 Risk | 说明 Note |
|---|---|---|---|---|
| {{project}} | {{budget}} | {{roi}} | 低/中/高 | {{note}} |

### 5.2 ROI 估算汇总 | ROI Estimation Summary

| 类别 Category | 总预算 Total Budget | 预期收益 Expected Return | 加权 ROI | 回收期 Payback |
|---|---|---|---|---|
| 快赢 Quick Win | {{budget}} | {{return}} | {{roi}}% | {{months}} 月 |
| 战略 Strategic | {{budget}} | {{return}} | {{roi}}% | {{months}} 月 |
| 基础 Foundation | {{budget}} | — | 间接 Indirect | — |
| **合计 Total** | **{{total_budget}}** | **{{total_return}}** | **{{avg_roi}}%** | — |

### 5.3 实施路线图 | Implementation Roadmap

```
Q1          Q2          Q3          Q4          Q5          Q6
├── 快赢项目 ──┤
│   {{qw_1}}   │
│   {{qw_2}}   │
├──────── 战略项目 ────────────────────┤
│         {{st_1}}                      │
│              {{st_2}}                 │
├──────────────── 基础项目 ──────────────────────────────────┤
│                 {{fd_1}}                                    │
```

---

## 六、双向验证 | Bidirectional Verification

### 自顶向下 Top-Down (1→2→2.5→3→4)
- ✅ / ⚠️ 战略目标 → 瓶颈关联度: {{td_score}}%
- ✅ / ⚠️ 瓶颈 → AI场景覆盖度: {{td_ai_score}}%
- ✅ / ⚠️ AI场景 → IT覆盖关联度: {{td_it_score}}%
- ✅ / ⚠️ IT覆盖 → 投资关联度: {{td_inv_score}}%

### 自底向上 Bottom-Up (4→3→2→1)
- ✅ / ⚠️ 投资项目 → IT系统可追溯: {{bu_score_1}}%
- ✅ / ⚠️ IT系统 → 瓶颈可追溯: {{bu_score_2}}%
- ✅ / ⚠️ 瓶颈 → 战略目标可追溯: {{bu_score_3}}%

---

## 附录 | Appendix

### A. 术语表 | Glossary
参见 → `term-dictionary.md`

### B. 方法论 | Methodology
参见 → `methodology.md`

### C. AI 评分标准 | AI Scoring Criteria
参见 → `ai-native-scoring.md`

---

*报告由 同辙 · StratAlign v0.5.0-beta 自动生成 | Generated by StratAlign Engine*
