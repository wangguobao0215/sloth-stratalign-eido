# 同辙 · StratAlign — 示例与演示 (咨询顾问视角)
# Examples & Demonstrations (Management Consultant Perspective)

> 版本 Version: 1.0.0 | 面向用户: 管理咨询顾问 | Target User: Management Consultants

---

## 示例企业背景 | Example Company Background

- **企业 Company**: 华远精密制造有限公司 (虚构 / Fictional)
- **行业 Industry**: 精密制造 — 汽车零部件 (Precision Manufacturing — Auto Parts)
- **规模 Scale**: 2,000 人, 年营收 15 亿元 (Mid-market)
- **现状 Current State**: SAP ERP (2018), 自研 MES (2020), Salesforce CRM (2019), 无统一数据平台
- **咨询背景 Engagement Context**: 某中型咨询公司 (方略咨询) 受聘开展为期 8 周的数字化转型战略项目。项目负责人为高级经理张磊，团队 3 人。
- **系统预设 System Pre-load**: 行业剧本 "manufacturing" 已自动加载；顾问选择 "加速模式 (Accelerated)"

> A mid-tier consulting firm ("FangLue Consulting") is engaged for an 8-week digital transformation strategy. Senior Manager Zhang Lei leads a 3-person team. The manufacturing industry playbook was auto-loaded and Accelerated mode selected.

---

## 示例一: 顾问启动与行业剧本激活 | Example 1: Consultant Onboarding & Industry Playbook Activation

Module 0 对话流程 — 顾问首次启动 StratAlign 时的引导交互:

**Step 1 — 行业选择 Industry Selection**

```
系统: 请选择客户所属行业 | Please select the client's industry:
  [1] 制造业 Manufacturing    [2] 金融服务 Financial Services
  [3] 零售/消费 Retail        [4] 医疗健康 Healthcare
  [5] 科技/互联网 Tech        [6] 其他 Other

顾问输入: 1
系统: 已选择 → 制造业。正在加载行业剧本 "manufacturing"...
```

**Step 2 — 企业规模 Company Size**

```
系统: 请选择企业规模 | Select company size:
  [1] 小型 Small (<500人)     [2] 中型 Mid-market (500-5,000人)
  [3] 大型 Large (5,000-20,000人)  [4] 超大型 Enterprise (>20,000人)

顾问输入: 2
系统: 已选择 → 中型企业 (Mid-market)
```

**Step 3 — 运行模式 Execution Mode**

```
系统: 请选择分析模式 | Select analysis mode:
  [1] 完整模式 Full (12-16周, 全量深度分析)
  [2] 加速模式 Accelerated (6-8周, 聚焦核心模块)
  [3] 快诊模式 Rapid Diagnostic (2-3周, 仅迷你诊断卡)

顾问输入: 2
系统: 已选择 → 加速模式。将执行: 战略解码 → 能力热力图 → AI评分 → 投资路线图
```

**Step 4 — 行业剧本预填确认 Playbook Pre-fill Review**

```
系统: 已加载制造业剧本，以下为预填默认值:

  BSC 标准维度:
    财务: 利润率提升、成本优化、资产周转率
    客户: 交付准时率(OTD)、质量合格率、客户满意度
    流程: 生产效率(OEE)、缺陷率(PPM)、供应链周期
    成长: 数字化人才占比、专利数、技能认证覆盖率

  AI 评分默认权重:
    规则显性度 25% | 数据就绪度 30% | 决策频率 20% | 实施复杂度 25%

  制造业常见场景预置 (可增删):
    ✓ 外观质检自动化    ✓ 预测性维护    ✓ 智能排产
    ✓ 供应链风险预警    ✓ 财务自动对账

  请确认或调整 (输入 "confirm" 确认 / 逐项修改编号):
顾问输入: confirm
系统: 预填已确认。开始战略解码...
```

---

## 示例二: 战略假设登记簿 | Example 2: Strategy Hypothesis Register

基于战略解码阶段提取的 BSC 四维目标，团队建立了 5 条核心假设:

