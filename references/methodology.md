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

## 五、战略假设清单 | Strategy Hypothesis Register

> 战略地图上的每一条因果链接都是一个待验证的假设。顾问的核心价值在于：
> 迫使客户把隐性假设显性化，然后设计度量方法来验证它们。
>
> Every causal link on a strategy map is a testable hypothesis. The consultant's core value
> lies in forcing clients to articulate their implicit assumptions, then designing measurements
> to test them.

---

### 5.1 If-Then-Because 假设格式 | Hypothesis Format

每条战略因果链接均应转化为结构化假设，采用 **If-Then-Because** 三段式：

Each strategic causal link should be converted into a structured hypothesis using the
**If-Then-Because** triad:

```
┌──────────────────────────────────────────────────────────────────┐
│                   HYPOTHESIS STRUCTURE                           │
│                                                                  │
│   IF   [我们采取某项行动 / We take a specific action]            │
│   THEN [将产生某个可度量的结果 / A measurable outcome occurs]     │
│   BECAUSE [背后的因果逻辑 / The underlying causal logic]         │
│                                                                  │
│   + 验证方法 Test Method: 如何用数据证实或证伪                    │
│   + 状态 Status: Untested / In-Test / Validated / Invalidated    │
└──────────────────────────────────────────────────────────────────┘
```

---

### 5.2 假设清单模板 | Hypothesis Register Template

以制造业数字化转型为例，覆盖 BSC 四大维度：

Example hypotheses for a manufacturing digital transformation, covering all four BSC perspectives:

| 假设编号 Hypothesis ID | If (行动 Action) | Then (结果 Outcome) | Because (逻辑 Logic) | 验证方法 Test Method | 状态 Status |
|---|---|---|---|---|---|
| H-001 | 投资 AI 视觉质检系统 Invest in AI visual quality inspection | 产品缺陷率降至 50 PPM 以下 Defect rate drops below 50 PPM | AI 视觉可检测人眼无法识别的微缺陷 AI vision detects micro-defects human eyes miss | 6个月 POC：对比 AI 与人工检测准确率 6-month POC: compare AI vs manual inspection accuracy | Untested |
| H-002 | 部署实时供应链可视化平台 Deploy real-time supply chain visibility platform | 库存周转率提升 25% Inventory turnover improves by 25% | 实时可视性消除信息延迟，减少安全库存 Real-time visibility eliminates information lag, reduces safety stock | 对比部署前后 6 个月的库存周转数据 Compare 6-month inventory turnover before/after deployment | Untested |
| H-003 | 实施客户自助服务门户 Implement customer self-service portal | 客户满意度 (CSAT) 从 7.2 提升至 8.5 CSAT improves from 7.2 to 8.5 | 客户偏好自主解决问题，减少等待时间 Customers prefer self-resolution; reduces wait time | A/B 测试：门户用户 vs 传统渠道用户满意度对比 A/B test: portal users vs traditional channel CSAT comparison | Untested |
| H-004 | 建立数字化技能认证体系 Establish digital skill certification program | 员工数字技能认证率达到 50% Skill certification rate reaches 50% | 结构化学习路径+激励机制加速技能获取 Structured learning paths + incentives accelerate skill acquisition | 按季度追踪认证通过率及技能应用率 Quarterly tracking of certification pass rate and skill application rate | Untested |
| H-005 | 将核心流程自动化率提升至 60% Raise core process automation to 60% | 运营成本降低 15% OpEx reduces by 15% | 自动化消除重复人工作业，减少错误返工 Automation eliminates repetitive manual work, reduces error rework | 逐流程度量：自动化前后的 FTE、周期时间、错误率 Per-process measurement: FTE, cycle time, error rate before/after | Untested |
| H-006 | 打通 ERP-MES-WMS 系统集成 Integrate ERP-MES-WMS systems end-to-end | 订单交付周期缩短 40% Order delivery cycle time reduces by 40% | 系统孤岛导致信息重复录入和延迟；集成消除断点 System silos cause redundant data entry and delays; integration eliminates breaks | 追踪 Order-to-Delivery 周期时间趋势 Track Order-to-Delivery cycle time trend | Untested |
| H-007 | 数字渠道营收占比达到 30% Digital channel revenue reaches 30% | 总营收增长 12% Total revenue grows by 12% | 数字渠道降低获客成本，扩大市场覆盖 Digital channels reduce CAC and expand market reach | 按渠道拆分营收，对比数字化渠道增量贡献 Revenue split by channel; measure digital channel incremental contribution | Untested |
| H-008 | 部署预测性维护系统 Deploy predictive maintenance system | 设备非计划停机减少 60% Unplanned downtime reduces by 60% | IoT 传感器+ML 模型可提前预警设备故障 IoT sensors + ML models provide early warning of equipment failure | 12个月对比：预测准确率、停机时长、维护成本 12-month comparison: prediction accuracy, downtime duration, maintenance cost | Untested |

---

### 5.3 假设验证工作流 | Hypothesis Validation Workflow

```
                    ┌───────────┐
                    │  Untested │  假设已登记，尚未开始验证
                    │  未验证    │  Hypothesis registered, not yet tested
                    └─────┬─────┘
                          │  启动验证 Start validation
                          v
                    ┌───────────┐
                    │  In-Test  │  数据收集中，实验进行中
                    │  验证中    │  Data collection in progress, experiment running
                    └─────┬─────┘
                          │  数据充分 Sufficient data
                     ┌────┴────┐
                     v         v
              ┌──────────┐  ┌─────────────┐
              │ Validated │  │ Invalidated │
              │ 已验证    │  │ 已证伪       │
              └──────────┘  └──────┬──────┘
                                   │  修订假设 Revise hypothesis
                                   v
                            ┌──────────┐
                            │ Refined  │  新假设进入下一轮验证
                            │ 已修订    │  Revised hypothesis enters next cycle
                            └──────────┘
```

