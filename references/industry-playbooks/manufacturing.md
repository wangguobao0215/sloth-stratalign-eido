# 制造业行业剧本 | Manufacturing Industry Playbook

> 适用于离散制造、流程制造、汽车零部件、电子制造、装备制造等制造业细分领域。
> Applicable to discrete manufacturing, process manufacturing, automotive parts, electronics manufacturing, and equipment manufacturing sub-sectors.

---

## 一、行业特征 | Industry Profile

### 核心特征 | Key Characteristics

| 维度 | 特征描述 |
|------|----------|
| 资产结构 | 重资产运营，固定资产占比高（通常 40-70%），设备投资回收周期长 |
| 流程驱动 | 生产过程高度依赖工艺路线与标准作业程序（SOP），变更管理严格 |
| 质量关键 | 质量成本占营收 5-25%，缺陷追溯要求高，行业认证门槛严格（ISO 9001 / IATF 16949 / GMP） |
| 供应链复杂度 | 多级供应商网络，BOM 层级深（5-15 层），交期协同难度大 |
| 劳动力密集 | 一线操作工占比高，技能传承依赖师徒制，人员流动率 15-30%/年 |
| 能耗敏感 | 能源成本占运营成本 8-20%，碳排放合规压力持续增大 |

### 企业规模分级 | Company Size Tiers

| 规模 | 员工数 | 年营收（亿元） | 典型特征 |
|------|--------|----------------|----------|
| 中小企业 SME | 50-500 | 0.5-5 | 信息化基础薄弱，Excel 驱动，老板决策制 |
| 中型企业 Mid-market | 500-5,000 | 5-50 | 已部署 ERP，部分模块上线，数据孤岛严重 |
| 大型企业 Enterprise | 5,000+ | 50+ | 多工厂协同，集团化管控需求，正在推进工业 4.0 |

### 数字化成熟度谱系 | Digital Maturity Spectrum

1. **手工作坊阶段**（Level 1）：纸质工单、人工排产、经验式质检
2. **信息化起步**（Level 2）：基础 ERP 上线、部分流程电子化
3. **局部数字化**（Level 3）：MES 覆盖关键产线、数据采集初步建立
4. **互联互通**（Level 4）：OT-IT 融合、实时数据驱动决策
5. **智能制造领先者**（Level 5）：数字孪生、AI 驱动自适应生产

---

## 二、典型战略主题 | Strategic Themes

### ST-1: 智能制造升级 | Smart Manufacturing (Industry 4.0)

- **描述**：通过 IoT、数字孪生、AI 等技术实现生产过程的可视化、可预测、可自优化，从经验驱动转向数据驱动。
- **典型优先级**：高（High）
- **时间跨度**：中长期（Horizon 2-3），12-36 个月
- **BSC 对齐**：内部流程（设备综合效率 OEE 提升 10-20%）、财务（单位制造成本降低 8-15%）

### ST-2: 供应链韧性与可视化 | Supply Chain Resilience & Visibility

- **描述**：构建端到端供应链可视化平台，提升多源采购能力、库存缓冲策略、供应商风险预警，应对地缘政治与黑天鹅事件。
- **典型优先级**：高（High）
- **时间跨度**：中期（Horizon 2），6-18 个月
- **BSC 对齐**：客户（准时交付率 ≥95%）、内部流程（供应中断恢复时间缩短 50%）

### ST-3: 质量卓越 | Quality Excellence (Zero Defect)

- **描述**：构建全链路质量管理体系，从来料检验到出厂检测全流程数字化，利用 SPC/AI 实现预防性质量管控，推动零缺陷目标。
- **典型优先级**：高（High）
- **时间跨度**：中期（Horizon 1-2），6-18 个月
- **BSC 对齐**：客户（客户投诉率降低 40%）、财务（质量成本降低 20-30%）

### ST-4: 成本优化与精益运营 | Cost Optimization & Lean Operations

- **描述**：在精益管理基础上，通过数字化手段消除七大浪费，优化产能利用率、人效比和能耗水平。
- **典型优先级**：中高（Medium-High）
- **时间跨度**：短中期（Horizon 1-2），3-12 个月
- **BSC 对齐**：财务（毛利率提升 2-5pp）、内部流程（人均产值提升 15%）

### ST-5: 客户体验与服务化转型 | Customer Experience & Servitization

