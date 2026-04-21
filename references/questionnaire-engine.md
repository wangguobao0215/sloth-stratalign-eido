# 同辙 · StratAlign — 结构化问卷引擎
# Questionnaire Engine

> 六模块渐进式对话问卷，中文为主、英文辅助。支持行业预填、顾问模式切换与数据完整性校验。
> Six-module progressive dialogue questionnaire. Chinese primary, English hints. Supports industry pre-fill, consultant mode switching, and data completeness validation.

---

## 使用说明 | Usage Notes

### 问题类型 | Question Types

- 每个问题标注 `[类型]` 表示期望的回答形式
- 类型说明: `[开放]` 自由文本 / `[选择]` 单选或多选 / `[量表]` 1-5 评分 / `[列表]` 列举多项 / `[数值]` 具体数字
- Each question is tagged with `[Type]` indicating expected answer format
- Types: `[Open]` free text / `[Choice]` single/multi select / `[Scale]` 1-5 rating / `[List]` enumerate items / `[Numeric]` specific number

### 顾问模式标签 | Consultant Mode Tags

每个问题标注模式标签，决定该问题在不同模式下是否提问:

| 标签 Tag | 含义 Meaning | 完整发现 Full | 加速 Accelerated | 专家 Expert |
|---|---|---|---|---|
| `[必答]` | 必须回答 Required | ✅ | ✅ | ✅ |
| `[建议]` | 建议回答 Recommended | ✅ | ✅ | ⏭ 跳过 |
| `[选填]` | 可选回答 Optional | ✅ | ⏭ 跳过 | ⏭ 跳过 |

- **完整发现 Full Discovery**: 提问所有问题（必答 + 建议 + 选填）
- **加速模式 Accelerated**: 提问 必答 + 建议，跳过选填；行业预填值自动加载，顾问确认/修改
- **专家模式 Expert**: 仅提问必答；其余由行业预填值或顾问导入数据填充，引擎校验完整性

### 行业预填 | Industry Pre-fill

当选定行业后，引擎自动加载行业剧本 (`references/industry-playbooks/`)，为适用问题提供预填建议，以 `💡 行业默认 Industry Default:` 标注。在加速/专家模式下，预填值作为默认答案呈现，顾问可直接确认或修改。

---

## Module 0: 行业检测与顾问配置 | Industry Detection & Consultant Setup

> 目标: 快速确定行业背景、企业规模与顾问工作模式，加载行业剧本，减少冗余提问。
> Goal: Quickly determine industry context, company size, and consultant working mode. Load industry playbook and reduce redundant questioning.

### Q0.1 — 行业选择 Industry Selection
`[必答]`
**贵公司所属行业是？**
*What industry does the company operate in?*
`[选择 Choice]`
- A. 制造业 Manufacturing
- B. 零售与消费 Retail & Consumer
- C. 金融服务 Financial Services
- D. 医疗健康 Healthcare
- E. 专业服务 Professional Services
- F. 科技与互联网 Technology & Internet
- G. 其他 Other → 请注明 (please specify) `[开放 Open]`

> 选择后自动加载对应行业剧本: `references/industry-playbooks/{industry-key}.md`
> Upon selection, auto-load industry playbook: `references/industry-playbooks/{industry-key}.md`
> 预填内容包括: BSC 典型目标、常见痛点、L1-L2 能力地图、AI 场景默认值
> Pre-fill includes: typical BSC targets, common pain points, L1-L2 capability map, AI scenario defaults

### Q0.2 — 企业规模 Company Size
`[必答]`
**贵公司的员工人数大约在哪个范围？**
*What is the approximate employee count of the company?*
`[选择 Choice]`
- A. 中小企业 SME — <500 人
- B. 中型企业 Mid-market — 500-5,000 人
- C. 大型企业 Enterprise — 5,000-20,000 人
- D. 超大型企业 Large Enterprise — 20,000+ 人

### Q0.3 — 顾问模式 Consultant Mode
`[必答]`
**请选择本次咨询的工作模式:**
*Please select the working mode for this engagement:*
`[选择 Choice]`
- A. 完整发现 Full Discovery — 全部问题，适合首次接触的新客户。所有模块全部展开，引擎逐题引导。
  *All questions, for first engagement with new client. All modules fully expanded, engine guides question by question.*
- B. 加速模式 Accelerated — 行业剧本预填，顾问确认/调整，约减少 50% 提问量。适合已有初步了解的客户。
  *Pre-filled from industry playbook, consultant confirms/adjusts, ~50% fewer questions. For clients with preliminary understanding.*
- C. 专家模式 Expert — 最少提问，顾问提供预组装数据，引擎校验完整性。适合资深顾问已有完整客户资料。
  *Minimal questions, consultant provides pre-assembled data, engine validates completeness. For senior consultants with complete client materials.*