Based on BSC objectives extracted during strategic decoding, the team established 5 core hypotheses:

| H-ID | If (如果) | Then (那么) | Because (因为) | 验证方法 Test Method | 状态 Status |
|------|-----------|-------------|----------------|---------------------|-------------|
| H-001 | 在生产线部署 AI 视觉质检 | PPM 将从 320 降至 50 以下 | 机器视觉可在 100% 检测率下识别人眼不可见的微缺陷 | Line 3 POC, 跟踪 2 个月 PPM | Pending |
| H-002 | 建设统一数据平台整合 SAP/MES/CRM | 跨部门决策周期缩短 40% | 消除人工数据对账瓶颈是决策延迟的首要原因 | 对比 3 个关键流程决策周期 | Pending |
| H-003 | 数字化人才占比从 8% 提升至 20% | 可同时支撑 3 个以上数字化项目并行 | 当前 12 人 IT 团队无力支撑并发项目 | 12 个月内跟踪活跃项目数与交付质量 | Pending |
| H-004 | 对关键设备实施预测性维护 | 非计划停机减少 60%, OTD 从 89% 提升至 98%+ | 当前 70% 交付延误可追溯至设备故障 | 部署后 6 个月监测停机与 OTD 相关性 | Pending |
| H-005 | 财务对账实施 RPA 作为快赢项目 | 3 个月内展示 AI 投资回报 | 该流程规则明确、数据完备、集成复杂度极低 | 对比对账耗时与错误率 | Pending |

**顾问注释 Consultant Notes**:

> H-001 和 H-004 构成因果链: 质检改善 (H-001) + 设备可靠性 (H-004) → OTD 提升 → 客户满意度 → 利润率。若 H-004 的 "70% 归因设备故障" 假设不成立，整条链需要重构。建议优先验证 H-004 的因果归因。

---

## 示例三: AI 加权评分模型 | Example 3: AI Scoring — Weighted Model

### 3.1 评分模型说明 | Scoring Model Specification

**四维加权模型 (替代旧版乘法模型)**:

| 维度 Dimension | 代码 | 权重 Weight | 含义 |
|---------------|------|-------------|------|
| 规则显性度 Rule Explicitness | R | 25% | 业务规则可编码程度 (1=隐性经验, 5=完全文档化) |
| 数据就绪度 Data Readiness | D | 30% | 数据可用性与质量 (1=无数据, 5=结构化+标注) |
| 决策频率 Decision Frequency | F | 20% | 决策触发频次 (1=年度, 5=实时/逐件) |
| 实施复杂度 Impl. Complexity | C | 25% | 落地难度反转分 (1=极复杂, 5=开箱即用) |

**计算公式 Formula**:
```
加权原始分 Weighted Raw = 0.25 x R + 0.30 x D + 0.20 x F + 0.25 x C   (范围 1.0 - 5.0)
归一化百分 Normalized   = Raw x 20                                       (范围 20 - 100)
最终得分   Final Score  = Normalized x Scenario Data Coefficient          (范围 0 - 100)
```

**场景数据系数 Scenario Data Coefficient**: 每个场景独立评估数据可得性 (0.0-1.0)，取代旧版全局系数。

**分级标准 Tier Thresholds**:
| Tier | 得分范围 | 标签 | 建议 |
|------|---------|------|------|
| Tier 1 | 75 - 100 | 立即优先 Immediate Priority | 快赢或战略首批启动 |
| Tier 2 | 50 - 74 | 战略投资 Strategic Investment | 纳入 12 个月路线图 |
| Tier 3 | 25 - 49 | 夯实基础 Foundation First | 先补齐前置条件 |
| Tier 4 | 0 - 24 | 暂缓观察 Deprioritize / Monitor | 条件不成熟，持续关注 |

### 3.2 五场景评分明细 | Five Scenarios — Detailed Scoring