**状态转换规则 State Transition Rules:**

| 当前状态 Current | 触发条件 Trigger | 目标状态 Target | 所需证据 Evidence Required |
|---|---|---|---|
| Untested | 验证计划批准且资源到位 Validation plan approved, resources allocated | In-Test | 签署的验证计划 Signed validation plan |
| In-Test | 数据支持假设 Data supports hypothesis | Validated | 统计显著性检验通过 Statistical significance test passed |
| In-Test | 数据否定假设 Data contradicts hypothesis | Invalidated | 否定证据及分析报告 Contradicting evidence and analysis report |
| Invalidated | 根因分析完成，假设修订 Root cause analysis done, hypothesis revised | Refined (→ Untested) | 修订后的假设文档 Revised hypothesis document |

---

### 5.4 战略地图即假设网络 | Strategy Map as Hypothesis Network

> 战略地图不是一张静态的因果图——它是一组相互关联的假设网络。
> 如果任何一个链接（假设）被证伪，所有下游假设都面临风险。
>
> A strategy map is not a static causal diagram -- it is a network of interlinked hypotheses.
> If any single link (hypothesis) is invalidated, all downstream hypotheses are at risk.

```
  学习与成长 Learning & Growth
  ┌──────────────────────────────────────────────────────────┐
  │  [H-004] 技能认证体系 ──────┐                            │
  │  Skill certification        │                            │
  └─────────────────────────────┼────────────────────────────┘
                                │ (IF skills improve...)
                                v
  内部流程 Internal Process
  ┌──────────────────────────────────────────────────────────┐
  │  [H-005] 流程自动化 ───┐  [H-006] 系统集成 ────┐        │
  │  Process automation    │  System integration   │        │
  └────────────────────────┼───────────────────────┼────────┘
                           │                       │
                           v                       v
  客户 Customer
  ┌──────────────────────────────────────────────────────────┐
  │  [H-003] 客户自助门户 ──── [H-001] AI质检(质量提升) ─┐   │
  │  Customer self-service     AI quality inspection     │   │
  └──────────────────────────────────────────────────────┼───┘
                                                         │
                                                         v
  财务 Financial
  ┌──────────────────────────────────────────────────────────┐
  │  [H-007] 数字渠道营收30%    [H-005→F] 运营成本降15%      │
  │  Digital revenue 30%       OpEx reduces 15%             │
  └──────────────────────────────────────────────────────────┘

  *** 如果 H-004 被证伪 → H-005, H-006 的前提条件不成立 → 整条链路受影响
  *** If H-004 is invalidated → H-005, H-006 premises fail → entire chain at risk
```

---

### 5.5 顾问操作指南 | Consultant Playbook

**何时使用 When to Use:**
- 战略研讨会结束后，将战略地图上每条因果箭头转化为 If-Then-Because 假设
- After strategy workshops, convert every causal arrow on the strategy map into an If-Then-Because hypothesis

**如何引导客户 How to Facilitate:**

1. **显性化隐性假设 Surface implicit assumptions**
   - 针对每条因果链接追问："你为什么相信 A 会导致 B？证据是什么？"
   - For each causal link, ask: "Why do you believe A leads to B? What is your evidence?"

2. **量化预期 Quantify expectations**
   - 将模糊表述转化为可度量目标："提升效率"→"流程周期缩短 40%"
   - Convert vague statements into measurable targets: "improve efficiency" → "cycle time reduces 40%"

3. **设计验证实验 Design validation experiments**
   - 为每条假设设计最小可行验证方案（POC / A-B 测试 / 先导项目）
   - Design minimum viable validation for each hypothesis (POC / A-B test / pilot)

4. **建立假设看板 Create hypothesis dashboard**
   - 可视化所有假设状态，在月度战略回顾会上更新
   - Visualize all hypothesis statuses; update in monthly strategy review meetings

5. **级联风险评估 Cascade risk assessment**
   - 识别关键路径上的假设：一旦证伪，影响范围最大的假设优先验证
   - Identify hypotheses on the critical path: prioritize validation for those with highest downstream impact if invalidated

---

## 六、能力分层分解 | L1-L2 Capability Decomposition

> 业务能力模型是战略与执行之间的桥梁。它回答一个核心问题：
> "企业需要具备哪些能力来执行其战略？"
>
> The Business Capability Model is the bridge between strategy and execution.
> It answers one core question: "What capabilities must the enterprise possess
> to execute its strategy?"

---

### 6.1 能力层级定义 | Capability Level Definitions

