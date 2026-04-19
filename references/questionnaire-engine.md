# 同辙 · StratAlign — 结构化问卷引擎
# Questionnaire Engine

> 五模块渐进式对话问卷，中文为主、英文辅助。
> Five-module progressive dialogue questionnaire. Chinese primary, English hints.

---

## 使用说明 | Usage Notes

- 每个问题标注 `[类型]` 表示期望的回答形式
- 类型说明: `[开放]` 自由文本 / `[选择]` 单选或多选 / `[量表]` 1-5 评分 / `[列表]` 列举多项 / `[数值]` 具体数字
- 对话引擎应按模块顺序逐步推进，支持跳转
- Each question is tagged with `[Type]` indicating expected answer format
- Types: `[Open]` free text / `[Choice]` single/multi select / `[Scale]` 1-5 rating / `[List]` enumerate items / `[Numeric]` specific number

---

## Module 1: 战略解码 | Strategic Decoding

> 目标: 理解企业战略全貌，提取战略主题，构建 BSC 四维目标体系。
> Goal: Understand the full strategic picture, extract themes, build BSC objectives.

### Q1.1 — 愿景 Vision
**请描述贵公司未来 3-5 年的愿景是什么？**
*What is your company's 3-5 year vision?*
`[开放 Open]` 期望 100-300 字的描述

### Q1.2 — 使命 Mission
**贵公司的核心使命是什么？为谁创造什么价值？**
*What is your core mission? For whom do you create what value?*
`[开放 Open]` 期望包含客户、价值、差异化要素

### Q1.3 — 战略主题 Strategic Themes
**当前最重要的 3-5 个战略主题是什么？请按优先级排序。**
*What are the top 3-5 strategic themes? Please rank by priority.*
`[列表 List]` 期望 3-5 项，含简要说明

### Q1.4 — 财务目标 Financial Objectives
**在财务维度，未来 3 年最关键的目标是什么？**
*What are the most critical financial objectives for the next 3 years?*
`[列表 List]` 例如: 营收增长、成本降低、利润率提升
*Hint: revenue growth, cost reduction, margin improvement*

### Q1.5 — 客户目标 Customer Objectives
**在客户维度，您希望实现哪些关键改善？**
*What key improvements do you want to achieve in the customer dimension?*
`[列表 List]` 例如: 满意度提升、新客户获取、数字渠道占比
*Hint: CSAT improvement, new customer acquisition, digital channel ratio*

### Q1.6 — 流程目标 Process Objectives
**哪些内部流程最需要优化或数字化改造？**
*Which internal processes most need optimization or digital transformation?*
`[列表 List]` 期望列出 3-5 个关键流程

### Q1.7 — 学习与成长目标 Learning & Growth Objectives
**在组织能力和人才方面，最大的差距在哪里？**
*Where are the biggest gaps in organizational capability and talent?*
`[开放 Open]` 期望涵盖: 人才、技术、文化、知识管理

### Q1.8 — 战略矛盾自检 Strategy Contradiction Self-Check
**您是否感觉到某些战略目标之间存在矛盾或资源冲突？**
*Do you sense any contradictions or resource conflicts between strategic objectives?*
`[选择 Choice]` 是/否/不确定
如果"是"，请简要说明 → `[开放 Open]`

### Q1.9 — 战略执行障碍 Strategy Execution Barriers
**过去 1-2 年，战略执行中最大的障碍是什么？**
*What was the biggest barrier to strategy execution in the past 1-2 years?*
`[开放 Open]` 期望具体事例

### Q1.10 — 数字化在战略中的定位 Role of Digitalization
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
**贵公司最核心的 5-8 个端到端业务流程是什么？**
*What are the 5-8 most critical end-to-end business processes?*
`[列表 List]` 例如: 订单到回款 (O2C)、采购到付款 (P2P)、生产计划到交付

### Q2.2 — 最大痛点 Top Pain Points
**目前业务运营中，最让您"头疼"的 3 个问题是什么？**
*What are the 3 most "painful" problems in current operations?*
`[列表 List]` 期望含: 问题描述 + 影响程度 + 发生频率

### Q2.3 — 信息断点 Information Breakpoints
**哪些环节存在"信息孤岛"或数据不通的问题？**
*Where do "information silos" or data disconnection issues exist?*
`[列表 List]` 期望指出具体部门/系统之间的断点

### Q2.4 — 人工依赖 Manual Dependencies
**哪些工作仍高度依赖人工操作，难以自动化？**
*Which tasks still heavily depend on manual operations and are hard to automate?*
`[列表 List]` 期望列出工作内容 + 原因