### Q0.4 — 客户资料导入 Client Materials Import
`[建议]`
**是否有现成的客户资料可供导入？（战略报告、汇报 PPT、年报、IT 架构文档等）**
*Do you have existing client materials available for import? (strategy reports, presentations, annual reports, IT architecture docs, etc.)*
`[选择 Choice]`
- A. 是，我将上传文件 Yes, I will upload files → 使用 `数据导入` / `import data` 指令上传
- B. 否，从零开始 No, starting from scratch
- C. 部分有，稍后补充 Partially available, will supplement later

> **引擎行为 Engine Behavior:**
> - 选择 A → 引擎解析上传文件，提取关键信息预填后续问题
> - 选择 B → 按所选模式正常推进
> - 选择 C → 正常推进，允许中途随时通过 `数据导入` 指令补充

---

## Module 1: 战略解码 | Strategic Decoding

> 目标: 理解企业战略全貌，提取战略主题，构建 BSC 四维目标体系。
> Goal: Understand the full strategic picture, extract themes, build BSC objectives.

### Q1.1 — 愿景 Vision
`[必答]`
**请描述贵公司未来 3-5 年的愿景是什么？**
*What is your company's 3-5 year vision?*
`[开放 Open]` 期望 100-300 字的描述
💡 行业默认 Industry Default: 根据行业剧本自动提示典型愿景关键词
*(Manufacturing: 智能制造领先、全球化布局 / Retail: 全渠道体验、数据驱动增长 / Financial Services: 数字金融生态、普惠金融)*

### Q1.2 — 使命 Mission
`[建议]`
**贵公司的核心使命是什么？为谁创造什么价值？**
*What is your core mission? For whom do you create what value?*
`[开放 Open]` 期望包含客户、价值、差异化要素

### Q1.3 — 战略主题 Strategic Themes
`[必答]`
**当前最重要的 3-5 个战略主题是什么？请按优先级排序。**
*What are the top 3-5 strategic themes? Please rank by priority.*
`[列表 List]` 期望 3-5 项，含简要说明
💡 行业默认 Industry Default:
- 制造业 Manufacturing: 智能制造升级、供应链韧性、绿色低碳、国际化拓展、产品创新
- 零售 Retail: 全渠道融合、会员数字化、供应链优化、私域运营、新品类拓展
- 金融 Financial Services: 数字化转型、风控智能化、客户体验升级、合规科技、生态平台
- 医疗 Healthcare: 精准医疗、数字化运营、患者体验、合规与安全、AI 辅助诊疗

### Q1.4 — 财务目标 Financial Objectives
`[必答]`
**在财务维度，未来 3 年最关键的目标是什么？**
*What are the most critical financial objectives for the next 3 years?*
`[列表 List]` 例如: 营收增长、成本降低、利润率提升
*Hint: revenue growth, cost reduction, margin improvement*
💡 行业默认 Industry Default:
- 制造业 Manufacturing: 毛利率提升、运营成本降低、数字化营收占比增长
- 零售 Retail: GMV 增长、坪效提升、库存周转率改善、线上占比提升
- 金融 Financial Services: 资产质量优化、非息收入占比提升、运营成本率降低
- 医疗 Healthcare: 人均产值提升、耗材成本控制、商保与自费收入增长

### Q1.5 — 客户目标 Customer Objectives
`[必答]`
**在客户维度，您希望实现哪些关键改善？**
*What key improvements do you want to achieve in the customer dimension?*
`[列表 List]` 例如: 满意度提升、新客户获取、数字渠道占比
*Hint: CSAT improvement, new customer acquisition, digital channel ratio*
💡 行业默认 Industry Default:
- 制造业 Manufacturing: 交付准时率提升、客户投诉率降低、大客户留存率
- 零售 Retail: 复购率提升、NPS 改善、全渠道体验一致性
- 金融 Financial Services: 客户满意度(CSAT)提升、数字渠道活跃度、交叉销售率
- 医疗 Healthcare: 患者满意度、等候时间缩短、随访率提升

### Q1.6 — 流程目标 Process Objectives
`[必答]`
**哪些内部流程最需要优化或数字化改造？**
*Which internal processes most need optimization or digital transformation?*
`[列表 List]` 期望列出 3-5 个关键流程
💡 行业默认 Industry Default:
- 制造业 Manufacturing: 生产排程、质量检测、供应商管理、设备维护、仓储物流
- 零售 Retail: 选品与采购、库存管理、门店运营、会员管理、营销投放
- 金融 Financial Services: 信贷审批、风控反欺诈、客户服务、合规报送、理赔处理
- 医疗 Healthcare: 门诊流程、住院管理、药品供应、医疗影像、病历质控