```
┌─────────────────────────────────────────────────────────────────────┐
│  L0: 企业 Enterprise                                               │
│  ┌───────────────────────────────────────────────────────────────┐  │
│  │  L1: 能力域 Capability Domain                                 │  │
│  │  (企业级核心能力领域，通常 6-10 个)                              │  │
│  │  (Enterprise-level core capability areas, typically 6-10)     │  │
│  │  ┌─────────────────────────────────────────────────────────┐  │  │
│  │  │  L2: 能力组件 Capability Component                      │  │  │
│  │  │  (每个 L1 下 3-6 个组件)                                 │  │  │
│  │  │  (3-6 components per L1 domain)                         │  │  │
│  │  │  ┌───────────────────────────────────────────────────┐  │  │  │
│  │  │  │  L3: 能力活动 Capability Activity (可选 Optional)  │  │  │  │
│  │  │  │  (每个 L2 下的具体活动，按需展开)                    │  │  │  │
│  │  │  │  (Specific activities under each L2, expand as     │  │  │  │
│  │  │  │   needed)                                          │  │  │  │
│  │  │  └───────────────────────────────────────────────────┘  │  │  │
│  │  └─────────────────────────────────────────────────────────┘  │  │
│  └───────────────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────────────┘
```

| 层级 Level | 名称 Name | 定义 Definition | 数量范围 Typical Count |
|---|---|---|---|
| L0 | 企业 Enterprise | 整个组织，作为能力分解的起点 The entire organization as the starting point | 1 |
| L1 | 能力域 Capability Domain | 企业运营所需的核心能力领域 Core capability areas required for operations | 6-10 per enterprise |
| L2 | 能力组件 Capability Component | 每个能力域下的具体能力单元 Specific capability units within each domain | 3-6 per L1 |
| L3 | 能力活动 Capability Activity | 可选细分，描述具体的业务活动 Optional granularity, describes specific activities | 2-5 per L2 |

---

### 6.2 制造业 L1-L2 能力地图模板 | Manufacturing L1-L2 Capability Map Template

以下模板适用于中型制造企业，顾问可根据具体行业和企业特征调整：

The following template is suitable for mid-size manufacturing enterprises. Consultants
should adapt based on specific industry and enterprise characteristics:

```
L0: 精密制造企业 Precision Manufacturing Enterprise
│
├── L1: 产品研发 Product Development
│   ├── L2: 产品设计 Product Design
│   ├── L2: 原型验证 Prototyping & Validation
│   ├── L2: 工艺开发 Process Engineering
│   └── L2: 产品生命周期管理 Product Lifecycle Mgmt (PLM)
│
├── L1: 供应链管理 Supply Chain Management
│   ├── L2: 采购管理 Procurement
│   │   └── L3: 寻源 Sourcing | 询报价 RFQ | 采购订单 PO Mgmt | 收货 Receiving
│   ├── L2: 物流管理 Logistics
│   ├── L2: 库存管理 Inventory Management
│   ├── L2: 供应商管理 Supplier Management
│   └── L2: 需求计划 Demand Planning
│
├── L1: 生产制造 Manufacturing Operations
│   ├── L2: 生产计划与排程 Production Planning & Scheduling
│   ├── L2: 车间执行 Shop Floor Execution
│   ├── L2: 质量管理 Quality Management
│   ├── L2: 设备管理 Equipment / Asset Management
│   └── L2: 安全与环保 Safety & Environmental Compliance
│
├── L1: 客户关系管理 Customer Relationship Management
│   ├── L2: 销售管理 Sales Management
│   ├── L2: 市场营销 Marketing
│   ├── L2: 客户服务 Customer Service
│   └── L2: 客户分析 Customer Analytics
│
├── L1: 财务管理 Financial Management
│   ├── L2: 财务核算 Financial Accounting
│   ├── L2: 管理会计 Management Accounting
│   ├── L2: 资金管理 Treasury & Cash Management
│   └── L2: 税务与合规 Tax & Compliance
│
├── L1: 人力资源管理 Human Resource Management
│   ├── L2: 人才获取 Talent Acquisition
│   ├── L2: 绩效管理 Performance Management
│   ├── L2: 学习发展 Learning & Development
│   └── L2: 薪酬福利 Compensation & Benefits
│
├── L1: 信息技术 Information Technology
│   ├── L2: 应用管理 Application Management
│   ├── L2: 基础设施 Infrastructure & Operations
│   ├── L2: 数据管理 Data Management
│   ├── L2: 信息安全 Information Security
│   └── L2: IT 治理 IT Governance
│
└── L1: 企业管理 Corporate Management
    ├── L2: 战略规划 Strategic Planning
    ├── L2: 风险管理 Risk Management
    ├── L2: 法务合规 Legal & Compliance
    └── L2: 行政管理 Administration
```

---

### 6.3 行业适配指南 | Industry Adaptation Guide

不同行业需要调整 L1 能力域。以下为常见行业的差异化能力域：

Different industries require L1 capability domain adjustments. Common industry-specific
domains include:

| 行业 Industry | 特有 L1 能力域 Industry-Specific L1 Domains | 备注 Notes |
|---|---|---|
| 离散制造 Discrete Mfg | 产品研发、生产制造、设备管理 | 本模板默认场景 Default in this template |
| 流程制造 Process Mfg | 配方管理、批次追溯、过程控制 | 替换"产品研发"为"配方管理" |
| 零售 Retail | 门店运营、品类管理、全渠道 | 新增"门店运营"；弱化"生产制造" |
| 金融服务 Financial Services | 风控合规、产品精算、渠道管理 | 新增"风控合规"；移除"生产制造" |
| 医疗健康 Healthcare | 临床运营、医疗质量、合规审查 | 高度监管行业，合规能力权重高 |

**适配步骤 Adaptation Steps:**

1. 以本模板为起点，与客户业务领导逐一确认 L1 能力域
2. 对不适用的 L1 进行替换或删除，对缺失的行业特有能力进行补充
3. 在每个 L1 下与业务专家共同分解 L2 能力组件
4. 仅在需要细粒度分析时（如 IT 系统映射）展开 L3