- **描述**：从"卖产品"向"卖产品+服务"转型，通过远程运维、预测性服务、按用量付费等模式提升客户黏性和经常性收入占比。
- **典型优先级**：中（Medium）
- **时间跨度**：中长期（Horizon 2-3），12-36 个月
- **BSC 对齐**：客户（NPS 提升 15 分）、财务（服务收入占比从 <10% 提升至 20-30%）

---

## 三、痛点库 | Pain Point Library

| # | 痛点 | 英文 | 严重度 | 频率 | 典型表现 |
|---|------|------|--------|------|----------|
| PP-1 | 生产排程复杂度高 | Production scheduling complexity | H | 高 | 多品种小批量导致排程反复调整，APS 系统利用率低，插单率 >30% |
| PP-2 | 质量缺陷率居高不下 | Quality defect rates (PPM) | H | 高 | PPM 值 >500，客户退货增加，8D 报告处理周期长 |
| PP-3 | 设备非计划停机 | Unplanned equipment downtime | H | 中高 | OEE <65%，被动维修占比 >60%，备件管理混乱 |
| PP-4 | 库存与生产不匹配 | Inventory-production mismatch | H | 高 | 原材料呆滞库存高、关键物料频繁缺料，库存周转天数 >90 |
| PP-5 | 供应商交付不可靠 | Supplier delivery unreliability | M | 中高 | 准时交付率 <85%，到货质量波动大，二次采购频繁 |
| PP-6 | 车间与管理层信息断层 | Information silos: shop floor vs. management | H | 高 | 生产进度靠人工汇报，数据延迟 4-24 小时，决策滞后 |
| PP-7 | 人工质检瓶颈 | Manual quality inspection bottleneck | M | 中 | 质检人员占一线 8-15%，检验速度跟不上产线节拍，漏检率高 |
| PP-8 | 能源与资源浪费 | Energy/resource waste | M | 中 | 能耗异常无预警，单位产品能耗高于行业标杆 15-30% |
| PP-9 | 技术工人短缺 | Skilled labor shortage | H | 高 | 关键岗位招聘周期 >3 个月，新人培训周期长，知识沉淀不足 |
| PP-10 | 新产品导入周期长 | Long new product introduction (NPI) cycle | M | 中 | NPI 周期 >12 个月，工程变更频繁，试产转量产良率爬坡慢 |

---

## 四、IT 基准模板 | IT Baseline Template

| 系统 | 类型 | 典型厂商 | 覆盖范围 | 成熟度参考 |
|------|------|----------|----------|------------|
| ERP | 企业资源计划 | SAP S/4HANA, Oracle EBS, 用友 U9, 金蝶云星空 | 财务、采购、库存、生产订单 | Level 2-4 |
| MES | 制造执行系统 | 西门子 Opcenter, 达索 DELMIA, 摩尔元数, 盘古信息 | 生产执行、工单追踪、报工 | Level 3-4 |
| WMS | 仓储管理系统 | 富勒 FLUX, Manhattan, 唯智 | 入库/出库、库位管理、拣配 | Level 2-3 |
| QMS | 质量管理系统 | ETQ, MasterControl, 质慧, 海岸鸿蒙 | 来料检验、过程检验、不合格品处理 | Level 2-3 |
| PLM | 产品生命周期管理 | PTC Windchill, 西门子 Teamcenter, CAXA | BOM 管理、工程变更、文档管理 | Level 3-4 |
| SCADA | 数据采集与监控 | Ignition, GE iFIX, 力控, 亚控 | 设备信号采集、产线监控、报警 | Level 3-5 |
| CRM | 客户关系管理 | Salesforce, 纷享销客, 销售易 | 客户管理、商机追踪、售后服务 | Level 1-3 |
| BI | 商业智能 | Power BI, 帆软 FineBI, Tableau | 经营仪表盘、生产报表、分析 | Level 2-4 |

---

## 五、L1-L2 能力地图 | Capability Map

### L1-1: 产品研发 | Product Development
- L2-1.1: 市场需求分析与产品规划
- L2-1.2: 产品设计与仿真验证
- L2-1.3: 工艺规划与工装设计
- L2-1.4: 试产验证与量产导入（NPI）
- L2-1.5: 工程变更管理（ECN/ECO）

### L1-2: 采购与供应商管理 | Procurement
- L2-2.1: 供应商寻源与准入评估
- L2-2.2: 采购计划与订单管理
- L2-2.3: 供应商绩效评价与协同
- L2-2.4: 战略采购与成本分析

### L1-3: 生产制造 | Production
- L2-3.1: 生产计划与排程（APS）
- L2-3.2: 车间执行与报工
- L2-3.3: 设备管理与维护（TPM）
- L2-3.4: 能源管理与环境监控
- L2-3.5: 安全生产管理（EHS）