### Q1.7 — 学习与成长目标 Learning & Growth Objectives
`[必答]`
**在组织能力和人才方面，最大的差距在哪里？**
*Where are the biggest gaps in organizational capability and talent?*
`[开放 Open]` 期望涵盖: 人才、技术、文化、知识管理
💡 行业默认 Industry Default:
- 制造业 Manufacturing: 数字化人才短缺、工程师老龄化、数据分析能力弱
- 零售 Retail: 数据运营人才、全渠道技术能力、数字化营销人才
- 金融 Financial Services: 金融科技复合人才、AI/ML 工程师、数据治理能力
- 医疗 Healthcare: 医疗信息化人才、AI 应用人才、跨学科复合型人才

### Q1.8 — 战略矛盾自检 Strategy Contradiction Self-Check
`[建议]`
**您是否感觉到某些战略目标之间存在矛盾或资源冲突？**
*Do you sense any contradictions or resource conflicts between strategic objectives?*
`[选择 Choice]` 是/否/不确定
如果"是"，请简要说明 → `[开放 Open]`

### Q1.9 — 战略执行障碍 Strategy Execution Barriers
`[建议]`
**过去 1-2 年，战略执行中最大的障碍是什么？**
*What was the biggest barrier to strategy execution in the past 1-2 years?*
`[开放 Open]` 期望具体事例
💡 行业默认 Industry Default:
- 制造业 Manufacturing: 部门壁垒、IT 与 OT 融合困难、人才流失
- 零售 Retail: 线上线下割裂、数据孤岛、组织敏捷性不足
- 金融 Financial Services: 监管合规压力、遗留系统束缚、部门间数据不通
- 医疗 Healthcare: 信息系统孤立、医护人员抵触变革、资金投入不足

### Q1.10 — 数字化在战略中的定位 Role of Digitalization
`[建议]`
**数字化在贵公司战略中扮演什么角色？**
*What role does digitalization play in your company's strategy?*
`[选择 Choice]`
- A. 核心驱动力 Core driver — 数字化就是战略本身
- B. 重要支撑 Key enabler — 支撑战略但不是核心
- C. 效率工具 Efficiency tool — 主要用于降本增效
- D. 尚未明确 Not yet defined — 还在探索阶段

---

## Module 2: 瓶颈扫描 | Bottleneck Scan

> 目标: 识别业务流程痛点、能力差距和组织/技术债务。
> Goal: Identify process pain points, capability gaps, and organizational/technical debt.

### Q2.1 — 核心业务流程 Core Business Processes
`[必答]`
**贵公司最核心的 5-8 个端到端业务流程是什么？**
*What are the 5-8 most critical end-to-end business processes?*
`[列表 List]` 例如: 订单到回款 (O2C)、采购到付款 (P2P)、生产计划到交付
💡 行业默认 Industry Default:
- 制造业 Manufacturing: 订单到回款(O2C)、采购到付款(P2P)、生产计划到交付、新产品开发(NPD)、设备全生命周期管理、质量管理
- 零售 Retail: 商品企划到上架、全渠道订单履约、会员全生命周期管理、供应商管理、门店运营管理
- 金融 Financial Services: 客户获取到转化、信贷审批到放款、理赔处理、合规风控、资产管理
- 医疗 Healthcare: 患者就诊全流程、住院管理、药品供应链、医疗质量管理、医保结算

### Q2.2 — 最大痛点 Top Pain Points
`[必答]`
**目前业务运营中，最让您"头疼"的 3 个问题是什么？**
*What are the 3 most "painful" problems in current operations?*
`[列表 List]` 期望含: 问题描述 + 影响程度 + 发生频率
💡 行业默认 Industry Default:
- 制造业 Manufacturing: 交付延迟、质量不稳定、设备非计划停机
- 零售 Retail: 库存积压/断货、全渠道体验不一致、营销 ROI 低
- 金融 Financial Services: 风控滞后、客户流失、合规成本高
- 医疗 Healthcare: 等候时间长、信息不互通、医疗差错风险

### Q2.3 — 信息断点 Information Breakpoints
`[建议]`
**哪些环节存在"信息孤岛"或数据不通的问题？**
*Where do "information silos" or data disconnection issues exist?*
`[列表 List]` 期望指出具体部门/系统之间的断点

### Q2.4 — 人工依赖 Manual Dependencies
`[建议]`
**哪些工作仍高度依赖人工操作，难以自动化？**
*Which tasks still heavily depend on manual operations and are hard to automate?*
`[列表 List]` 期望列出工作内容 + 原因

### Q2.5 — 响应速度 Response Speed
`[建议]`
**业务响应速度是否满足客户/市场需求？哪些环节最慢？**
*Does business response speed meet customer/market needs? Which steps are slowest?*
`[量表 Scale]` 整体满意度 1-5 + `[列表 List]` 最慢环节

