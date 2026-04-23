# 深略 · StratAlign — 结构化问卷引擎
# Questionnaire Engine

> 六模块渐进式对话问卷，支持中文、中英双语、英文三种成果物语言。支持客户名称智能补全、行业自动识别、行业预填、顾问模式切换与数据完整性校验。
> Six-module progressive dialogue questionnaire. Supports Chinese, Bilingual, and English deliverable languages. Features client name auto-completion, industry auto-detection, industry pre-fill, consultant mode switching, and data completeness validation.

<!-- LANGUAGE HANDLING INSTRUCTIONS:
This file contains bilingual content (Chinese + English) for each question.
The engine MUST respect the user's language selections from SKILL.md Language Configuration:

INTERACTION LANGUAGE (how the engine talks to the user):
- CHINESE MODE: Use only the Chinese text (bold lines) for questions, options, and hints.
  Append English abbreviations/terms in parentheses only where helpful for professional clarity.
- ENGLISH MODE: Use only the English text (italic lines) for questions, options, and hints.
  Do NOT include Chinese text in the output.

DELIVERABLE LANGUAGE (how generated artifacts are formatted):
- CHINESE: Output deliverables in Chinese only.
- BILINGUAL: Output deliverables with Chinese as primary and English in parallel.
- ENGLISH: Output deliverables in English only.

- DELIVERABLE OVERRIDE: If user requests a specific language for the questionnaire output
  (via "用中文生成" / "generate in Chinese", "用英文生成" / "generate in English",
  or "用双语生成" / "generate bilingual"),
  use that language for the output file regardless of the default setting.

All question tags [必答][建议][选填] should be rendered as:
  - Chinese mode: [必答] [建议] [选填]
  - English mode: [Required] [Recommended] [Optional]

All type tags should be rendered as:
  - Chinese mode: [开放] [选择] [量表] [列表] [数值]
  - English mode: [Open] [Choice] [Scale] [List] [Numeric]
-->

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

## Module 0: 客户识别与顾问配置 | Client Recognition & Consultant Setup

> 目标: 通过客户名称智能识别企业身份和所属行业，快速确定企业规模与顾问工作模式，加载行业剧本，减少冗余提问。
> Goal: Intelligently identify client identity and industry from the client name, quickly determine company size and consultant working mode, load industry playbook, and reduce redundant questioning.

### Q0.1 — 客户名称 Client Name
`[必答]`
**请输入您此次诊断的客户名称（公司名、简称或品牌名均可）:**
*Please enter the client name for this engagement (company name, abbreviation, or brand name):*
`[开放 Open]`

> **引擎行为 Engine Behavior — 智能补全与确认 Auto-Completion & Confirmation:**
>
> ⚠️ **必须联网搜索 MUST WebSearch**: 引擎**必须使用 WebSearch** 查询企业正式名称，搜索词模板: `"{用户输入}" 工商注册 全称` 或 `"{用户输入}" 公司 官网`。**严禁仅凭训练数据猜测公司全称**。
> ⚠️ **MUST WebSearch**: The engine **MUST use WebSearch** to look up the formal registered name. Query templates: `"{input}" registered company official name` or `"{input}" company official website`. **NEVER guess the full name from training data alone**.
>
> 1. **自动补全正式名称**: 引擎根据用户输入的名称，**先执行 WebSearch**，再根据搜索结果补全为企业的正式注册名称（工商注册名/法人全称）。
>    *Auto-complete formal name*: The engine **first performs WebSearch**, then auto-completes the input to the company's official registered name based on search results.
>
> 2. **处理简称歧义**: 如果简称可能对应多家企业，引擎列出候选列表供用户确认。
>    *Handle abbreviation ambiguity*: If the abbreviation could match multiple companies, the engine presents a candidate list for user confirmation.
>
>    示例 Example:
>    ```
>    用户输入: "华为"
>    User input: "Huawei"
>
>    引擎回复 Engine response:
>    ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
>    "华为" 可能指以下企业，请确认:
>    "Huawei" could refer to the following — please confirm:
>
>      A. 华为技术有限公司 (Huawei Technologies Co., Ltd.)
>         — 全球 ICT 基础设施和智能终端提供商
>      B. 华为投资控股有限公司 (Huawei Investment & Holding Co., Ltd.)
>         — 华为集团控股母公司
>      C. 其他 Other — 请补充完整名称 Please provide the full name
>    ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
>    ```
>
> 3. **唯一匹配确认**: 如果名称匹配唯一，直接展示补全结果请用户确认。
>    *Unique match confirmation*: If the name matches uniquely, display the result and ask user to confirm.
>
>    示例 Example:
>    ```
>    用户输入: "三一重工"
>    User input: "Sany Heavy Industry"
>
>    引擎回复 Engine response:
>    已识别为: 三一重工股份有限公司 (Sany Heavy Industry Co., Ltd.)
>    Identified as: Sany Heavy Industry Co., Ltd.
>    请确认是否正确？(Y/N)
>    Please confirm — is this correct? (Y/N)
>    ```