### L1-4: 质量管理 | Quality
- L2-4.1: 来料检验（IQC）
- L2-4.2: 过程质量控制（IPQC / SPC）
- L2-4.3: 成品检验（OQC）
- L2-4.4: 不合格品处理与纠正预防（CAPA）
- L2-4.5: 质量体系与审计管理

### L1-5: 仓储物流 | Logistics
- L2-5.1: 原材料入库与管理
- L2-5.2: 在制品（WIP）周转管理
- L2-5.3: 成品仓储与发运
- L2-5.4: 物流配送与运输管理

### L1-6: 销售与市场 | Sales & Marketing
- L2-6.1: 客户管理与商机追踪
- L2-6.2: 报价与合同管理
- L2-6.3: 订单承诺与交期管理（ATP/CTP）
- L2-6.4: 市场分析与渠道管理

### L1-7: 售后服务 | After-sales Service
- L2-7.1: 客户投诉与工单管理
- L2-7.2: 备品备件管理
- L2-7.3: 现场服务与远程运维
- L2-7.4: 质量追溯与召回管理

### L1-8: 企业管理 | Corporate Functions
- L2-8.1: 财务与成本核算
- L2-8.2: 人力资源管理
- L2-8.3: IT 基础设施与信息安全
- L2-8.4: 合规与内控管理

---

## 六、AI 机会目录 | AI Opportunity Catalog

> 4D 加权评分说明：Rule（规则明确度 1-5）、Data（数据就绪度 1-5）、Freq（发生频率 1-5）、Complexity（人工复杂度 1-5）
> 综合分 = (Rule + Data + Freq + Complexity) / 4，分值越高越适合 AI 介入

| # | 场景名称 | 英文 | Rule | Data | Freq | Complexity | 综合分 | 说明 |
|---|----------|------|------|------|------|------------|--------|------|
| AI-1 | 视觉质检 | Visual quality inspection | 4 | 3 | 5 | 3 | 3.75 | 利用机器视觉替代人工外观检测，覆盖表面缺陷、尺寸偏差、装配错误等场景。投资回报快，通常 6-12 个月回本。 |
| AI-2 | 预测性维护 | Predictive maintenance | 3 | 4 | 4 | 3 | 3.50 | 基于设备振动/温度/电流数据预测故障，将被动维修转为计划性维护，减少非计划停机 30-50%。 |
| AI-3 | 智能排产 | Intelligent scheduling | 3 | 3 | 3 | 2 | 2.75 | 利用 AI 优化多约束排程问题（设备、物料、人员、交期），提升产能利用率 10-20%。落地难度较高，需要可靠数据基础。 |
| AI-4 | 需求预测 | Demand forecasting | 3 | 4 | 3 | 4 | 3.50 | 结合历史销量、市场趋势、客户订单管道进行销量预测，降低库存持有成本 15-25%。 |
| AI-5 | 财务对账 RPA | Financial reconciliation RPA | 5 | 4 | 2 | 5 | 4.00 | 自动完成应收/应付对账、发票匹配、三单匹配，减少人工操作 70-90%。规则明确、收益确定，是 AI 快速见效的典型场景。 |
| AI-6 | 供应商风险预警 | Supplier risk early warning | 2 | 2 | 2 | 4 | 2.50 | 通过供应商财务数据、舆情、交付历史等多源数据构建风险评估模型。数据获取是主要挑战。 |
| AI-7 | 能源优化 | Energy optimization | 4 | 3 | 4 | 3 | 3.50 | 基于产线负荷与环境参数动态调节能耗策略，典型节能 8-15%。适合高能耗行业（如钢铁、化工、建材）。 |

---

## 七、BSC 基准指标 | BSC Benchmarks

### 财务视角 | Financial Perspective

| 指标 | 英文 | 行业基准 | 优秀标杆 | 数据来源 |
|------|------|----------|----------|----------|
| 营收增长率 | Revenue growth rate | 5-10% | >15% | 年报 / 财务系统 |
| 毛利率 | Gross margin | 20-30% | >35% | 财务系统 |
| 单位制造成本降低 | Unit cost reduction | 3-5% YoY | >8% YoY | 成本核算系统 |
| 库存周转率 | Inventory turnover | 4-6x | >8x | ERP |

### 客户视角 | Customer Perspective