### Q2.6 — 技术债务 Technical Debt
`[选填]`
**当前 IT 系统中，哪些是"老旧系统"亟需升级或替换？**
*Which current IT systems are "legacy systems" urgently needing upgrade or replacement?*
`[列表 List]` 系统名称 + 上线年份 + 主要问题

### Q2.7 — 组织协作障碍 Organizational Collaboration Barriers
`[选填]`
**跨部门协作中最大的障碍是什么？**
*What is the biggest barrier in cross-department collaboration?*
`[开放 Open]` 期望涵盖: 流程、文化、工具、权责

### Q2.8 — 痛点优先级 Pain Point Priority
`[必答]`
**如果只能解决一个问题，您会选择哪个？为什么？**
*If you could solve only one problem, which would you choose and why?*
`[开放 Open]` 期望明确选择 + 理由

---

## Module 2.5: AI 原生潜力分诊 | AI-Native Potential Triage

> 目标: 评估关键场景的 AI 化潜力，评估实施复杂度与数据就绪度，生成评分矩阵。
> Goal: Assess AI potential for key scenarios, evaluate implementation complexity and data readiness, generate scoring matrix.

### Q2.5.1 — 候选场景识别 Candidate Scenario Identification
`[必答]`
**基于前面识别的痛点，哪些业务场景您认为最有可能通过 AI/智能化解决？**
*Based on the pain points identified above, which scenarios do you think AI could most likely solve?*
`[列表 List]` 期望 3-7 个场景
💡 行业默认 Industry Default:
- 制造业 Manufacturing: 预测性维护、智能质检、智能排产、供应链需求预测、工艺参数优化
- 零售 Retail: 智能选品与定价、个性化推荐、需求预测与自动补货、智能客服、营销内容生成
- 金融 Financial Services: 智能风控、智能客服、反欺诈检测、智能投研、合规文档自动审阅
- 医疗 Healthcare: AI 辅助影像诊断、智能分诊、临床决策支持、病历质控、药物相互作用预警

### Q2.5.2 — 规则显性度评估 Rule Explicitness Assessment
`[必答]`
**对于每个候选场景，其业务规则的文档化程度如何？**
*For each candidate scenario, how well-documented are the business rules?*
`[量表 Scale]` 每个场景 1-5 分
- 1 = 完全依赖老师傅经验，无文档 Fully tacit knowledge, no documentation
- 3 = 有部分 SOP，但不完整 Partial SOP, incomplete
- 5 = 完整 SOP，规则已数字化 Full SOP, rules digitized

### Q2.5.3 — 数据模态评估 Data Modality Assessment
`[必答]`
**对于每个候选场景，相关数据的数字化程度如何？**
*For each candidate scenario, how digitized is the relevant data?*
`[量表 Scale]` 每个场景 1-5 分
- 1 = 无数字数据，全靠纸质/口头 No digital data, all paper/verbal
- 3 = 有数字数据但分散在不同系统 Digital data but scattered across systems
- 5 = 结构化实时数据流 Structured real-time data streams

### Q2.5.4 — 决策频率评估 Decision Frequency Assessment
`[必答]`
**对于每个候选场景，决策发生的频率是？**
*For each candidate scenario, how frequent are the decisions?*
`[量表 Scale]` 每个场景 1-5 分
- 1 = 年度/季度战略决策 Yearly/quarterly strategic decisions
- 3 = 每日运营决策 Daily operational decisions
- 5 = 实时/秒级决策 Real-time/per-second decisions

### Q2.5.5 — 数据基础设施状态 Data Infrastructure Status
`[必答]`
**贵公司整体数据基础设施处于什么状态？**
*What is the overall state of your data infrastructure?*
`[选择 Choice]`
- A. 基本无统一数据管理 No unified data management → 系数 0.3
- B. 有部分数据仓库但分散 Some data warehouses but scattered → 系数 0.6
- C. 有统一数据平台且数据质量可控 Unified data platform with quality control → 系数 1.0

### Q2.5.6 — 实施复杂度评估 Implementation Complexity Assessment
`[必答]`
**对于每个候选 AI 场景，实施复杂度如何评估？**
*For each candidate AI scenario, how would you assess the implementation complexity?*
`[量表 Scale]` 每个场景 1-5 分
- 1 = 极度复杂：需跨多个部门/系统的深度变革，涉及组织架构调整 Extremely complex: deep cross-org change, organizational restructuring required
- 2 = 高复杂度：需显著流程重构和多系统集成 High complexity: significant process re-engineering and multi-system integration
- 3 = 中等：需一定的系统集成和流程调整 Moderate: some system integration and process adjustment needed
- 4 = 较简单：主要是配置和轻度定制 Relatively simple: mostly configuration and light customization
- 5 = 即插即用：成熟 SaaS 方案可直接部署 Plug-and-play: mature SaaS solution, direct deployment

