# 同辙 · StratAlign — 方法论参考
# Methodology Reference

---

## 一、平衡计分卡 (BSC) 四维指标体系
## 1. Balanced Scorecard (BSC) Four-Perspective Indicator System

> 基于 Kaplan & Norton (1992) 经典框架，结合数字化转型场景适配。
> Based on Kaplan & Norton (1992) classic framework, adapted for digital transformation context.

---

### 1.1 财务维度 | Financial Perspective

**核心问题**: 数字化转型如何创造股东价值？
**Core Question**: How does digital transformation create shareholder value?

| 编号 | 指标 Indicator | 度量方式 Measurement | 典型目标 Typical Target |
|---|---|---|---|
| F-1 | 数字化营收占比 Digital Revenue Ratio | 数字渠道营收 / 总营收 × 100% | ≥ 30% (3年) |
| F-2 | IT 投资回报率 IT ROI | (IT相关收益 - IT投入) / IT投入 × 100% | ≥ 150% |
| F-3 | 运营成本降低率 OpEx Reduction | (基线成本 - 当前成本) / 基线成本 × 100% | ≥ 15% |
| F-4 | 数字化项目 NPV Digital Project NPV | 项目净现值汇总 | > 0 |
| F-5 | 现金流改善周期 Cash Cycle Improvement | 应收账期缩短天数 | ≥ 10天 |

---

### 1.2 客户维度 | Customer Perspective

**核心问题**: 数字化如何提升客户体验与满意度？
**Core Question**: How does digitalization enhance customer experience and satisfaction?

| 编号 | 指标 Indicator | 度量方式 Measurement | 典型目标 Typical Target |
|---|---|---|---|
| C-1 | 客户满意度 CSAT | 调查评分 (1-10) | ≥ 8.5 |
| C-2 | 净推荐值 NPS | 推荐者% - 贬损者% | ≥ 40 |
| C-3 | 数字渠道客户占比 Digital Customer Ratio | 数字渠道客户 / 总客户 × 100% | ≥ 60% |
| C-4 | 客户响应时间 Response Time | 平均首次响应时间 (小时) | ≤ 2h |
| C-5 | 客户留存率 Retention Rate | 年度续约/复购客户占比 | ≥ 85% |

---

### 1.3 内部流程维度 | Internal Process Perspective

**核心问题**: 哪些流程需要数字化改造以支撑战略？
**Core Question**: Which processes need digital transformation to support strategy?

| 编号 | 指标 Indicator | 度量方式 Measurement | 典型目标 Typical Target |
|---|---|---|---|
| P-1 | 端到端流程自动化率 E2E Automation Rate | 自动化步骤 / 总步骤 × 100% | ≥ 60% |
| P-2 | 流程周期时间 Cycle Time | 关键流程平均完成时间 | 缩短 ≥ 40% |
| P-3 | 数据驱动决策比例 Data-Driven Decision Ratio | 数据辅助决策 / 总决策 × 100% | ≥ 70% |
| P-4 | 系统集成度 System Integration Level | 已集成系统 / 总系统 × 100% | ≥ 80% |
| P-5 | 异常检测准确率 Anomaly Detection Accuracy | 正确预警 / 总预警 × 100% | ≥ 90% |

---

### 1.4 学习与成长维度 | Learning & Growth Perspective

**核心问题**: 组织需要哪些能力建设来支撑数字化转型？
**Core Question**: What capabilities must the organization build to support digital transformation?

| 编号 | 指标 Indicator | 度量方式 Measurement | 典型目标 Typical Target |
|---|---|---|---|
| L-1 | 数字化人才比例 Digital Talent Ratio | 数字化岗位 / 总岗位 × 100% | ≥ 25% |
| L-2 | 员工数字技能认证率 Skill Certification Rate | 通过认证员工 / 总员工 × 100% | ≥ 50% |
| L-3 | 内部创新项目数 Innovation Projects | 年度孵化项目数量 | ≥ 10 |
| L-4 | 知识管理平台活跃度 KM Platform Activity | 月活用户 / 总员工 × 100% | ≥ 60% |
| L-5 | 组织敏捷度评分 Agility Score | 敏捷成熟度评估 (1-5) | ≥ 3.5 |

---

## 二、企业架构 (EA) 映射方法论
## 2. Enterprise Architecture (EA) Mapping Methodology

> 综合 TOGAF ADM 与 Zachman 框架，聚焦业务能力到 IT 能力的映射。
> Combining TOGAF ADM and Zachman Framework, focusing on business-to-IT capability mapping.

---

### 2.1 架构分层模型 | Architecture Layer Model

```
┌─────────────────────────────────────────┐
│         战略层 Strategy Layer            │  ← 愿景、使命、战略主题
├─────────────────────────────────────────┤
│       业务架构 Business Architecture     │  ← 业务能力、流程、组织
├─────────────────────────────────────────┤
│       数据架构 Data Architecture         │  ← 数据实体、数据流、数据质量
├─────────────────────────────────────────┤
│     应用架构 Application Architecture    │  ← 应用系统、接口、集成
├─────────────────────────────────────────┤
│     技术架构 Technology Architecture     │  ← 基础设施、平台、安全
└─────────────────────────────────────────┘
```