---

### 6.4 能力→IT 系统映射 | Capability-to-IT System Mapping

将 L2 能力与支撑 IT 系统关联，生成覆盖度矩阵（与 2.2 节联动）：

Map L2 capabilities to supporting IT systems to generate a coverage matrix
(connects to Section 2.2):

| L1 能力域 | L2 能力组件 | 主系统 Primary | 辅系统 Secondary | 覆盖度 Coverage |
|---|---|---|---|---|
| 供应链管理 | 采购管理 Procurement | ERP | SRM | ██ Full |
| 供应链管理 | 库存管理 Inventory | ERP + WMS | — | ██ Full |
| 供应链管理 | 需求计划 Demand Planning | — | Excel | ░░ ⚠️ Gap |
| 生产制造 | 车间执行 Shop Floor | MES | — | ██ Full |
| 生产制造 | 质量管理 Quality | MES (部分) | — | █░ Partial |
| 生产制造 | 设备管理 Equipment | — | — | ░░ ⚠️ Gap |
| 客户关系 | 销售管理 Sales | CRM | — | ██ Full |
| 客户关系 | 客户分析 Analytics | — | BI (手工) | █░ Partial |
| 信息技术 | 数据管理 Data Mgmt | — | — | ░░ ⚠️ Gap |

---

### 6.5 能力热力图 | Capability Heat Map

对每个 L2 能力按成熟度 1-5 级进行评分，可视化组织能力强弱：

Score each L2 capability on a 1-5 maturity scale to visualize organizational
strengths and weaknesses:

**成熟度等级定义 Maturity Level Definitions:**

| 等级 Level | 名称 Name | 定义 Definition | 热力颜色 Heat Color |
|---|---|---|---|
| 1 | 初始 Initial | 临时性、无标准流程 Ad-hoc, no standard process | ░░░ 红 Red |
| 2 | 可重复 Repeatable | 有基本流程但依赖个人 Basic process, person-dependent | ░░█ 橙 Orange |
| 3 | 已定义 Defined | 标准化流程已文档化 Standardized and documented | ░██ 黄 Yellow |
| 4 | 已管理 Managed | 流程可度量且持续优化 Measurable and continuously improved | ███ 浅绿 Light Green |
| 5 | 优化 Optimized | 行业领先，持续创新 Industry-leading, continuously innovating | ███ 深绿 Dark Green |

**热力图示例 Heat Map Example (制造企业 Manufacturing):**

```
                          成熟度 Maturity
L1 能力域              L2 能力组件            1    2    3    4    5
─────────────────────────────────────────────────────────────────
产品研发               产品设计               ·    ·    ·    ■    ·    [4]
Product Dev            原型验证               ·    ·    ■    ·    ·    [3]
                       工艺开发               ·    ·    ■    ·    ·    [3]
                       PLM                    ·    ■    ·    ·    ·    [2]
─────────────────────────────────────────────────────────────────
供应链管理             采购管理               ·    ·    ·    ■    ·    [4]
Supply Chain           物流管理               ·    ·    ■    ·    ·    [3]
                       库存管理               ·    ·    ·    ■    ·    [4]
                       供应商管理             ·    ·    ■    ·    ·    [3]
                       需求计划               ·    ■    ·    ·    ·    [2]  <-- 薄弱
─────────────────────────────────────────────────────────────────
生产制造               生产计划               ·    ·    ■    ·    ·    [3]
Manufacturing          车间执行               ·    ·    ·    ■    ·    [4]
                       质量管理               ·    ·    ■    ·    ·    [3]
                       设备管理               ■    ·    ·    ·    ·    [1]  <-- 薄弱
                       安全环保               ·    ·    ■    ·    ·    [3]
─────────────────────────────────────────────────────────────────
信息技术               应用管理               ·    ·    ■    ·    ·    [3]
IT                     基础设施               ·    ·    ·    ■    ·    [4]
                       数据管理               ■    ·    ·    ·    ·    [1]  <-- 薄弱
                       信息安全               ·    ·    ■    ·    ·    [3]
                       IT 治理                ·    ■    ·    ·    ·    [2]
─────────────────────────────────────────────────────────────────

  ■ = 当前成熟度 Current maturity rating
  红色区域 (1-2): 需要重点投资    Requires priority investment
  绿色区域 (4-5): 竞争优势来源    Source of competitive advantage
```

---

## 七、应用组合健康度四象限 | Application Portfolio Health Quadrant

> 企业通常拥有数十甚至数百个应用系统。并非所有系统都值得投资维护——
> 关键是区分哪些是战略资产、哪些应该淘汰。
>
> Enterprises typically own dozens or even hundreds of applications. Not all deserve
> continued investment -- the key is distinguishing strategic assets from candidates
> for elimination.

---

### 7.1 四象限模型 | Quadrant Model

```
    技术健康度 Technical Health
    High
     ^
     |
     |  TOLERATE (容忍)           STRATEGIC ASSETS (战略资产)
     |  低价值 + 高健康            高价值 + 高健康
     |  Low Value + High Health   High Value + High Health
     |                            
     |  维护现状，考虑合并          持续投资，增长优化
     |  Maintain; consider         Invest & grow
     |  consolidation              
     |                            
     |─────────────────────────────────────────────────────>
     |                                        Business Value
     |  ELIMINATE (淘汰)           TRANSFORM (转型)         High
     |  低价值 + 低健康            高价值 + 低健康
     |  Low Value + Low Health    High Value + Low Health
     |                            
     |  计划退役，迁移数据          紧急：现代化或替换
     |  Phase out, migrate data   Urgent: modernize or replace
     |                            
    Low
```