💡 行业默认 Industry Default:
- 制造业 Manufacturing: 预测性维护(3)、智能质检(4)、智能排产(2)、需求预测(3)、工艺优化(2)
- 零售 Retail: 智能选品(3)、个性化推荐(4)、需求预测(3)、智能客服(4)、内容生成(5)
- 金融 Financial Services: 智能风控(2)、智能客服(4)、反欺诈(3)、智能投研(3)、合规审阅(3)
- 医疗 Healthcare: AI 影像(2)、智能分诊(3)、临床决策(1)、病历质控(3)、药物预警(3)

### Q2.5.7 — 场景级数据就绪度 Per-Scenario Data Readiness
`[必答]`
**对于每个候选 AI 场景，该场景所需数据的就绪程度如何？（注意：这是针对具体场景的评估，与 Q2.5.5 的整体基础设施评估互补）**
*For each candidate AI scenario, how ready is the DATA specifically needed for that scenario? (Note: this is a per-scenario assessment, complementary to the overall infrastructure assessment in Q2.5.5)*
`[量表 Scale]` 每个场景 1-5 分
- 1 = 数据不存在或完全无法获取 Data does not exist or is completely inaccessible
- 2 = 数据存在但质量差、格式不统一、需大量清洗 Data exists but poor quality, inconsistent formats, heavy cleaning needed
- 3 = 数据可获取但需整合，部分需要补采 Data accessible but needs consolidation, partial collection still needed
- 4 = 数据基本就绪，少量质量优化即可使用 Data mostly ready, minor quality optimization needed
- 5 = 高质量数据已就位，可直接用于模型训练/推理 High-quality data in place, ready for model training/inference

💡 行业默认 Industry Default:
- 制造业 Manufacturing: 预测性维护(3-传感器数据常有)、智能质检(2-视觉数据需采集)、智能排产(3)、需求预测(4-ERP数据通常可用)、工艺优化(2)
- 零售 Retail: 智能选品(4-销售数据丰富)、个性化推荐(3-行为数据需整合)、需求预测(4)、智能客服(3-历史对话需清洗)、内容生成(4)
- 金融 Financial Services: 智能风控(4-交易数据充足)、智能客服(3)、反欺诈(3-需跨渠道整合)、智能投研(4)、合规审阅(3-文档需结构化)
- 医疗 Healthcare: AI 影像(3-PACS数据有但标注少)、智能分诊(2)、临床决策(2-数据碎片化)、病历质控(3)、药物预警(4-药品数据库成熟)

### Q2.5.8 — AI 团队与经验 AI Team & Experience
`[选填]`
**贵公司是否有 AI/数据科学团队？过去是否有 AI 项目经验？**
*Does your company have an AI/data science team? Any prior AI project experience?*
`[选择 Choice]`
- A. 无团队无经验 No team, no experience
- B. 有数据团队但无 AI 项目经验 Data team exists but no AI project experience
- C. 有团队且有成功 AI 项目 Team exists with successful AI projects
💡 行业默认 Industry Default:
- 制造业 Manufacturing: 多数为 A 或 B；大型制造企业可能为 C
- 零售 Retail: 头部零售商多为 C；中小零售商多为 A
- 金融 Financial Services: 大型银行多为 C；中小金融机构多为 B
- 医疗 Healthcare: 大型三甲医院可能为 B 或 C；多数为 A

### Q2.5.9 — AI 预期管理 AI Expectation Management
`[选填]`
**您对 AI 的预期是什么？希望 AI 在多长时间内产生可见效果？**
*What are your AI expectations? How soon should AI produce visible results?*
`[选择 Choice]`
- A. 3 个月内见效 Within 3 months
- B. 6 个月内见效 Within 6 months
- C. 12 个月可接受 12 months acceptable
- D. 作为长期战略投资 As long-term strategic investment

---

## Module 3: 覆盖分析 | Coverage Analysis

> 目标: 盘点 IT 现状，建立业务→IT 能力映射，识别空白与冗余。
> Goal: Inventory IT landscape, build business→IT mapping, identify gaps & redundancies.

### Q3.1 — IT 系统清单 IT System Inventory
`[必答]`
**请列出贵公司当前使用的主要 IT 系统。**
*Please list the major IT systems your company currently uses.*
`[列表 List]` 期望含: 系统名称、类型 (ERP/CRM/MES/...)、上线年份、供应商
💡 行业默认 Industry Default:
- 制造业 Manufacturing: ERP(SAP/Oracle)、MES、PLM、WMS、SRM、QMS
- 零售 Retail: ERP、POS/mPOS、电商平台、CRM/CDP、WMS、OMS
- 金融 Financial Services: 核心银行系统、CRM、风控系统、反洗钱系统、网银/手机银行
- 医疗 Healthcare: HIS、LIS、PACS、EMR/EHR、HRP、药品管理系统