### 2.2 业务能力 → IT 能力映射 | Business → IT Capability Mapping

**映射步骤 Mapping Steps:**

1. **识别业务能力 Identify Business Capabilities**
   - 从战略主题分解核心业务能力 (Level 1-3)
   - Decompose core business capabilities from strategic themes

2. **评估当前 IT 覆盖 Assess Current IT Coverage**
   - 盘点现有系统对业务能力的支撑程度
   - Inventory existing system support for each capability

3. **识别空白与冗余 Identify Gaps & Redundancies**
   - 标记无系统覆盖的业务能力 (空白)
   - 标记多系统重叠覆盖的能力 (冗余)
   - Flag uncovered capabilities (gaps) and multi-system overlaps (redundancies)

4. **生成映射矩阵 Generate Mapping Matrix**

```
业务能力            ERP   CRM   MES   WMS   BI    空白
─────────────────────────────────────────────────────
订单管理             ██    ██    ░░    ░░    ░░    
生产计划             ██    ░░    ██    ░░    ░░    
质量检测             ░░    ░░    ██    ░░    ░░    
客户服务             ░░    ██    ░░    ░░    ░░    
供应链可视化         ░░    ░░    ░░    ██    ██    
智能预测             ░░    ░░    ░░    ░░    ░░    ⚠️ GAP
```

### 2.3 覆盖度评估标准 | Coverage Assessment Criteria

| 覆盖等级 Level | 说明 Description | 视觉标记 |
|---|---|---|
| 完全覆盖 Full | 系统完全满足业务能力需求 | ██ |
| 部分覆盖 Partial | 系统部分满足，存在功能缺口 | █░ |
| 无覆盖 None | 无系统支撑该业务能力 | ░░ ⚠️ |
| 冗余覆盖 Redundant | 多系统重复覆盖同一能力 | 🔄 |

---

## 三、双向验证方法 | Bidirectional Verification Method

### 3.1 自顶向下 Top-Down (1→2→2.5→3→4)

从战略出发，逐层向下验证一致性：

| 步骤 Step | 验证内容 Verification | 通过标准 Pass Criteria |
|---|---|---|
| 1→2 | 每个战略目标至少关联 1 个瓶颈 | 关联度 ≥ 80% |
| 2→2.5 | 每个关键瓶颈至少评估 1 个 AI 场景 | 覆盖度 ≥ 70% |
| 2.5→3 | 每个 AI 场景可追溯到 IT 系统需求 | 可追溯度 ≥ 90% |
| 3→4 | 每个 IT 需求纳入投资组合 | 纳入率 ≥ 85% |

### 3.2 自底向上 Bottom-Up (4→3→2→1)

从投资出发，逐层向上验证战略对齐：

| 步骤 Step | 验证内容 Verification | 通过标准 Pass Criteria |
|---|---|---|
| 4→3 | 每笔投资可追溯到 IT 系统/能力 | 可追溯度 ≥ 90% |
| 3→2 | 每个 IT 能力可追溯到业务瓶颈/目标 | 可追溯度 ≥ 85% |
| 2→1 | 每个瓶颈可追溯到战略目标 | 可追溯度 ≥ 80% |

**验证不通过处理 Failure Handling:**
- 如有投资项目无法追溯到战略目标 → 标记为"待论证"
- 如有战略目标无对应投资支撑 → 标记为"投资缺口"

---

## 四、投资分类框架 | Investment Classification Framework

### 4.1 三类分组 | Three Categories

| 类别 Category | 时间窗 Timeframe | 风险 Risk | ROI 预期 | 特征 Characteristics |
|---|---|---|---|---|
| 快赢 Quick Win | 0-6 月 | 低 | 高 (快) | 见效快、投入小、风险低 |
| 战略 Strategic | 6-18 月 | 中-高 | 高 (慢) | 转型核心、投入大、长期价值 |
| 基础 Foundation | 持续 Ongoing | 低-中 | 间接 | 基础设施、平台、能力建设 |

### 4.2 优先级评估 | Priority Assessment (RICE + MoSCoW 混合)

```
优先级得分 = (Reach × Impact × Confidence) / Effort
Priority Score = (R × I × C) / E

其中 Where:
  Reach = 影响范围 (1-10)
  Impact = 影响深度 (1-5)
  Confidence = 信心水平 (0.5/0.8/1.0)
  Effort = 工作量 (人月 person-months)
```

---

*方法论参考文献 References:*
- *Kaplan, R.S. & Norton, D.P. (1992). The Balanced Scorecard*
- *The Open Group (2018). TOGAF Standard, Version 9.2*
- *Zachman, J.A. (1987). A Framework for Information Systems Architecture*