---

### 7.2 业务价值评分标准 | Business Value Scoring Criteria (X 轴)

对每个应用系统的业务价值进行 1-5 分评估：

Score each application's business value on a 1-5 scale:

| 评分 Score | 等级 Rating | 评估标准 Criteria |
|---|---|---|
| 5 | 关键 Mission-Critical | 系统中断将直接导致营收损失或合规违规；核心业务流程完全依赖该系统 System outage directly causes revenue loss or compliance violation; core processes fully depend on it |
| 4 | 重要 Important | 支撑主要业务流程；有替代方案但切换成本高 Supports major business processes; alternatives exist but switching cost is high |
| 3 | 有用 Useful | 提升效率但非必需；中断后可通过人工流程临时替代 Improves efficiency but not essential; manual workaround possible during outage |
| 2 | 边缘 Marginal | 仅少数用户使用；功能与其他系统部分重叠 Used by few users; functionality partially overlaps with other systems |
| 1 | 可弃 Disposable | 几乎无人使用或功能已被其他系统完全替代 Nearly unused or fully superseded by other systems |

**评分维度细化 Detailed Scoring Dimensions:**

| 维度 Dimension | 权重 Weight | 评估要点 Assessment Focus |
|---|---|---|
| 流程覆盖 Process Coverage | 30% | 支撑多少核心业务流程 How many core processes does it support |
| 用户规模 User Base | 20% | 日活 / 月活用户数 DAU / MAU |
| 数据资产 Data Assets | 20% | 承载的数据是否为核心业务资产 Does it hold core business data assets |
| 营收关联 Revenue Linkage | 20% | 是否直接关联收入生成 Directly linked to revenue generation |
| 合规要求 Compliance | 10% | 是否满足监管或合规要求 Required for regulatory compliance |

---

### 7.3 技术健康度评分标准 | Technical Health Scoring Criteria (Y 轴)

对每个应用系统的技术健康度进行 1-5 分评估：

Score each application's technical health on a 1-5 scale:

| 评分 Score | 等级 Rating | 评估标准 Criteria |
|---|---|---|
| 5 | 优秀 Excellent | 现代架构，厂商积极维护，安全补丁及时，可扩展性强 Modern architecture, active vendor support, timely patches, highly scalable |
| 4 | 良好 Good | 架构合理，厂商支持稳定，偶有技术债务但可控 Sound architecture, stable vendor support, minor tech debt but manageable |
| 3 | 一般 Adequate | 架构老化但仍可运行，厂商支持即将到期，存在已知安全风险 Aging architecture but operational, vendor support nearing EOL, known security risks |
| 2 | 较差 Poor | 遗留架构难以维护，依赖关键个人，安全漏洞频繁 Legacy architecture, hard to maintain, key-person dependent, frequent security issues |
| 1 | 危险 Critical | 厂商已停止支持，无法打补丁，存在重大安全隐患，随时可能故障 Vendor support ended, unpatchable, major security vulnerabilities, failure-prone |

**评分维度细化 Detailed Scoring Dimensions:**

| 维度 Dimension | 权重 Weight | 评估要点 Assessment Focus |
|---|---|---|
| 架构现代性 Architecture Modernity | 25% | 技术栈是否现代、是否支持 API / 微服务 Modern tech stack, API / microservice support |
| 可维护性 Maintainability | 25% | 代码质量、文档完整性、修改风险 Code quality, documentation, change risk |
| 安全性 Security | 20% | 漏洞数量、补丁频率、合规认证 Vulnerability count, patch frequency, certifications |
| 厂商支持 Vendor Support | 15% | 厂商支持状态 (主流支持 / 扩展支持 / 停止支持) Mainstream / Extended / End of support |
| 可扩展性 Scalability | 15% | 能否支撑未来 3 年业务增长 Can it support 3-year business growth |

---

### 7.4 应用组合仪表盘模板 | Portfolio Dashboard Template

将所有应用系统绘制在四象限中，形成全景视图：

Plot all applications on the quadrant to create a panoramic view:

```
  Tech Health
   5 |                                                     
     |  [OA系统]           [ERP]  [CRM]                    
   4 |       [邮件系统]              [BI平台]               
     |                         [WMS]                       
   3 |  [旧HR系统]                        [MES]            
     |           [旧报表]                                   
   2 |                              [旧质检系统]            
     |  [废弃OA]                                           
   1 |       [旧Excel工具]         [旧MRP]                  
     |________________________________________________     
     1      2      3      4      5   Business Value        

  ┌─────────────────────────────────────────────────────┐
  │  图例 Legend:                                        │
  │  右上 Top-Right:  战略资产 Strategic Assets          │
  │  左上 Top-Left:   容忍 Tolerate                      │
  │  右下 Bottom-Right: 转型 Transform (紧急 Urgent)     │
  │  左下 Bottom-Left:  淘汰 Eliminate                   │
  └─────────────────────────────────────────────────────┘
```

**仪表盘汇总表 Dashboard Summary Table:**