### Q3.2 — 系统集成现状 System Integration Status
`[必答]`
**这些系统之间的集成程度如何？是否有统一的集成平台？**
*How well integrated are these systems? Is there a unified integration platform?*
`[选择 Choice]`
- A. 基本独立运行 Mostly independent
- B. 部分点对点集成 Some point-to-point integration
- C. 有 ESB/iPaaS 中间件 ESB/iPaaS middleware exists
- D. 有统一数据中台 Unified data middle platform

### Q3.3 — 系统满意度 System Satisfaction
`[建议]`
**对现有 IT 系统的整体满意度如何？最不满意的系统是哪个？**
*How satisfied are you with current IT systems overall? Which system are you least satisfied with?*
`[量表 Scale]` 整体满意度 1-5 + `[开放 Open]` 最不满意的系统及原因

### Q3.4 — 云化程度 Cloud Adoption Level
`[建议]`
**贵公司的 IT 系统云化程度如何？**
*What is the cloud adoption level of your IT systems?*
`[选择 Choice]`
- A. 全部本地部署 All on-premises
- B. 混合云 (部分上云) Hybrid cloud
- C. 云优先 Cloud-first
- D. 全面云原生 Fully cloud-native

### Q3.5 — 数据治理成熟度 Data Governance Maturity
`[建议]`
**贵公司是否有数据治理体系？数据质量如何？**
*Does your company have a data governance system? How is data quality?*
`[量表 Scale]` 数据治理成熟度 1-5
- 1 = 无数据治理 No data governance
- 3 = 有基本规范但执行不一致 Basic standards but inconsistent execution
- 5 = 完善的数据治理体系 Comprehensive data governance system

### Q3.6 — IT 团队能力 IT Team Capability
`[选填]`
**IT 团队的规模和核心能力如何？最缺什么技能？**
*What are the IT team's size and core capabilities? What skills are most lacking?*
`[开放 Open]` 期望含: 团队规模、核心能力、技能缺口

### Q3.7 — IT 预算结构 IT Budget Structure
`[选填]`
**当前 IT 预算中，"维持运营"与"创新投入"的比例大约是？**
*What is the approximate ratio of "keep-the-lights-on" vs "innovation" in IT budget?*
`[选择 Choice]`
- A. 90:10 (几乎全部用于维护)
- B. 70:30 (大部分用于维护)
- C. 50:50 (各半)
- D. 30:70 (大部分用于创新)
💡 行业默认 Industry Default:
- 制造业 Manufacturing: 通常 B (70:30)，传统制造企业可能 A
- 零售 Retail: 通常 B 到 C，数字化领先零售商可能 C 到 D
- 金融 Financial Services: 通常 B (70:30)，监管合规占较大比例
- 医疗 Healthcare: 通常 A 到 B，信息化基础投入大

---

## Module 4: 投资组合 | Investment Portfolio

> 目标: 形成数字化投资组合，排序优先级，生成路线图。
> Goal: Form digital investment portfolio, prioritize, generate roadmap.

### Q4.1 — 总体预算 Total Budget
`[必答]`
**未来 12-18 个月，可用于数字化转型的总预算大约是多少？**
*What is the approximate total budget for digital transformation in the next 12-18 months?*
`[数值 Numeric]` 单位: 万元 (10K CNY) 或 等值货币

### Q4.2 — 预算分配倾向 Budget Allocation Preference
`[建议]`
**您倾向于如何分配预算？**
*How do you prefer to allocate the budget?*
`[选择 Choice]`
- A. 集中投入 1-2 个大项目 Concentrate on 1-2 large projects
- B. 分散投入多个小项目 Spread across multiple small projects
- C. 混合: 1 个核心 + 若干快赢 Mixed: 1 core + several quick wins
💡 行业默认 Industry Default:
- 制造业 Manufacturing: 通常 C — 一个核心平台(如MES/数字孪生) + 若干快赢(如RPA/BI)
- 零售 Retail: 通常 C — 一个核心(如CDP/全渠道中台) + 快赢(如智能客服/推荐)
- 金融 Financial Services: 通常 A 或 C — 核心系统升级往往是大项目
- 医疗 Healthcare: 通常 B 到 C — 分阶段推进，降低风险

### Q4.3 — 风险偏好 Risk Appetite
`[建议]`
**贵公司对数字化项目的风险容忍度如何？**
*What is your company's risk tolerance for digital projects?*
`[选择 Choice]`
- A. 保守 Conservative — 只做成熟技术、确定性高的项目
- B. 中等 Moderate — 可接受一定创新风险
- C. 激进 Aggressive — 愿意尝试前沿技术
*Hint: Conservative / Moderate / Aggressive*