| 场景 Scenario | R | D | F | C | 加权原始分 | 归一化 | 数据系数 | 最终得分 | Tier | 排名 |
|--------------|---|---|---|---|-----------|--------|---------|---------|------|------|
| 成品外观质检 | 4 | 3 | 5 | 3 | 3.65 | 73.0 | 0.6 | **43.8** | Tier 3 | 3 |
| 设备预测维护 | 3 | 4 | 4 | 3 | 3.50 | 70.0 | 0.8 | **56.0** | Tier 2 | 2 |
| 智能排产优化 | 3 | 3 | 3 | 2 | 2.75 | 55.0 | 0.6 | **33.0** | Tier 3 | 4 |
| 供应商风险预警 | 2 | 2 | 2 | 4 | 2.50 | 50.0 | 0.4 | **20.0** | Tier 4 | 5 |
| 财务智能对账 | 5 | 4 | 2 | 5 | 4.10 | 82.0 | 1.0 | **82.0** | Tier 1 | 1 |

**详细计算示范 Worked Examples**:

**财务智能对账** (排名第 1):
```
Raw = 0.25 x 5 + 0.30 x 4 + 0.20 x 2 + 0.25 x 5
    = 1.25  +  1.20  +  0.40  +  1.25  = 4.10
Normalized = 4.10 x 20 = 82.0
Final = 82.0 x 1.0 (数据完备, ERP 财务模块数据质量高) = 82.0 → Tier 1
```

**成品外观质检** (排名第 3):
```
Raw = 0.25 x 4 + 0.30 x 3 + 0.20 x 5 + 0.25 x 3
    = 1.00  +  0.90  +  1.00  +  0.75  = 3.65
Normalized = 3.65 x 20 = 73.0
Final = 73.0 x 0.6 (图像数据未结构化, 需新建采集基础设施) = 43.8 → Tier 3
```

> **顾问洞察**: 成品外观质检的归一化分 (73.0) 实际很高，被低数据系数 (0.6) 拉低。这意味着一旦补齐图像数据基础设施，该场景将跃升至 Tier 1。这是典型的 "基础设施解锁型" 机会。

### 3.3 敏感性分析 | Sensitivity Analysis

**情景: 若决策频率权重提升至 40% (管理层更看重实时性)**

调整权重: R=20%, D=20%, F=40%, C=20%

| 场景 | 默认最终分 | 调整后最终分 | Tier 变化 |
|------|-----------|-------------|----------|
| 财务智能对账 | 82.0 | 72.0 | Tier 1 → **Tier 2** |
| 设备预测维护 | 56.0 | 57.6 | 不变 |
| 成品外观质检 | 43.8 | 48.0 | 不变 |
| 智能排产优化 | 33.0 | 33.0 | 不变 |
| 供应商风险预警 | 20.0 | 20.0 | 不变 |

```
财务智能对账 (调整后):
  Raw = 0.20 x 5 + 0.20 x 4 + 0.40 x 2 + 0.20 x 5 = 1.0 + 0.8 + 0.8 + 1.0 = 3.60
  Normalized = 72.0 → Final = 72.0 x 1.0 = 72.0 → Tier 2
```

> **顾问建议**: 财务智能对账对频率权重敏感 (月度执行频率仅为 2)。若客户高管团队强调 "实时智能"，应提前预判此场景降级风险，在汇报中调整叙事框架，将其定位为 "运营效率快赢" 而非 "AI 战略标杆"。

---

## 示例四: L1-L2 能力热力图 | Example 4: L1-L2 Capability Heat Map

### 制造业能力分解 Manufacturing Capability Decomposition

成熟度等级 Maturity Levels:
- `[1]` 初始 Initial — 人工/临时性
- `[2]` 已管理 Managed — 部分标准化
- `[3]` 已定义 Defined — 流程标准化
- `[4]` 已度量 Measured — 量化管控
- `[5]` 持续优化 Optimizing — 持续改进+智能化