| 应用 Application | 业务价值 Biz Value | 技术健康 Tech Health | 象限 Quadrant | 建议行动 Recommended Action |
|---|---|---|---|---|
| ERP | 5 | 4 | 战略资产 Strategic | 持续投资，推进模块扩展 Continue investment |
| CRM | 4 | 4 | 战略资产 Strategic | 增强客户分析模块 Enhance analytics |
| MES | 5 | 3 | 转型 Transform | 升级架构，引入 IoT 集成 Modernize, add IoT |
| 旧质检系统 Legacy QC | 4 | 2 | 转型 Transform | 紧急替换为 AI 质检 Urgent: replace with AI QC |
| WMS | 4 | 3 | 战略资产 Strategic (边缘) | 评估升级路径 Evaluate upgrade path |
| BI 平台 | 3 | 4 | 容忍 Tolerate | 评估与 ERP 合并 Evaluate consolidation with ERP |
| 旧HR系统 Legacy HR | 2 | 3 | 容忍 Tolerate | 迁移至云端 HR SaaS Migrate to cloud HR SaaS |
| 旧MRP | 4 | 1 | 转型 Transform | 紧急：已停止支持，立即替换 Urgent: EOL, replace now |
| 旧报表 Legacy Reports | 2 | 2 | 淘汰 Eliminate | 数据迁移后退役 Retire after data migration |
| 废弃OA Deprecated OA | 1 | 1 | 淘汰 Eliminate | 立即停用 Decommission immediately |

---

### 7.5 评分工作坊顾问指南 | Scoring Workshop Facilitation Guide

**准备阶段 Preparation (工作坊前 1-2 周 1-2 weeks before):**

1. 收集应用清单：从 IT 部门获取完整的应用系统台账
   Collect application inventory: obtain complete system registry from IT department
2. 预填数据：基于系统文档预先填写技术健康度初评
   Pre-populate data: pre-score technical health based on system documentation
3. 邀请参与者：IT 负责人 + 各业务线负责人 (共同评分消除偏见)
   Invite participants: IT leaders + business line leaders (co-scoring reduces bias)

**工作坊流程 Workshop Agenda (约 3-4 小时 approx. 3-4 hours):**

| 环节 Phase | 时长 Duration | 活动 Activity |
|---|---|---|
| 开场 Opening | 15 min | 介绍四象限模型与评分标准 Introduce model and scoring criteria |
| 技术评分 Tech Scoring | 60 min | IT 团队主导，逐个应用评分 IT-led, score each application |
| 业务评分 Biz Scoring | 60 min | 业务团队主导，逐个应用评分 Business-led, score each application |
| 校准 Calibration | 30 min | 对齐分歧：业务与 IT 视角差异讨论 Align discrepancies between IT and business views |
| 定位 Plotting | 15 min | 将结果绘制到四象限图 Plot results on the quadrant |
| 行动规划 Action Planning | 30 min | 为每个象限制定行动策略 Define action strategy per quadrant |

**常见陷阱 Common Pitfalls:**
- IT 倾向于高估技术健康度（"我们的系统还能跑"）→ 用客观标准（厂商支持状态、CVE 数量）校准
  IT tends to overestimate tech health ("our system still runs") → calibrate with objective criteria
- 业务倾向于高估业务价值（"这个系统很重要"）→ 用数据（用户数、流程覆盖率）校准
  Business tends to overestimate value ("this system is important") → calibrate with data (user count, process coverage)
- 避免"所有系统都是战略资产"的结果——如果 >40% 落在右上象限，评分标准需要重新校准
  Avoid "everything is strategic" outcome -- if >40% lands in top-right, recalibrate scoring criteria

---

## 八、ROI 计算模板 | ROI Calculation Template

> ROI 计算是将战略假设转化为财务语言的关键步骤。
> 好的 ROI 模型不追求精确——而是让假设透明化，让决策者理解风险。
>
> ROI calculation is the critical step of translating strategic hypotheses into financial
> language. A good ROI model does not pursue precision -- it makes assumptions transparent
> and helps decision-makers understand risk.

---

### 8.1 成本模型 | Cost Model (五年 TCO Five-Year TCO)

将所有投资成本拆解为五大类，按年分摊：

Decompose all investment costs into five categories, distributed by year:

| 成本类别 Cost Category | Year 0 | Year 1 | Year 2 | Year 3 | Year 4 | Year 5 | 合计 Total |
|---|---|---|---|---|---|---|---|
| 许可/订阅费 License / Subscription | — | — | — | — | — | — | — |
| 实施费用 Implementation (含顾问) | — | — | — | — | — | — | — |
| 集成开发 Integration & Customization | — | — | — | — | — | — | — |
| 培训与变革管理 Training & Change Mgmt | — | — | — | — | — | — | — |
| 持续运营 Ongoing Operations (运维/支持) | — | — | — | — | — | — | — |
| **年度成本合计 Annual Cost Total** | **—** | **—** | **—** | **—** | **—** | **—** | **—** |

**成本估算注意事项 Cost Estimation Notes:**
- Year 0 = 项目启动年，包含大部分实施和集成成本
  Year 0 = Project launch year, contains most implementation and integration costs
- 许可费区分一次性买断 vs 年度订阅 (SaaS) 模式
  Distinguish one-time license vs annual subscription (SaaS) model
- 隐性成本不可忽略：数据迁移、并行运行期、生产力损失
  Hidden costs must not be ignored: data migration, parallel run period, productivity loss

---

### 8.2 收益模型 | Benefit Model

将收益分为三大类，每项均需量化依据：

Categorize benefits into three types; each must have a quantification basis:

| 收益类别 Benefit Category | 量化方式 Quantification Method | Year 1 | Year 2 | Year 3 | Year 4 | Year 5 | 合计 Total |
|---|---|---|---|---|---|---|---|
| **直接节约 Direct Savings** | | | | | | | |
| - 人力成本节约 Headcount Savings | 减少 FTE × 年均人力成本 Reduced FTE × avg labor cost | — | — | — | — | — | — |
| - 时间节约 Time Savings | 节约工时 × 时薪 Saved hours × hourly rate | — | — | — | — | — | — |
| - 错误减少 Error Reduction | 减少的返工/废品成本 Reduced rework/scrap cost | — | — | — | — | — | — |
| - 运营效率 Operational Efficiency | 流程自动化节约成本 Process automation savings | — | — | — | — | — | — |
| **营收提升 Revenue Uplift** | | | | | | | |
| - 新渠道营收 New Channel Revenue | 数字渠道增量营收 Digital channel incremental revenue | — | — | — | — | — | — |
| - 客户留存 Customer Retention | 留存率提升 × 客户终身价值 Retention uplift × CLV | — | — | — | — | — | — |
| - 交叉销售 Cross-sell / Up-sell | 新增销售机会 × 转化率 × 客单价 New opportunities × conversion × AOV | — | — | — | — | — | — |
| **风险规避 Risk Avoidance** | | | | | | | |
| - 合规罚款规避 Compliance Fine Avoidance | 预期罚款 × 发生概率 Expected fine × probability | — | — | — | — | — | — |
| - 停机损失规避 Downtime Loss Avoidance | 预期停机时长 × 每小时损失 Expected downtime × hourly loss | — | — | — | — | — | — |
| - 安全事件规避 Security Incident Avoidance | 预期损失 × 发生概率 Expected loss × probability | — | — | — | — | — | — |
| **年度收益合计 Annual Benefit Total** | | **—** | **—** | **—** | **—** | **—** | **—** |

---

### 8.3 NPV 与 ROI 计算 | NPV and ROI Calculation

**折现率 Discount Rate:** 默认 10% (可根据企业 WACC 调整)
Default 10% (adjust based on enterprise WACC)

**现金流时间线 Cash Flow Timeline:**

| 项目 Item | Year 0 | Year 1 | Year 2 | Year 3 | Year 4 | Year 5 |
|---|---|---|---|---|---|---|
| 成本 Costs (C) | — | — | — | — | — | — |
| 收益 Benefits (B) | 0 | — | — | — | — | — |
| 净现金流 Net Cash Flow (B-C) | — | — | — | — | — | — |
| 折现因子 Discount Factor (r=10%) | 1.000 | 0.909 | 0.826 | 0.751 | 0.683 | 0.621 |
| 折现净现金流 Discounted NCF | — | — | — | — | — | — |
| 累计折现净现金流 Cumulative DNCF | — | — | — | — | — | — |

**核心公式 Core Formulas:**

```
NPV (净现值 Net Present Value):

              n     B_t - C_t
  NPV  =  Sigma  ───────────
             t=0   (1 + r)^t

  其中 Where:
    B_t = 第 t 年收益 Benefits in year t
    C_t = 第 t 年成本 Costs in year t
    r   = 折现率 Discount rate (default 10%)
    n   = 评估周期 Evaluation period (default 5 years)


ROI (投资回报率 Return on Investment):

              NPV of Benefits - NPV of Costs
  ROI (%) = ─────────────────────────────────── × 100%
                     NPV of Costs


Payback Period (回收期):

  回收期 = 累计折现净现金流首次转正的年份
  Payback = Year when cumulative discounted NCF first turns positive
```

---

### 8.4 敏感性分析 | Sensitivity Analysis

> 单点估算毫无意义——真正的价值在于理解"如果假设变了，结果会怎样"。
>
> A single-point estimate is meaningless -- the real value is understanding
> "what happens if assumptions change."

**关键变量敏感性矩阵 Key Variable Sensitivity Matrix:**

选取 3-5 个对 ROI 影响最大的变量，分析 ±20% 变动对结果的影响：

Select 3-5 variables with the greatest ROI impact; analyze the effect of ±20% variation:

| 关键变量 Key Variable | 基准值 Base Value | -20% 值 | -20% ROI | 基准 ROI Base ROI | +20% 值 | +20% ROI | 敏感度 Sensitivity |
|---|---|---|---|---|---|---|---|
| 实施成本 Implementation Cost | — | — | — | — | — | — | 高/中/低 H/M/L |
| 人力成本节约 Headcount Savings | — | — | — | — | — | — | 高/中/低 H/M/L |
| 营收增长率 Revenue Growth Rate | — | — | — | — | — | — | 高/中/低 H/M/L |
| 采纳速度 Adoption Speed | — | — | — | — | — | — | 高/中/低 H/M/L |
| 折现率 Discount Rate | 10% | 8% | — | — | 12% | — | 高/中/低 H/M/L |

**龙卷风图 Tornado Chart (概念示意 Conceptual):**

```
  ROI 变动幅度 ROI Variation
  (相对基准 vs Baseline)

                    -30%  -20%  -10%   0   +10%  +20%  +30%
                      |     |     |    |    |     |     |
  营收增长率          ├─────────────────┼──────────────────┤
  Revenue Growth      |<=============================>|

  人力节约            ├────────────┼─────────────┤
  Headcount Save      |<==================>|

  实施成本            ├─────────┼──────────┤
  Impl. Cost          |<==============>|

  采纳速度            ├──────┼───────┤
  Adoption Speed      |<==========>|

  折现率              ├───┼────┤
  Discount Rate       |<=====>|
```