### Q0.2 — 行业识别与确认 Industry Detection & Confirmation
`[必答]`

> **引擎行为 Engine Behavior — 自动识别:**
>
> ⚠️ **必须联网搜索 MUST WebSearch**: 引擎**必须使用 WebSearch** 搜索客户行业信息，搜索词: `"{公司全称}" 主营业务 行业分类`。结合搜索结果与公司名称特征进行行业判定。**不得仅凭公司名称中的关键词推断行业**。
> ⚠️ **MUST WebSearch**: The engine **MUST use WebSearch** to search for client industry info. Query: `"{company}" main business industry classification`. Combine search results with company name characteristics for industry determination. **Do NOT infer industry solely from keywords in the company name**.
>
> 引擎根据 Q0.1 确认的客户正式名称，**先执行 WebSearch 获取主营业务信息**，再映射到行业剧本库。
> The engine **first performs WebSearch to obtain main business info** based on the confirmed formal name from Q0.1, then maps it to the industry playbook library.
>
> **行业映射规则 Industry Mapping Rules:**
>
> | 识别结果 Detection Result | 行业剧本 Playbook | 文件 File |
> |---|---|---|
> | 制造业 (含装备制造、电子、汽车零部件等) | 制造业 Manufacturing | `manufacturing.md` |
> | 零售、快消、电商、餐饮 | 零售与消费 Retail | `retail.md` |
> | 银行、保险、证券、基金 | 金融服务 Financial Services | `financial-services.md` |
> | 医院、制药、医疗器械、健康服务 | 医疗健康 Healthcare | `healthcare.md` |
> | 咨询、律所、会计、设计、广告 | 专业服务 Professional Services | `professional-services.md` |
> | 电力、电网、油气、水务、新能源、矿业 | 能源与公用事业 Energy & Utilities | `energy-utilities.md` |
> | 货运、快递、航运、仓储、冷链、物流 | 交通运输与物流 Transportation & Logistics | `transportation-logistics.md` |
> | 房地产开发、工程建筑、物业管理 | 房地产与建筑 Real Estate & Construction | `real-estate-construction.md` |
> | 无法明确归类 | 请用户手动选择 User selects manually | — |
>
> **多业态企业处理 Multi-Business Enterprises:**
>
> 对于涉及多个业态的企业（如海尔：智慧家庭 + 工业互联网 + 大健康），引擎应：
> For enterprises with multiple business lines (e.g., Haier: Smart Home + Industrial Internet + Health), the engine should:
>
> 1. 识别主业态并推荐为默认行业
>    Identify the primary business and recommend it as the default industry
> 2. 明确提示用户该企业涉及多业态
>    Explicitly notify the user that the enterprise spans multiple business lines
> 3. 允许用户修改为其他行业
>    Allow the user to switch to a different industry
>
>    示例 Example:
>    ```
>    ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
>    🏭 行业识别 Industry Detection
>    ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
>
>    客户: 海尔智家股份有限公司
>    Client: Haier Smart Home Co., Ltd.
>
>    检测到行业: 制造业 — 家电/智能家居
>    Detected industry: Manufacturing — Home Appliances / Smart Home
>
>    提示: 海尔集团涉及多个业态:
>    Note: Haier Group spans multiple business lines:
>      • 智慧家庭 (Smart Home) — 海尔智家
>      • 工业互联网 (Industrial Internet) — 卡奥斯 COSMOPlat
>      • 大健康 (Healthcare) — 盈康一生
>
>    当前按"制造业"加载行业剧本。如需调整请选择:
>    Currently loading "Manufacturing" playbook. To change, select:
>      A. 确认制造业 Confirm Manufacturing (推荐 Recommended)
>      B. 切换行业 Switch Industry → [选择列表 Selection list]
>    ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
>    ```
>
> **手动选择回退 Manual Selection Fallback:**
>
> 如果无法自动识别行业，引擎退回手动选择：
> If the industry cannot be auto-detected, the engine falls back to manual selection:
>
> `[选择 Choice]`
> - A. 制造业 Manufacturing
> - B. 零售与消费 Retail & Consumer
> - C. 金融服务 Financial Services
> - D. 医疗健康 Healthcare
> - E. 专业服务 Professional Services
> - F. 能源与公用事业 Energy & Utilities
> - G. 交通运输与物流 Transportation & Logistics
> - H. 房地产与建筑 Real Estate & Construction
> - I. 其他 Other → 请注明 (please specify) `[开放 Open]`
>
> 选择后自动加载对应行业剧本: `references/industry-playbooks/{industry-key}.md`
> Upon selection, auto-load industry playbook: `references/industry-playbooks/{industry-key}.md`
> 预填内容包括: BSC 典型目标、常见痛点、L1-L2 能力地图、AI 场景默认值
> Pre-fill includes: typical BSC targets, common pain points, L1-L2 capability map, AI scenario defaults