```
L1 能力域            L2 子能力             成熟度   系统支撑        差距说明
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
产品研发              需求分析              [3] ███░░  SAP PLM       -
Product Dev          设计管理              [3] ███░░  SAP PLM       -
                     试制验证              [2] ██░░░  Excel         缺乏数字化试制平台

采购管理              供应商准入            [3] ███░░  SAP MM        -
Procurement          采购执行              [4] ████░  SAP MM        -
                     供应商绩效            [1] █░░░░  Excel         无系统化评估

生产制造              生产计划 Planning     [3] ███░░  SAP PP        -
Production           排程调度 Scheduling   [2] ██░░░  MES(自研)     算法简单,人工调整多
                     执行监控 Execution    [3] ███░░  MES(自研)     -
                     过程监控 Monitoring   [2] ██░░░  MES(自研)     实时性不足
                     生产报告 Reporting    [1] █░░░░  Excel         完全手工汇总

质量管理              来料检验              [3] ███░░  SAP QM        -
Quality              过程检验              [2] ██░░░  MES           抽检,非全检
                     成品检验              [1] █░░░░  人工目视       ← 关键短板
                     质量追溯              [2] ██░░░  MES/SAP       批次级,非单件级

物流仓储              仓库管理              [3] ███░░  SAP WM        -
Logistics            配送管理              [2] ██░░░  第三方         缺乏可视化

销售服务              客户管理              [3] ███░░  Salesforce    -
Sales                销售预测              [1] █░░░░  Excel         经验主义
                     报价管理              [2] ██░░░  SAP SD        -

售后服务              投诉处理              [2] ██░░░  Salesforce    -
After-sales          备件管理              [2] ██░░░  SAP           -
                     现场服务              [1] █░░░░  纸质工单       无数字化
```

**热力图摘要**: 平均成熟度 2.1/5.0。关键薄弱环节集中在 "成品检验" (L1=1)、"生产报告" (L1=1)、"销售预测" (L1=1)。生产制造 L2 中，排程调度和过程监控是 AI 可提升的高价值区域。

---

## 示例五: 应用组合健康度象限 | Example 5: Application Portfolio Health Quadrant

```
                        技术健康度 Technical Health →
                    低 Low              中 Medium           高 High
               ┌────────────────┬────────────────┬────────────────┐
    高 High    │                │                │                │
               │   ★ 自研 MES   │                │   ★ SAP ERP    │
  业           │   Transform    │                │   Strategic    │
  务           │   (紧急改造)    │                │   (战略资产)    │
  价           ├────────────────┼────────────────┼────────────────┤
  值           │                │                │                │
  Business     │                │                │ ★ Salesforce   │
  Value        │                │                │   CRM          │
    ↑          │                │                │   Tolerate     │
               ├────────────────┼────────────────┤   (维持)       │
    低 Low     │                │                │                │
               │  ★ Excel BI   │                │                │
               │   Eliminate    │                │                │
               │   (淘汰替换)   │                │                │
               └────────────────┴────────────────┴────────────────┘
```

| 系统 System | 业务价值 | 技术健康 | 象限 Quadrant | 行动建议 Action |
|-------------|---------|---------|---------------|----------------|
| SAP ERP (2018) | 8/10 | 6/10 | Strategic 战略资产 | 持续投资, 升级至 S/4HANA |
| 自研 MES (2020) | 9/10 | 3/10 | Transform 紧急改造 | 架构重构或替换为商业 MES, 优先级最高 |
| Salesforce CRM (2019) | 5/10 | 8/10 | Tolerate 维持 | 最低限度维护, 不追加投资 |
| Excel BI | 3/10 | 2/10 | Eliminate 淘汰 | 替换为统一 BI 平台 (Power BI / Tableau) |

> **顾问洞察**: 自研 MES 是最大风险点 — 业务价值极高 (生产核心) 但技术债严重 (无 API、单点架构)。任何 AI 场景 (预测维护、智能排产) 都依赖 MES 数据通道。MES 改造应纳入数字化转型基础设施，而非单独立项。

---

## 示例六: ROI 测算 — AI 视觉质检 | Example 6: ROI Calculation — AI Visual Quality Inspection

### 6.1 成本结构 Cost Structure