| 指标 | 英文 | 行业基准 | 优秀标杆 | 数据来源 |
|------|------|----------|----------|----------|
| 准时交付率 | On-time delivery rate (OTD) | 85-92% | >97% | ERP / CRM |
| 客户投诉率 | Customer complaint rate | <2% | <0.5% | QMS / CRM |
| 客户满意度 | Customer satisfaction (CSAT) | 75-85 | >90 | 调研 |
| NPS | Net Promoter Score | 20-35 | >50 | 调研 |

### 内部流程视角 | Internal Process Perspective

| 指标 | 英文 | 行业基准 | 优秀标杆 | 数据来源 |
|------|------|----------|----------|----------|
| OEE | Overall Equipment Effectiveness | 60-75% | >85% | MES / SCADA |
| 一次合格率 | First Pass Yield (FPY) | 90-95% | >99% | QMS |
| 生产周期时间 | Manufacturing cycle time | 行业相关 | 缩短 20-40% | MES |
| 能耗单耗 | Energy per unit output | 行业相关 | 低于标杆 15% | 能管系统 |

### 学习与成长视角 | Learning & Growth Perspective

| 指标 | 英文 | 行业基准 | 优秀标杆 | 数据来源 |
|------|------|----------|----------|----------|
| 员工培训时长 | Training hours per employee | 40h/年 | >80h/年 | HR 系统 |
| 数字化技能覆盖率 | Digital skill coverage | 30-50% | >70% | 评估 |
| 改善提案数 | Kaizen suggestions per capita | 2-4/年 | >8/年 | 精益管理系统 |
| 关键岗位离职率 | Key position turnover rate | <15% | <8% | HR 系统 |

---

## 八、问卷预填默认值 | Questionnaire Pre-fill Defaults

> 用于加速模式（Accelerated Mode）和专家模式（Expert Mode）的预填参考值。

| 问题领域 | 预填值 | 说明 |
|----------|--------|------|
| 企业战略类型 | 成本领先 + 差异化并重 | 制造业多采用混合战略 |
| 首要数字化目标 | 提升运营效率 | 降本增效是制造业最常见的数字化驱动力 |
| 年度 IT 预算占营收比 | 1.5-3% | 制造业 IT 投入相对保守 |
| 最大痛点 TOP3 | PP-1（排程）、PP-3（停机）、PP-6（信息断层） | 基于行业调研的高频痛点 |
| 数字化成熟度自评 | Level 2（信息化起步） | 国内制造业中位数水平 |
| 优先投资方向 | MES + 数据采集 | 打通车间数据是制造业数字化的第一步 |
| 组织变革准备度 | 中等 | 一线变革阻力较大，需要自上而下推动 |
| 期望见效周期 | 6-12 个月 | 制造业客户对 ROI 敏感，偏好快速见效 |

---

## 九、顾问贴士 | Consultant Tips

1. **先走车间，再看系统**：制造业项目启动时务必安排现场走访（Gemba Walk），亲眼看到实际作业流程比任何 PPT 都有价值。很多"已上线"的系统实际使用率不到 30%。

2. **OT 与 IT 两个世界**：制造业存在 OT（运营技术）和 IT（信息技术）两个技术栈，组织上往往也分属不同部门。数字化转型必须双线并进，协调好两方负责人的利益和关切。

3. **数据质量是最大坑**：制造企业的数据问题往往比预期严重。BOM 不准确、工时数据靠手填、设备数据采集覆盖率低。务必在方案中预留 20-30% 的工作量用于数据治理。

4. **精益是数字化的前提**：不要在混乱的流程上做数字化。如果企业连 5S 都没做好，建议先做精益基础建设，再推数字化工具。否则是"把混乱数字化"。

5. **找对 Champion 很关键**：制造业项目的成败往往取决于是否有一位既懂业务又有推动力的内部 Champion（通常是生产副总或 CIO）。项目前期要识别并绑定这个关键人物。

6. **分步实施，小步快跑**：制造业客户对风险敏感，建议采用"灯塔产线"策略——先在一条产线上试点验证，取得可量化的成果后再横向推广。避免一次性全厂铺开。

7. **注意合规与安全红线**：汽车行业需关注 IATF 16949 与功能安全（ISO 26262），医药行业需关注 GMP/FDA 合规，食品行业需关注 HACCP。数字化方案必须兼容行业合规要求，不能为了效率牺牲合规。

---

*本剧本基于制造业通用场景编写，使用前请根据客户具体细分行业进行调整。*
*This playbook is written for general manufacturing scenarios. Please adjust based on the client's specific sub-sector before use.*