### Q2.5 — 响应速度 Response Speed
**业务响应速度是否满足客户/市场需求？哪些环节最慢？**
*Does business response speed meet customer/market needs? Which steps are slowest?*
`[量表 Scale]` 整体满意度 1-5 + `[列表 List]` 最慢环节

### Q2.6 — 技术债务 Technical Debt
**当前 IT 系统中，哪些是"老旧系统"亟需升级或替换？**
*Which current IT systems are "legacy systems" urgently needing upgrade or replacement?*
`[列表 List]` 系统名称 + 上线年份 + 主要问题

### Q2.7 — 组织协作障碍 Organizational Collaboration Barriers
**跨部门协作中最大的障碍是什么？**
*What is the biggest barrier in cross-department collaboration?*
`[开放 Open]` 期望涵盖: 流程、文化、工具、权责

### Q2.8 — 痛点优先级 Pain Point Priority
**如果只能解决一个问题，您会选择哪个？为什么？**
*If you could solve only one problem, which would you choose and why?*
`[开放 Open]` 期望明确选择 + 理由

---

## Module 2.5: AI 原生潜力分诊 | AI-Native Potential Triage

> 目标: 评估关键场景的 AI 化潜力，生成评分矩阵。
> Goal: Assess AI potential for key scenarios, generate scoring matrix.

### Q2.5.1 — 候选场景识别 Candidate Scenario Identification
**基于前面识别的痛点，哪些业务场景您认为最有可能通过 AI/智能化解决？**
*Based on the pain points identified above, which scenarios do you think AI could most likely solve?*
`[列表 List]` 期望 3-7 个场景

### Q2.5.2 — 规则显性度评估 Rule Explicitness Assessment
**对于每个候选场景，其业务规则的文档化程度如何？**
*For each candidate scenario, how well-documented are the business rules?*
`[量表 Scale]` 每个场景 1-5 分
- 1 = 完全依赖老师傅经验，无文档 Fully tacit knowledge, no documentation
- 3 = 有部分 SOP，但不完整 Partial SOP, incomplete
- 5 = 完整 SOP，规则已数字化 Full SOP, rules digitized

### Q2.5.3 — 数据模态评估 Data Modality Assessment
**对于每个候选场景，相关数据的数字化程度如何？**
*For each candidate scenario, how digitized is the relevant data?*
`[量表 Scale]` 每个场景 1-5 分
- 1 = 无数字数据，全靠纸质/口头 No digital data, all paper/verbal
- 3 = 有数字数据但分散在不同系统 Digital data but scattered across systems
- 5 = 结构化实时数据流 Structured real-time data streams

### Q2.5.4 — 决策频率评估 Decision Frequency Assessment
**对于每个候选场景，决策发生的频率是？**
*For each candidate scenario, how frequent are the decisions?*
`[量表 Scale]` 每个场景 1-5 分
- 1 = 年度/季度战略决策 Yearly/quarterly strategic decisions
- 3 = 每日运营决策 Daily operational decisions
- 5 = 实时/秒级决策 Real-time/per-second decisions

### Q2.5.5 — 数据基础设施状态 Data Infrastructure Status
**贵公司整体数据基础设施处于什么状态？**
*What is the overall state of your data infrastructure?*
`[选择 Choice]`
- A. 基本无统一数据管理 No unified data management → 系数 0.3
- B. 有部分数据仓库但分散 Some data warehouses but scattered → 系数 0.6
- C. 有统一数据平台且数据质量可控 Unified data platform with quality control → 系数 1.0

### Q2.5.6 — AI 团队与经验 AI Team & Experience
**贵公司是否有 AI/数据科学团队？过去是否有 AI 项目经验？**
*Does your company have an AI/data science team? Any prior AI project experience?*
`[选择 Choice]`
- A. 无团队无经验 No team, no experience
- B. 有数据团队但无 AI 项目经验 Data team exists but no AI project experience
- C. 有团队且有成功 AI 项目 Team exists with successful AI projects

### Q2.5.7 — AI 预期管理 AI Expectation Management
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
**请列出贵公司当前使用的主要 IT 系统。**
*Please list the major IT systems your company currently uses.*
`[列表 List]` 期望含: 系统名称、类型 (ERP/CRM/MES/...)、上线年份、供应商

### Q3.2 — 系统集成现状 System Integration Status
**这些系统之间的集成程度如何？是否有统一的集成平台？**
*How well integrated are these systems? Is there a unified integration platform?*
`[选择 Choice]`
- A. 基本独立运行 Mostly independent
- B. 部分点对点集成 Some point-to-point integration
- C. 有 ESB/iPaaS 中间件 ESB/iPaaS middleware exists
- D. 有统一数据中台 Unified data middle platform