| 项目 Item | Year 0 (万元) | Year 1 | Year 2 | Year 3 |
|-----------|--------------|--------|--------|--------|
| 工业相机硬件 Camera Hardware | 80 | - | - | - |
| AI 软件平台 AI Software | 60 | - | - | - |
| 系统集成 Integration | 40 | - | - | - |
| 培训 Training | 10 | - | - | - |
| 年度运维 Annual Ops | - | 15 | 15 | 15 |
| **小计 Subtotal** | **190** | **15** | **15** | **15** |

**总投资 Total Investment (3 年)**: 235 万元

### 6.2 收益结构 Benefit Structure

| 收益来源 Benefit Source | 年均收益 Annual (万元) | 计算依据 Basis |
|------------------------|----------------------|----------------|
| 缺陷降低 Defect Reduction | 150 | 退货减少 90万 + 返工减少 60万 |
| 人力节省 Headcount Savings | 60 | 3 名质检员 x 20万/年 |
| 质量溢价 Quality Premium | 100 | 高质量认证 → 单价提升 2% |
| **年度总收益 Total Annual** | **310** | |

### 6.3 NPV 与 ROI 计算 | NPV & ROI Calculation

折现率 Discount Rate: 10%

```
Year 0:  -190.00 万
Year 1:  (310 - 15) / 1.10   = 295 / 1.100 = +268.18 万
Year 2:  (310 - 15) / 1.10^2 = 295 / 1.210 = +243.80 万
Year 3:  (310 - 15) / 1.10^3 = 295 / 1.331 = +221.64 万
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
NPV (3 年) = -190.00 + 268.18 + 243.80 + 221.64 = +543.62 万元

ROI = (总收益 - 总成本) / 总成本 = (930 - 235) / 235 = 295.7%
回收期 Payback = 190 / (310 - 15) = 0.64 年 ≈ 7.7 个月
```

### 6.4 敏感性分析 | Sensitivity Analysis

| 情景 Scenario | NPV (万元) | ROI | 回收期 |
|--------------|-----------|-----|--------|
| 基准 Base Case | 543.62 | 295.7% | 7.7 月 |
| 收益 -20% Benefits -20% | 389.44 | 196.6% | 9.8 月 |
| 收益 +20% Benefits +20% | 697.81 | 394.9% | 6.4 月 |
| 成本 +20% Costs +20% | 498.15 | 229.8% | 9.3 月 |
| 成本 -20% Costs -20% | 589.08 | 386.2% | 6.2 月 |

> **顾问结论**: 即使在最悲观情景 (收益 -20%) 下，NPV 仍为正 (389 万)，回收期不超过 10 个月。项目财务可行性高度稳健。建议在 Steering Committee 汇报中以基准 + 悲观双情景呈现，增强可信度。

---

## 示例七: 叙事报告节选 | Example 7: Narrative Report Excerpt

> 以下为 StratAlign 生成的最终报告节选，展示叙事体格式 (非表格罗列)。

### 执行摘要 Executive Summary

华远精密制造正处于战略转型的关键窗口期。公司在精密制造领域的技术积淀深厚，但数字化能力严重滞后于业务需求 -- 能力成熟度评估显示，全域平均仅为 2.1 分 (满分 5.0)，成品检验、生产报告、销售预测三个子能力处于最低的 "初始级"。这一差距直接反映在经营指标上: PPM 高达 320 (行业标杆为 50 以下)，OTD 仅 89% (客户要求 98%)。

经过四维加权 AI 评分模型分析，我们识别出 5 个候选 AI 场景。评分结果揭示了一个关键发现: **财务智能对账以 82.0 分位列第一 (Tier 1)**，具备立即启动的全部条件; 而管理层最关注的 AI 视觉质检仅排第三 (43.8 分, Tier 3)，原因并非场景价值不足，而是图像数据基础设施的缺失 (数据系数仅 0.6) 构成了硬约束。

我们建议采用 **"快赢先行 + 基础并建"** 的双轨策略: 3 个月内通过财务对账 RPA 快赢建立组织信心和 AI 投资回报样板; 同步启动 6 个月的图像数据基础设施建设; 基础就绪后，AI 视觉质检的评分将跃升至 Tier 1 区间 (预估 73.0 分)，届时可全面展开部署。三年期 NPV 预计 543.62 万元，回收期 7.7 个月。