### Q4.4 — 期望见效时间 Expected Time to Value
`[必答]`
**您期望多长时间看到第一个数字化项目的成果？**
*How soon do you expect to see results from the first digital project?*
`[选择 Choice]`
- A. 3 个月内 Within 3 months
- B. 6 个月内 Within 6 months
- C. 12 个月内 Within 12 months

### Q4.5 — 外部资源 External Resources
`[建议]`
**是否考虑引入外部合作伙伴 (咨询公司、SI、ISV)？**
*Are you considering bringing in external partners (consultants, SI, ISV)?*
`[选择 Choice]`
- A. 全部内部自研 All in-house
- B. 核心自研 + 部分外包 Core in-house + partial outsourcing
- C. 以外部合作为主 Primarily external partnerships

### Q4.6 — 成功标准 Success Criteria
`[建议]`
**您如何定义这次数字化转型"成功"？最关键的 1-2 个指标是什么？**
*How do you define "success" for this digital transformation? What are the 1-2 most critical metrics?*
`[开放 Open]` 期望具体、可量化的成功标准
💡 行业默认 Industry Default:
- 制造业 Manufacturing: OEE 提升 X%、交付周期缩短 X%、质量缺陷率降低
- 零售 Retail: GMV 增长 X%、库存周转提升、客户复购率提升
- 金融 Financial Services: 不良率控制在 X%、审批效率提升 X 倍、客户满意度达 X 分
- 医疗 Healthcare: 平均等候时间缩短 X 分钟、误诊率降低、患者满意度达 X%

---

## 问卷引擎控制指令 | Engine Control Commands

### 基础导航 | Basic Navigation

| 指令 Command | 说明 Description |
|---|---|
| `下一步` / `next` | 进入下一个问题 Proceed to next question |
| `跳过` / `skip` | 跳过当前问题 Skip current question |
| `返回` / `back` | 回到上一个问题 Go back to previous question |
| `跳转 M2` / `goto M2` | 跳转到指定模块 Jump to specified module |
| `总结` / `summary` | 显示当前已收集的信息摘要 Show summary of collected information |
| `生成报告` / `report` | 基于已有信息生成报告 Generate report from collected information |
| `迷你卡` / `mini` | 生成迷你诊断卡 Generate mini diagnostic card |

### 行业与模式控制 | Industry & Mode Control

| 指令 Command | 说明 Description |
|---|---|
| `行业切换` / `switch industry` | 切换行业剧本（重新加载预填值，已确认答案保留）Switch industry playbook (reload pre-fills, confirmed answers retained) |
| `模式切换` / `switch mode` | 在 完整发现/加速/专家 模式间切换（调整后续提问策略）Switch between Full/Accelerated/Expert mode (adjust subsequent questioning strategy) |
| `预填查看` / `show defaults` | 显示当前行业剧本的所有预填值 Show all pre-filled values from current industry playbook |
| `数据导入` / `import data` | 导入客户资料（战略报告、PPT、年报等），引擎解析后预填相关问题 Import client materials (strategy reports, PPT, annual reports, etc.), engine parses and pre-fills relevant questions |

### 完整性与验证 | Completeness & Validation

| 指令 Command | 说明 Description |
|---|---|
| `完整性检查` / `check completeness` | 运行数据完整性校验，显示报告就绪度评分 Run data completeness validation, show report readiness score |
| `缺失项` / `show gaps` | 显示所有未回答的必答/建议题目 Show all unanswered required/recommended questions |

---

## 数据完整性校验 | Completeness Validation

> 在生成报告前，引擎自动执行完整性校验，确保数据质量满足报告生成要求。
> Before report generation, the engine automatically runs completeness validation to ensure data quality meets report generation requirements.

### 报告就绪度评分 | Report Readiness Score

引擎计算 0-100% 的报告就绪度评分，基于以下权重:

| 模块 Module | 权重 Weight | 最低通过要求 Minimum Pass |
|---|---|---|
| Module 0: 行业检测 Industry Detection | 5% | Q0.1 + Q0.2 + Q0.3 已回答 |
| Module 1: 战略解码 Strategic Decoding | 25% | 全部 `[必答]` 已回答 (Q1.1, Q1.3-Q1.7) |
| Module 2: 瓶颈扫描 Bottleneck Scan | 20% | 全部 `[必答]` 已回答 (Q2.1, Q2.2, Q2.8) |
| Module 2.5: AI 分诊 AI Triage | 25% | 全部 `[必答]` 已回答 (Q2.5.1-Q2.5.7) |
| Module 3: 覆盖分析 Coverage Analysis | 15% | 全部 `[必答]` 已回答 (Q3.1, Q3.2) |
| Module 4: 投资组合 Investment Portfolio | 10% | 全部 `[必答]` 已回答 (Q4.1, Q4.4) |