### Q3.3 — 系统满意度 System Satisfaction
**对现有 IT 系统的整体满意度如何？最不满意的系统是哪个？**
*How satisfied are you with current IT systems overall? Which system are you least satisfied with?*
`[量表 Scale]` 整体满意度 1-5 + `[开放 Open]` 最不满意的系统及原因

### Q3.4 — 云化程度 Cloud Adoption Level
**贵公司的 IT 系统云化程度如何？**
*What is the cloud adoption level of your IT systems?*
`[选择 Choice]`
- A. 全部本地部署 All on-premises
- B. 混合云 (部分上云) Hybrid cloud
- C. 云优先 Cloud-first
- D. 全面云原生 Fully cloud-native

### Q3.5 — 数据治理成熟度 Data Governance Maturity
**贵公司是否有数据治理体系？数据质量如何？**
*Does your company have a data governance system? How is data quality?*
`[量表 Scale]` 数据治理成熟度 1-5
- 1 = 无数据治理 No data governance
- 3 = 有基本规范但执行不一致 Basic standards but inconsistent execution
- 5 = 完善的数据治理体系 Comprehensive data governance system

### Q3.6 — IT 团队能力 IT Team Capability
**IT 团队的规模和核心能力如何？最缺什么技能？**
*What are the IT team's size and core capabilities? What skills are most lacking?*
`[开放 Open]` 期望含: 团队规模、核心能力、技能缺口

### Q3.7 — IT 预算结构 IT Budget Structure
**当前 IT 预算中，"维持运营"与"创新投入"的比例大约是？**
*What is the approximate ratio of "keep-the-lights-on" vs "innovation" in IT budget?*
`[选择 Choice]`
- A. 90:10 (几乎全部用于维护)
- B. 70:30 (大部分用于维护)
- C. 50:50 (各半)
- D. 30:70 (大部分用于创新)

---

## Module 4: 投资组合 | Investment Portfolio

> 目标: 形成数字化投资组合，排序优先级，生成路线图。
> Goal: Form digital investment portfolio, prioritize, generate roadmap.

### Q4.1 — 总体预算 Total Budget
**未来 12-18 个月，可用于数字化转型的总预算大约是多少？**
*What is the approximate total budget for digital transformation in the next 12-18 months?*
`[数值 Numeric]` 单位: 万元 (10K CNY) 或 等值货币

### Q4.2 — 预算分配倾向 Budget Allocation Preference
**您倾向于如何分配预算？**
*How do you prefer to allocate the budget?*
`[选择 Choice]`
- A. 集中投入 1-2 个大项目 Concentrate on 1-2 large projects
- B. 分散投入多个小项目 Spread across multiple small projects
- C. 混合: 1 个核心 + 若干快赢 Mixed: 1 core + several quick wins

### Q4.3 — 风险偏好 Risk Appetite
**贵公司对数字化项目的风险容忍度如何？**
*What is your company's risk tolerance for digital projects?*
`[选择 Choice]`
- A. 保守 Conservative — 只做成熟技术、确定性高的项目
- B. 中等 Moderate — 可接受一定创新风险
- C. 激进 Aggressive — 愿意尝试前沿技术
*Hint: Conservative / Moderate / Aggressive*

### Q4.4 — 期望见效时间 Expected Time to Value
**您期望多长时间看到第一个数字化项目的成果？**
*How soon do you expect to see results from the first digital project?*
`[选择 Choice]`
- A. 3 个月内 Within 3 months
- B. 6 个月内 Within 6 months
- C. 12 个月内 Within 12 months

### Q4.5 — 外部资源 External Resources
**是否考虑引入外部合作伙伴 (咨询公司、SI、ISV)？**
*Are you considering bringing in external partners (consultants, SI, ISV)?*
`[选择 Choice]`
- A. 全部内部自研 All in-house
- B. 核心自研 + 部分外包 Core in-house + partial outsourcing
- C. 以外部合作为主 Primarily external partnerships

### Q4.6 — 成功标准 Success Criteria
**您如何定义这次数字化转型"成功"？最关键的 1-2 个指标是什么？**
*How do you define "success" for this digital transformation? What are the 1-2 most critical metrics?*
`[开放 Open]` 期望具体、可量化的成功标准

---

## 问卷引擎控制指令 | Engine Control Commands

| 指令 Command | 说明 Description |
|---|---|
| `下一步` / `next` | 进入下一个问题 |
| `跳过` / `skip` | 跳过当前问题 |
| `返回` / `back` | 回到上一个问题 |
| `跳转 M2` / `goto M2` | 跳转到指定模块 |
| `总结` / `summary` | 显示当前已收集的信息摘要 |
| `生成报告` / `report` | 基于已有信息生成报告 |
| `迷你卡` / `mini` | 生成迷你诊断卡 |

---

*问卷引擎 v0.5.0-beta | Questionnaire Engine v0.5.0-beta*