### 第三章节选: 能力差距与应用组合分析

应用组合健康度分析揭示了一个需要立即关注的风险: 自研 MES 系统虽然承载了生产制造这一最高业务价值域 (9/10)，但其技术健康度仅为 3/10 -- 无标准 API 接口、单点架构、文档缺失。这意味着任何依赖生产数据的 AI 场景 (预测维护、智能排产) 都将受制于 MES 的数据输出能力。

我们的建议是将 MES 现代化改造从 "IT 基础设施项目" 提升为 "数字化转型使能项目"，纳入 Steering Committee 直接管辖。具体路径有两个选项: (1) 渐进式改造 -- 为现有 MES 增加 API 层和数据总线，预算约 150 万元，周期 8 个月; (2) 整体替换 -- 引入商业 MES (如 Siemens Opcenter)，预算约 400 万元，周期 14 个月。鉴于华远的中期目标和预算约束，我们倾向方案 (1)，并在路线图中预留方案 (2) 作为第二阶段选项。

---

## 迷你诊断卡 (更新版) | Mini Diagnostic Card — Updated

---

**企业 Company**: 华远精密制造有限公司 | **行业 Industry**: 精密制造 (Manufacturing Playbook)
**规模 Scale**: Mid-market (2,000人) | **模式 Mode**: Accelerated | **日期 Date**: 2024-06-15

---

### 一句话诊断 | One-Line Diagnosis

> 战略清晰但数字化执行能力断层 (成熟度 2.1/5.0)。财务对账 (82.0 分) 具备立即启动条件; AI 视觉质检潜力最高但受限于数据基础设施 (系数 0.6)。MES 技术债务是全面 AI 化的首要阻碍。
>
> Clear strategy but digital execution gap (maturity 2.1/5.0). Financial reconciliation (82.0) is ready for immediate launch. AI visual inspection has the highest potential but is constrained by data infrastructure (coeff 0.6). MES technical debt is the primary blocker for AI at scale.

---

### Top 3 AI 机会 (加权模型) | Top 3 AI Opportunities (Weighted Model)

| # | 场景 Scenario | 最终得分 | Tier | 行动建议 |
|---|--------------|---------|------|---------|
| 1 | 财务智能对账 | 82.0/100 | Tier 1 立即优先 | RPA 快赢, 3 个月见效 |
| 2 | 设备预测维护 | 56.0/100 | Tier 2 战略投资 | 纳入 12 个月路线图 |
| 3 | 成品外观质检 | 43.8/100 | Tier 3 夯实基础 | 先建图像数据基础设施 |

---

### Top 3 瓶颈 | Top 3 Bottlenecks

| # | 瓶颈 Bottleneck | 影响 Impact |
|---|-----------------|-------------|
| 1 | 自研 MES 技术债 (技术健康 3/10) | 阻断生产数据链路, 制约预测维护与智能排产 |
| 2 | 图像数据未结构化 (场景系数 0.6) | 质检 AI 最高潜力场景无法启动 |
| 3 | IT 团队规模不足 (仅 12 人) | 无力并行推进多个数字化项目 |

---

### 关键假设风险 | Key Hypothesis Risk

> H-004 (70% 交付延误归因设备故障) 是因果链支点。若不成立，OTD 改善路径需重构。建议第一周优先验证。

---

### 推荐首要行动 | Recommended First Action

**双轨启动**: 财务对账 RPA (快赢, 30 万, 3 个月) + 图像数据基础设施建设 (80 万, 6 个月)
**预期效果**: 快赢 ROI 展示 + 为质检 AI (NPV 543 万) 解锁数据前置条件
**ROI 稳健性**: 即使收益下降 20%, NPV 仍为正 (389 万), 回收期 < 10 个月

---

*示例基于虚构企业，仅作演示用途 | Examples based on fictional company, for demonstration only*
*同辙 · StratAlign v1.0.0*