### 就绪度等级 | Readiness Levels

| 评分 Score | 等级 Level | 行为 Behavior |
|---|---|---|
| 90-100% | 完全就绪 Fully Ready | 可生成完整报告，所有分析维度数据充分 Full report generation, all analytical dimensions well-supported |
| 70-89% | 基本就绪 Mostly Ready | 可生成报告，部分维度会标注"数据不足，建议补充" Report generation possible, some dimensions flagged as "insufficient data, supplement recommended" |
| 50-69% | 部分就绪 Partially Ready | 可生成初步报告/迷你卡，多个维度数据不足 Preliminary report/mini card possible, multiple dimensions lack data |
| <50% | 未就绪 Not Ready | 拒绝生成报告，提示必须补充的关键问题 Report generation refused, key missing questions highlighted |

### 各模块最低数据要求 | Minimum Data Requirements per Module

**Module 0 — 行业检测 Industry Detection:**
- 必须: 行业选择、企业规模、顾问模式
- 缺失影响: 无法加载行业预填，所有问题按通用模式展开

**Module 1 — 战略解码 Strategic Decoding:**
- 必须: 愿景(Q1.1)、战略主题(Q1.3)、BSC 四维目标(Q1.4-Q1.7)
- 缺失影响: 无法构建 BSC 目标体系和战略地图
- 建议补充: 战略矛盾自检(Q1.8)、执行障碍(Q1.9) — 提升战略落地分析质量

**Module 2 — 瓶颈扫描 Bottleneck Scan:**
- 必须: 核心流程(Q2.1)、最大痛点(Q2.2)、痛点优先级(Q2.8)
- 缺失影响: 无法进行瓶颈分析和优先级排序
- 建议补充: 信息断点(Q2.3)、人工依赖(Q2.4) — 提升自动化机会识别

**Module 2.5 — AI 分诊 AI Triage:**
- 必须: 候选场景(Q2.5.1)、规则显性度(Q2.5.2)、数据模态(Q2.5.3)、决策频率(Q2.5.4)、数据基础设施(Q2.5.5)、实施复杂度(Q2.5.6)、场景数据就绪度(Q2.5.7)
- 缺失影响: 无法生成 AI 潜力评分矩阵和优先级排序
- 建议补充: AI 团队(Q2.5.8) — 提升实施可行性评估准确度

**Module 3 — 覆盖分析 Coverage Analysis:**
- 必须: IT 系统清单(Q3.1)、集成现状(Q3.2)
- 缺失影响: 无法建立 IT 能力映射和空白分析
- 建议补充: 数据治理(Q3.5)、云化程度(Q3.4) — 提升技术架构评估质量

**Module 4 — 投资组合 Investment Portfolio:**
- 必须: 总体预算(Q4.1)、期望见效时间(Q4.4)
- 缺失影响: 无法生成投资组合和路线图
- 建议补充: 风险偏好(Q4.3)、成功标准(Q4.6) — 提升路线图可行性

### 缺失数据警告 | Missing Data Warnings

当顾问请求生成报告时，引擎按以下逻辑处理:

1. **计算就绪度评分** — 遍历所有问题，统计回答状态
2. **必答题缺失警告** — 若有 `[必答]` 题未回答:
   - 列出所有缺失的必答题
   - 对于加速/专家模式：检查是否有行业预填值可用作替代
   - 预填值可替代 `[建议]` 和 `[选填]`，但不能替代 `[必答]` — 必答题必须由顾问确认
3. **模块完整性提示** — 对每个模块给出单独的完整性百分比
4. **报告质量预警** — 提示哪些报告章节可能因数据不足而质量降低

```
示例输出 / Example Output:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📊 报告就绪度 Report Readiness: 78%
等级 Level: 基本就绪 Mostly Ready
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
✅ Module 0: 100% — 完整 Complete
✅ Module 1: 90%  — Q1.8 未回答 (建议)
✅ Module 2: 85%  — Q2.3, Q2.6 未回答 (建议/选填)
⚠️ Module 2.5: 70% — Q2.5.6 未回答 (必答!)
✅ Module 3: 75%  — Q3.4, Q3.6 未回答 (建议/选填)
⚠️ Module 4: 60%  — Q4.3, Q4.6 未回答 (建议)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
⚠️ 关键缺失 Critical Gaps:
   - Q2.5.6 实施复杂度评估 (必答) — 影响 AI 优先级排序
建议 Recommendation:
   - 补充 Q2.5.6 后可提升至 85%+
   - 当前可生成报告，AI 分诊章节将标注数据不足
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

*问卷引擎 v1.0.0 | Questionnaire Engine v1.0.0*
*支持行业预填、顾问模式切换与完整性校验 | Supports industry pre-fill, consultant mode switching, and completeness validation*