### Q0.3 — 企业规模 Company Size
`[必答]`
**贵公司的员工人数大约在哪个范围？**
*What is the approximate employee count of the company?*

> **引擎行为 Engine Behavior — 自动获取优先 Auto-Detection First:**
>
> ⚠️ **必须联网搜索 MUST WebSearch**: 引擎**必须使用 WebSearch** 搜索员工规模，搜索词模板:
> - `"{公司全称}" 员工人数 2025` 或 `"{公司全称}" 年报 员工`
> - `"{公司全称}" 员工规模 招聘` 或 `"{company}" employee count headcount`
> **严禁凭训练数据编造员工人数**。搜索无结果时必须如实告知并回退手动选择。
>
> 引擎应**优先自动获取**客户的员工规模信息（通过 WebSearch 联网搜索公开数据：上市公司年报、工商信息、招聘平台企业信息等），仅在搜索无结果时才回退到手动选择。
> The engine should **prioritize auto-detection** of the client's employee count (via WebSearch for public data: annual reports, business registration, recruitment platform company profiles, etc.), and only fall back to manual selection when search yields no results.
>
> **场景 1 — 自动获取成功 Auto-Detection Succeeds:**
>
> 直接展示结果，请用户确认：
> Display the result directly and ask user to confirm:
>
> ```
> 📊 企业规模 Company Size (自动获取 Auto-detected):
>
>    员工人数: 约 1,500 人 (2024 年报数据)
>    Employees: ~1,500 (2024 annual report)
>    规模分级: 中型企业 Mid-market (500-5,000人)
>
>    请确认是否正确？(Y/N)
>    Is this correct? (Y/N)
> ```
>
> 用户确认即通过；用户否认则进入手动选择。
> User confirms to proceed; user denies to enter manual selection.
>
> **场景 2 — 自动获取失败 Auto-Detection Fails:**
>
> 退回手动选择：
> Fall back to manual selection:

`[选择 Choice]`
- A. 中小企业 SME — <500 人
- B. 中型企业 Mid-market — 500-5,000 人
- C. 大型企业 Enterprise — 5,000-20,000 人
- D. 超大型企业 Large Enterprise — 20,000+ 人

### Q0.4 — 顾问模式 Consultant Mode
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

### Q0.5 — 客户资料导入 Client Materials Import
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

> ⚠️ **强制多轮联网搜索 MANDATORY Multi-Round WebSearch**:
> 这是数据质量风险最高的问题。引擎在预填或协助回答此问题时，**必须执行 `references/intelligence-gathering.md` §2.2 定义的"IT 系统清单情报工作流"**，包括以下 5 个阶段:
>
> **行业关键词自动切换**: 当 Q0.2 确定行业后，Phase 2（招聘搜索）和 Phase 3（供应商验证）的搜索关键词**必须切换到 `intelligence-gathering.md` §8 对应行业的专属关键词库**（§8.1 制造业 / §8.2 零售业 / §8.3 金融服务 / §8.4 医疗健康 / §8.5 专业服务 / §8.6 能源公用 / §8.7 交通物流 / §8.8 房地产建筑），不再使用通用关键词。
>
> **Phase 1 — 年报/公告挖掘** (上市公司优先):
> ```
> WebSearch: "{公司全称}" 年报 信息化 OR 数字化 OR IT系统
> WebSearch: "{公司全称}" 年度报告 信息技术 投入 2024 OR 2025
> ```
> → 如找到年报相关页面，用 WebFetch 获取完整内容提取 IT 系统细节
>
> **Phase 2 — 招聘信息技术栈反推**:
> ```
> WebSearch: "{公司全称}" 招聘 SAP OR Oracle OR 用友 OR 金蝶
> WebSearch: "{公司全称}" 招聘 MES OR ERP OR PLM OR WMS OR CRM OR OA
> WebSearch: "{公司全称}" 招聘 Java OR Python OR .NET OR 运维 OR DBA
> ```
> → 从岗位要求中提取技术关键词，反推企业在用系统
>
> **Phase 3 — 供应商合作关系验证**:
> ```
> WebSearch: "{公司全称}" 签约 OR 合作 OR 中标 ERP OR MES OR CRM
> WebSearch: "{公司全称}" 数字化转型 OR 智能制造 案例 OR 合作
> WebSearch: "{供应商名}" 客户案例 "{公司全称}" (反向搜索)
> ```
> → 从供应商新闻/案例中确认系统实施信息
>
> **Phase 4 — 技术领导力与架构访谈**:
> ```
> WebSearch: "{公司全称}" CIO OR CTO OR 信息总监 访谈 OR 分享
> ```
>
> **Phase 5 — 技术指纹检测** (域名可达时):
> ```
> WebSearch: "{公司官网域名}" site:builtwith.com
> WebSearch: "{公司官网域名}" technology stack
> ```
>
> **汇总规则**: 搜索完成后按 `intelligence-gathering.md` §1.2 的置信度标准 ([C1]~[C4]) 标注每个系统。
> **未找到的系统**: 用行业默认值补充但**必须标注 [C4] 未知**，不得伪装为确认数据。
> **搜索结果为空**: 必须如实告知顾问 "联网搜索未找到该企业 IT 系统的公开信息，以下为行业默认值，请与客户确认后修正"。
> **输出格式**: 遵循 `intelligence-gathering.md` §6.2 定义的 IT 系统清单输出格式。