---

### 8.5 三场景分析 | Three-Scenario Analysis

为每个投资项目构建三种场景，附加概率权重计算期望 ROI：

Construct three scenarios for each investment, with probability weights to calculate
expected ROI:

| 场景 Scenario | 概率权重 Probability | 关键假设差异 Key Assumption Differences | NPV | ROI |
|---|---|---|---|---|
| 乐观 Optimistic | 20% | 采纳快于预期，收益上浮 20%，成本不超 Faster adoption, benefits +20%, cost on budget | — | — |
| 基准 Base Case | 60% | 按计划执行，收益与成本符合预期 On-plan execution, benefits and costs as estimated | — | — |
| 悲观 Pessimistic | 20% | 采纳慢于预期，收益下降 30%，成本超支 15% Slower adoption, benefits -30%, cost +15% overrun | — | — |

**期望 ROI 计算 Expected ROI Calculation:**

```
  Expected ROI = (P_opt × ROI_opt) + (P_base × ROI_base) + (P_pess × ROI_pess)

  期望 ROI = (20% × 乐观ROI) + (60% × 基准ROI) + (20% × 悲观ROI)

  示例 Example:
  Expected ROI = (0.20 × 280%) + (0.60 × 180%) + (0.20 × 60%)
               = 56% + 108% + 12%
               = 176%
```

**决策规则 Decision Rules:**

| 条件 Condition | 建议 Recommendation |
|---|---|
| 悲观场景 ROI > 0% | 低风险投资，推荐批准 Low-risk investment, recommend approval |
| 悲观场景 ROI < 0% 但基准 ROI > 50% | 中等风险，建议分阶段投资 Medium risk, recommend phased investment |
| 基准场景 ROI < 0% | 高风险，建议重新评估或放弃 High risk, recommend re-evaluation or abandonment |
| 期望 ROI < WACC | 不创造价值，不推荐 Does not create value, not recommended |

---

### 8.6 顾问操作指南 | Consultant Playbook for ROI

**ROI 估算常见陷阱 Common Pitfalls in ROI Estimation:**

1. **过度乐观的收益估算 Over-optimistic benefit estimation**
   - 症状：所有项目 ROI > 200%，没有项目失败
     Symptom: all projects show ROI > 200%, none fail
   - 对策：要求每项收益提供历史数据或行业基准支撑
     Countermeasure: require historical data or industry benchmarks for each benefit line

2. **忽略隐性成本 Ignoring hidden costs**
   - 症状：实施后实际花费远超预算
     Symptom: actual spend far exceeds budget post-implementation
   - 对策：显式列出数据迁移、并行运行、生产力下降等过渡期成本
     Countermeasure: explicitly list data migration, parallel run, productivity dip costs

3. **双重计算收益 Double-counting benefits**
   - 症状：多个项目声称同一笔节约
     Symptom: multiple projects claim the same savings
   - 对策：在投资组合层面汇总，去重交叉收益
     Countermeasure: aggregate at portfolio level, deduplicate cross-project benefits

4. **忽略时间价值 Ignoring time value of money**
   - 症状：简单加总未折现的现金流
     Symptom: summing undiscounted cash flows
   - 对策：始终使用 NPV，明确折现率假设
     Countermeasure: always use NPV, make discount rate assumption explicit

5. **缺乏敏感性分析 No sensitivity analysis**
   - 症状：只呈现单一数字，无法回答"如果...会怎样"
     Symptom: presenting a single number with no "what if" analysis
   - 对策：至少对 3 个关键变量做 ±20% 敏感性分析
     Countermeasure: perform ±20% sensitivity analysis on at least 3 key variables

**如何挑战客户假设 How to Challenge Client Assumptions:**

- 对每项收益追问：**"这个数字从哪里来？有没有历史数据支撑？"**
  For each benefit, ask: "Where does this number come from? Is there historical data?"
- 对人力节约追问：**"减少的 FTE 会被裁员还是重新部署？如果重新部署，节约在哪里？"**
  For headcount savings: "Will reduced FTEs be laid off or redeployed? If redeployed, where is the saving?"
- 对营收提升追问：**"竞争对手也在做同样的事，你的增量来自哪里？"**
  For revenue uplift: "Competitors are doing the same -- where does your increment come from?"
- 对实施成本追问：**"类似规模的项目行业平均超支多少？你的应急预算是多少？"**
  For implementation cost: "What is the industry average overrun for similar projects? What is your contingency?"

---

*方法论参考文献 References:*
- *Kaplan, R.S. & Norton, D.P. (1992). The Balanced Scorecard*
- *Kaplan, R.S. & Norton, D.P. (2004). Strategy Maps: Converting Intangible Assets into Tangible Outcomes*
- *The Open Group (2018). TOGAF Standard, Version 9.2*
- *Zachman, J.A. (1987). A Framework for Information Systems Architecture*
- *Ward, J. & Daniel, E. (2012). Benefits Management: How to Increase the Business Value of Your IT Projects*
- *Ross, J.W., Weill, P. & Robertson, D. (2006). Enterprise Architecture as Strategy*
- *Brealey, R.A., Myers, S.C. & Allen, F. (2020). Principles of Corporate Finance*

---

*Version: 1.0.0*