💡 行业默认 Industry Default (完整矩阵见 `intelligence-gathering.md` §8.x.1):
- 制造业 Manufacturing: ERP(SAP/Oracle)、MES、PLM、WMS、SRM、QMS、SCADA/DCS、APS
- 零售 Retail: ERP、POS/mPOS、电商中台、CRM/CDP、WMS、OMS、SCM、BI
- 金融 Financial Services: 核心银行系统、CRM、风控系统、AML/KYC、渠道系统、数据平台、RPA
- 医疗 Healthcare: HIS、LIS、PACS、EMR/EHR、HRP、互联网医院、CDR、药品管理系统
- 专业服务 Professional Services: PSA、CRM、ERP/财务、KM知识管理、PM项目管理、协同办公、HCM
- 能源与公用事业 Energy & Utilities: EMS/SCADA、DCS、GIS、OMS、AMI、EAM/APM、ERP、PI Historian
- 交通运输与物流 Transportation & Logistics: TMS、WMS、OMS、FMS车队管理、路径优化、Track&Trace、ERP
- 房地产与建筑 Real Estate & Construction: BIM、项目管理、成本管理、智慧工地、CRM/营销、物业PMS、BMS

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
| `客户信息` / `show client` | 显示当前客户名称、所属行业、企业规模等基本信息 Show current client name, industry, company size and other basic info |

### 完整性与验证 | Completeness & Validation

| 指令 Command | 说明 Description |
|---|---|
| `完整性检查` / `check completeness` | 运行数据完整性校验，显示报告就绪度评分 Run data completeness validation, show report readiness score |
| `缺失项` / `show gaps` | 显示所有未回答的必答/建议题目 Show all unanswered required/recommended questions |

### 语言控制 | Language Control

| 指令 Command | 说明 Description |
|---|---|
| `切换英文` / `switch to English` | 将交互语言切换为英文，后续问卷以英文展示 Switch interaction language to English |
| `切换中文` / `switch to Chinese` | 将交互语言切换为中文，后续问卷以中文展示 Switch interaction language to Chinese |
| `用英文生成` / `generate in English` | 仅本次成果物使用英文 Generate this deliverable in English only |
| `用中文生成` / `generate in Chinese` | 仅本次成果物使用中文 Generate this deliverable in Chinese only |
| `用双语生成` / `generate bilingual` | 仅本次成果物使用中英双语 Generate this deliverable bilingually |
| `成果物语言切换` / `switch deliverable language` | 永久更改成果物默认语言 Permanently change default deliverable language |

---

## 数据完整性校验 | Completeness Validation

> 在生成报告前，引擎自动执行完整性校验，确保数据质量满足报告生成要求。
> Before report generation, the engine automatically runs completeness validation to ensure data quality meets report generation requirements.

### 报告就绪度评分 | Report Readiness Score

引擎计算 0-100% 的报告就绪度评分，基于以下权重:

| 模块 Module | 权重 Weight | 最低通过要求 Minimum Pass |
|---|---|---|
| Module 0: 客户识别 Client Recognition | 5% | Q0.1 + Q0.2 + Q0.3 + Q0.4 已回答 |
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

**Module 0 — 客户识别 Client Recognition:**
- 必须: 客户名称确认(Q0.1)、行业确认(Q0.2)、企业规模(Q0.3)、顾问模式(Q0.4)
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

*问卷引擎 v1.3.0 | Questionnaire Engine v1.3.0*
*支持客户名称智能补全、行业自动识别、行业预填、顾问模式切换、完整性校验、中文/中英双语/英文三种成果物语言、强制联网搜索与置信度标注 | Supports client name auto-completion, industry auto-detection, industry pre-fill, consultant mode switching, completeness validation, Chinese/Bilingual/English deliverable output, mandatory WebSearch and confidence tagging*
