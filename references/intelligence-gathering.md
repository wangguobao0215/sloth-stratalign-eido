# 深略 · StratAlign — 企业情报采集引擎
# Enterprise Intelligence Gathering Engine

> 融合 OSINT 结构化情报方法论与 Web 采集最佳实践，为管理咨询场景提供可追溯、有置信度的客户数据。
> Fuses OSINT structured intelligence methodology with web scraping best practices, delivering traceable, confidence-rated client data for management consulting.

<!-- 
METHODOLOGY ORIGINS:
- Company intelligence workflows: adapted from danielmiessler/personal_ai_infrastructure OSINT framework (279 sources, 7 workflows, phased investigation methodology)
- Web scraping best practices: adapted from mindrally/skills web-scraping (Python toolchain, anti-bot handling, ethical scraping)
- China market extensions: original StratAlign contribution (7-category Chinese source catalog)
-->

---

## 1. 核心原则 | Core Principles

### 1.1 搜索强制原则 Search-First Mandate

引擎在预填**任何客户相关数据**时，**必须先执行 WebSearch 联网搜索**。这不是建议，而是硬性要求。违反此原则等同于向客户提交未经验证的数据——这在管理咨询中是不可接受的。

The engine **MUST perform WebSearch** before pre-filling **any client-related data**. This is not a recommendation — it is a hard requirement. Violating this principle is equivalent to submitting unverified data to a client, which is unacceptable in management consulting.

| 规则 Rule | 说明 Description |
|---|---|
| **绝不臆造** Never Fabricate | 不得基于训练数据编造公司名称、员工人数、IT系统、财务数据等具体事实 |
| **搜索优先** Search First | 每个预填字段必须至少有一次 WebSearch 搜索尝试记录 |
| **来源标注** Source Attribution | 每条数据必须标注来源 URL 或来源类型 |
| **置信度标注** Confidence Tag | 每条数据必须标注 [C1]~[C4] 置信度等级 |
| **失败透明** Failure Transparency | 搜索无结果时如实告知，标注 [C4]，不得用行业默认值冒充实际数据 |
| **时效标注** Recency Tag | 超过 2 年的数据标注 `(⚠️ 数据可能过时 yyyy)` |

### 1.2 置信度等级体系 Confidence Rating System

| 等级 Level | 标记 Tag | 判定标准 Criteria | 来源要求 Source Requirement |
|---|---|---|---|
| 高 HIGH | `[C1]` | 多源交叉验证 Multi-source verified | 至少 2 个独立来源互相印证 |
| 中 MEDIUM | `[C2]` | 单一可信来源 Single reliable source | 年报/官方公告/工商数据等权威单源 |
| 低 LOW | `[C3]` | 间接推断 Inferred | 招聘信息推断、行业惯例推测、非权威来源 |
| 未知 UNKNOWN | `[C4]` | 无法获取 Unavailable | 搜索无结果，仅使用行业默认值占位 |

**升级规则**: 同一数据在两个独立来源中出现 → 从 [C2] 升级为 [C1]。
**降级规则**: 数据来源超过 3 年 → 自动降一级（[C1]→[C2]，[C2]→[C3]）。

---

## 2. 企业情报工作流 | Company Intelligence Workflows

### 2.1 企业全景画像工作流 Company Profile Workflow

> 适用于: Module 0 (Q0.1-Q0.3) — 客户识别阶段。
> 目标: 建立客户身份、行业、规模的可信基线。

```
Phase 1: 实体识别 Entity Identification
├── WebSearch: "{输入名称}" 工商注册 全称
├── WebSearch: "{输入名称}" 公司 官网
├── 歧义处理: 若匹配多家 → 列出候选请用户确认
├── 输出: 正式注册名称、统一社会信用代码
└── 置信度: [C1] 如工商数据确认 / [C2] 如仅官网确认

Phase 2: 行业定位 Industry Classification
├── WebSearch: "{公司全称}" 主营业务 行业分类
├── WebSearch: "{公司全称}" 所属行业 经营范围
├── 交叉验证: 工商经营范围 vs 实际业务描述
├── 多业态检测: 若主营覆盖多个行业 → 提示用户选择主业态
├── 输出: 行业分类 + 对应行业剧本
└── 置信度: [C1] 如工商+官网一致 / [C2] 如单源 / [C3] 如推断

Phase 3: 企业规模 Company Size
├── WebSearch: "{公司全称}" 员工人数 2025 OR 2024
├── WebSearch: "{公司全称}" 年报 员工总数
├── WebSearch: "{公司全称}" 招聘 规模 (招聘平台通常显示企业规模区间)
├── 优先级: 年报数据 > 工商数据 > 招聘平台数据 > 推断
├── 输出: 员工人数(具体或范围) + 规模分级
└── 置信度: [C1] 如年报确认 / [C2] 如工商或招聘平台 / [C3] 如推断
```

### 2.2 IT 系统清单情报工作流 IT System Inventory Intelligence Workflow

> 适用于: Module 3 (Q3.1) — 这是数据质量风险最高的环节。
> 目标: 获取客户实际在用的 IT 系统清单，而非行业泛化猜测。

```
Phase 1: 年报/公告挖掘 Annual Report Mining (上市公司优先)
├── WebSearch: "{公司全称}" 年报 信息化 OR 数字化 OR IT系统
├── WebSearch: "{公司全称}" 年度报告 信息技术 投入 2024 OR 2025
├── WebFetch: 对高价值搜索结果页面获取完整内容
├── 提取目标:
│   ├── 信息化投入金额及占比
│   ├── 明确提及的系统名称 (ERP/MES/CRM/...)
│   ├── 供应商/实施伙伴名称
│   ├── 数字化转型战略描述
│   └── IT 团队规模或组织架构
└── 置信度: [C1] 年报数据（最权威）

Phase 2: 招聘信息技术栈反推 Job Posting Tech Stack Inference
├── WebSearch: "{公司全称}" 招聘 SAP OR Oracle OR 用友 OR 金蝶
├── WebSearch: "{公司全称}" 招聘 MES OR ERP OR PLM OR WMS OR CRM OR OA
├── WebSearch: "{公司全称}" 招聘 Java OR Python OR .NET OR 运维 OR DBA
├── WebSearch: site:zhipin.com OR site:lagou.com "{公司全称}" 技术
├── 反推逻辑:
│   ├── 岗位要求 "SAP ABAP 开发" → 企业使用 SAP ERP [C3]
│   ├── 岗位要求 "Teamcenter 管理员" → 企业使用 Siemens PLM [C3]
│   ├── 岗位要求 "MES 实施" → 企业有 MES 系统(供应商待确认) [C3]
│   ├── 多个岗位反复提及同一系统 → 升级为 [C2]
│   └── 岗位要求的技术栈组合 → 推断整体架构风格
├── 提取目标:
│   ├── 技术栈关键词 (编程语言、框架、数据库、中间件)
│   ├── 系统管理类岗位 (ERP顾问、DBA、MES工程师等)
│   ├── 数字化/IT 部门组织结构线索
│   └── 在招岗位数量 → 推断 IT 团队规模
└── 置信度: [C3] 单条推断 / [C2] 多条交叉印证

Phase 3: 供应商合作关系验证 Vendor Partnership Verification
├── WebSearch: "{公司全称}" 签约 OR 合作 OR 中标 SAP OR 用友 OR 金蝶 OR Oracle
├── WebSearch: "{公司全称}" 数字化转型 OR 智能制造 合作 OR 实施
├── WebSearch: "{供应商名}" 客户案例 "{公司全称}"  (反向搜索)
├── WebSearch: "{公司全称}" site:sap.com OR site:yonyou.com OR site:kingdee.com
├── 提取目标:
│   ├── 确认的供应商关系 (签约新闻/案例白皮书)
│   ├── 实施项目内容和范围
│   ├── 上线时间 (推断系统版本和生命周期阶段)
│   └── 合作深度 (单产品 vs 全栈)
└── 置信度: [C1] 如双方公开确认 / [C2] 如单方公告

Phase 4: 技术领导力与架构访谈 Tech Leadership & Architecture
├── WebSearch: "{公司全称}" CIO OR CTO OR 信息总监 OR 数字化 访谈
├── WebSearch: "{公司全称}" 信息化建设 案例 OR 分享 OR 演讲
├── WebSearch: "{公司全称}" 数字化转型 架构 OR 中台 OR 云 OR 微服务
├── 提取目标:
│   ├── CIO/CTO 在公开场合透露的架构决策
│   ├── 技术路线图(如"去IOE"、"全面上云"、"数据中台"等)
│   ├── 数字化转型阶段自我评估
│   └── 对特定技术/供应商的公开评价
└── 置信度: [C2] 直接引用 / [C3] 间接推断

Phase 5: 技术指纹检测 Technology Fingerprinting (域名可达时)
├── WebSearch: "{公司官网域名}" site:builtwith.com
├── WebSearch: "{公司官网域名}" technology stack OR tech stack
├── 检测范围 (通过官网前端技术推断后端架构):
│   ├── Web 技术: 前端框架、服务器、CDN
│   ├── 分析工具: Google Analytics、百度统计、友盟
│   ├── 营销工具: 在线客服、表单工具、CRM 前端
│   ├── 电商平台: 商城引擎、支付接口
│   └── 安全措施: WAF、SSL 证书类型
├── 注意: 此方法仅能检测面向公众的技术栈，
│   内部系统 (ERP/MES/OA) 通常不可探测
└── 置信度: [C2] 技术指纹确认 / [C3] 间接推断
```

### 2.3 财务情报工作流 Financial Intelligence Workflow

> 适用于: Module 1 (Q1.4 财务目标), Module 4 (Q4.1 预算) — 辅助预填。
> 目标: 获取客户的关键财务指标，用于 ROI 计算基准。

```
Phase 1: 公开财务数据 Public Financial Data
├── WebSearch: "{公司全称}" 年报 营收 利润 2024
├── WebSearch: "{公司全称}" 财务数据 OR 经营数据 OR 业绩
├── WebSearch: "{证券代码}" 年报 巨潮资讯 OR cninfo (A股)
├── 提取: 营收、净利润、毛利率、研发投入、信息化投入
└── 置信度: [C1] 年报数据

Phase 2: 信息化投入推算 IT Spending Estimation
├── 如年报有 "信息化投入" 数据 → 直接使用 [C1]
├── 如无 → 按行业基准推算:
│   ├── 制造业: IT 支出 ≈ 营收 1.5-3%
│   ├── 零售业: IT 支出 ≈ 营收 2-4%
│   ├── 金融业: IT 支出 ≈ 营收 7-12%
│   ├── 医疗业: IT 支出 ≈ 营收 3-5%
│   └── 专业服务: IT 支出 ≈ 营收 4-8%
└── 置信度: [C3] 行业基准推算
```

### 2.4 竞争情报工作流 Competitive Intelligence Workflow

> 适用于: 全模块 — 为行业对标和差距分析提供参照。
> 目标: 建立客户在行业中的相对位置。

```
Phase 1: 行业地位确认
├── WebSearch: "{公司全称}" 行业排名 OR 市场份额
├── WebSearch: "{所属行业}" 龙头企业 OR 排名 2024 OR 2025
├── 输出: 行业排名、主要竞争对手名单

Phase 2: 数字化成熟度对标
├── WebSearch: "{公司全称}" 数字化 OR 智能化 奖项 OR 标杆 OR 案例
├── WebSearch: "{行业}" 数字化转型 标杆企业 OR 最佳实践
├── 输出: 客户在行业数字化中的相对位置评估
└── 置信度: [C2] 有对标数据 / [C3] 推断
```

---

## 3. 情报源编目 | Intelligence Source Catalog

### 3.1 中国市场情报源 China Market Sources

| 类别 | 一级来源(权威) | 二级来源(参考) | 数据内容 |
|---|---|---|---|
| **工商注册** | 国家企业信用信息公示系统 (gsxt.gov.cn) | 天眼查、企查查、爱企查 | 公司全称、注册资本、经营范围、法人、股东、经营状态、行业代码 |
| **上市公司财务** | 巨潮资讯网 (cninfo.com.cn)、上交所/深交所/北交所公告系统 | 东方财富 (eastmoney.com)、同花顺 (10jqka.com.cn) | 年报/季报、营收利润、员工人数、信息化投入、管理层讨论 |
| **招聘信息** | Boss直聘 (zhipin.com)、拉勾 (lagou.com) | 猎聘 (liepin.com)、前程无忧 (51job.com)、智联招聘 | 技术栈反推、岗位结构、团队规模、薪资水平(推断数字化投入意愿) |
| **技术资讯** | InfoQ 中文 (infoq.cn)、CSDN | 36氪、虎嗅、钛媒体、IT经理网 | CIO访谈、技术选型案例、架构演进、数字化转型进展 |
| **行业报告** | IDC 中国、Gartner 中国 | 艾瑞咨询、亿欧智库、甲子光年 | 行业趋势、技术采用率、厂商排名、最佳实践 |
| **供应商案例** | SAP/Oracle/用友/金蝶/浪潮/华为云/阿里云官方客户案例页 | 合作伙伴/ISV 案例库 | 系统实施确认、项目范围、合作深度 |
| **知识产权** | 国家知识产权局 CNIPA (cnipa.gov.cn)、Google Patents | 佰腾网 (baiten.cn) | 技术研发方向、专利布局、创新能力评估 |

### 3.2 全球市场情报源 Global Market Sources

| 类别 | 来源 Sources | 数据内容 |
|---|---|---|
| **公司注册** | OpenCorporates、各国公司注册处 | 全球企业注册数据 |
| **财务数据** | SEC EDGAR (美股)、Companies House (英国) | 年报、10-K/10-Q、财务报表 |
| **商业情报** | Crunchbase、PitchBook、ZoomInfo | 融资、估值、高管、员工规模 |
| **技术指纹** | BuiltWith、Wappalyzer、SimilarWeb | 网站技术栈、流量、SEO |
| **人才数据** | LinkedIn、Glassdoor | 组织结构、团队规模、企业文化 |
| **域名/基础设施** | DomainTools、Shodan、Hunter.io | 域名注册、服务器架构、邮箱格式 |
| **法律/合规** | PACER (美国法院)、各国法院公告系统 | 诉讼记录、合规风险 |
| **专利** | Google Patents、USPTO、EPO | 全球专利布局 |
| **政府采购** | 各国政府采购公告平台 | 中标信息、项目预算 |
| **行业分析** | Gartner、Forrester、IDC、McKinsey Global Institute | 行业魔力象限、技术成熟度曲线 |

---

## 4. Web 采集最佳实践 | Web Scraping Best Practices

### 4.1 工具选择策略 Tool Selection Strategy

引擎根据目标页面特征选择最合适的采集方法:

| 页面类型 | 推荐方法 | 适用场景 |
|---|---|---|
| 静态 HTML 页面 | WebFetch (内置) | 年报摘要页、新闻报道、企业官网介绍页 |
| API 端点 | WebFetch + JSON 解析 | 招聘平台 API、金融数据 API |
| JavaScript 渲染页面 | WebSearch → WebFetch 结合 | 现代 SPA 架构的企业官网 |
| PDF 年报 | WebSearch 定位 → 引用摘要 | 完整年报文档(引擎标注页码供顾问查阅) |
| 反爬保护页面 | 多次 WebSearch 换词重试 | 部分招聘平台、金融资讯站 |

### 4.2 搜索策略模式 Search Strategy Patterns

**景观扫描 Landscape Scan** (改编自 thepexcel deep-research):
在搜索特定答案之前，先用宽泛查询了解全貌:
```
第1步: WebSearch "{公司全称}" → 浏览前5条结果了解企业概况
第2步: 根据概况中的关键词细化搜索
第3步: 针对具体问题深入搜索
```

**时效脉冲 Recency Pulse**:
优先搜索近期变化，捕捉最新动态:
```
WebSearch: "{公司全称}" 2025 OR 2026 数字化 OR IT OR 信息化
→ 优先使用最近6个月内的数据
→ 超过2年的数据自动降级置信度
```

**上游追溯 Upstream Tracing**:
从供应商端反向验证:
```
WebSearch: "SAP" 客户案例 "{行业}" "{地域}"
WebSearch: "用友 NC" 实施案例 "{行业}"
→ 用供应商案例库反向确认客户的系统选型
```

**饱和停止 Saturation Stop**:
当搜索结果不再产生新信息时停止:
```
规则: 连续2轮搜索未发现新系统/供应商 → 停止搜索
规则: 同一数据已有3个独立来源 → 无需继续验证，标为 [C1]
```

### 4.3 数据质量控制 Data Quality Control

**提取规则**:
- 优先提取**明确事实**(公司名用了SAP) 而非**模糊表述**(公司可能在用ERP)
- 区分**当前状态**与**规划/意向**（"正在实施MES" ≠ "已上线MES"）
- 注意**时间戳** — 3 年前的系统清单可能已大幅变化
- 招聘信息中的技术栈 ≠ 在用系统（可能是新采购计划）

**去重与合并**:
- 同一系统出现在年报和招聘 JD 中 → 合并为一条，升级置信度
- 不同来源称呼不一致时统一为标准名称（如 "SAP S/4" = "SAP S/4HANA"）

**冲突处理**:
- 年报称 "使用用友 NC"，但招聘 JD 要求 "SAP 经验" → 标注冲突，可能正在迁移
- 旧来源称 "自研 ERP"，新来源称 "上线 SAP" → 以新来源为准，标注变更

### 4.4 伦理与合规 Ethics & Compliance

| 规则 Rule | 说明 Description |
|---|---|
| **仅使用公开数据** | 不得访问需要登录的内部系统或私密数据库 |
| **尊重 robots.txt** | WebFetch 前检查目标站点的爬虫政策 |
| **不采集个人隐私** | 不采集非公开的个人联系方式、薪资等敏感信息 |
| **标注所有来源** | 所有数据必须可追溯到公开来源 URL |
| **及时告知不确定性** | 推断或猜测必须明确标注，不得伪装为确认事实 |

---

## 5. 问卷各环节搜索规程 | Per-Question Search Procedures

### Module 0: 客户识别

| 问题 | 必须搜索 | 搜索词模板 | 预期输出 |
|---|---|---|---|
| Q0.1 客户名称 | 是 | `"{输入}" 工商注册 全称`, `"{输入}" 公司 官网` | 正式名称 [C1/C2] |
| Q0.2 行业识别 | 是 | `"{全称}" 主营业务 行业`, `"{全称}" 经营范围` | 行业分类 [C1/C2] |
| Q0.3 员工规模 | 是 | `"{全称}" 员工人数 2025`, `"{全称}" 年报 员工` | 员工数+规模分级 [C1/C2/C3] |

### Module 1: 战略解码

| 问题 | 建议搜索 | 搜索词模板 | 预期输出 |
|---|---|---|---|
| Q1.1 愿景 | 是 | `"{全称}" 愿景 OR 使命 OR 企业文化 官网` | 官网愿景描述 [C2] |
| Q1.3 战略主题 | 是 | `"{全称}" 战略 OR 战略规划 OR 五年规划` | 公开战略方向 [C2/C3] |
| Q1.4 财务目标 | 是 | `"{全称}" 营收 利润 2024 年报 目标` | 关键财务指标 [C1/C2] |
| Q1.9 执行障碍 | 可选 | `"{全称}" 经营风险 OR 挑战 年报` | 年报风险章节 [C2] |

### Module 2: 瓶颈扫描

| 问题 | 建议搜索 | 搜索词模板 | 预期输出 |
|---|---|---|---|
| Q2.1 核心流程 | 可选 | `"{全称}" 业务流程 OR 价值链 OR 运营模式` | 业务模式理解 [C3] |
| Q2.2 痛点 | 可选 | `"{全称}" 客户投诉 OR 问题 OR 召回` | 公开的运营问题 [C3] |

### Module 3: 覆盖分析

| 问题 | 必须搜索 | 搜索词模板 | 预期输出 |
|---|---|---|---|
| Q3.1 IT系统清单 | **强制** | **执行完整5阶段工作流 (§2.2)** | 结构化系统清单 [C1~C4] |
| Q3.2 集成现状 | 建议 | `"{全称}" 数据中台 OR ESB OR 集成平台` | 集成架构线索 [C3] |
| Q3.4 云化程度 | 建议 | `"{全称}" 上云 OR 云计算 OR 阿里云 OR 华为云` | 云化策略 [C2/C3] |

### Module 4: 投资组合

| 问题 | 建议搜索 | 搜索词模板 | 预期输出 |
|---|---|---|---|
| Q4.1 总体预算 | 可选 | `"{全称}" IT预算 OR 信息化投入 OR 数字化投资` | 投资规模线索 [C2/C3] |

---

## 6. 输出格式规范 | Output Format Standards

### 6.1 预填数据展示格式

每条预填数据必须包含: **数据值 + 来源 + 置信度**。格式:

```
字段名: 数据值
来源: [来源描述] (URL 如有)
置信度: [C1/C2/C3/C4]
时效: yyyy 年数据
```

### 6.2 IT 系统清单输出格式

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🔍 IT 系统清单 (联网搜索汇总) | IT System Inventory

客户: {公司全称}
搜索时间: {当前日期}
数据来源: {搜索轮次摘要}
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

| # | 系统名称 | 类型 | 供应商 | 上线年份 | 来源 | 置信度 |
|---|----------|------|--------|----------|------|--------|
| 1 | SAP S/4HANA | ERP | SAP | 2021 | 年报+招聘 | [C1] |
| 2 | ... | ... | ... | ... | ... | ... |

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
搜索覆盖: 年报 ✅ | 招聘 ✅ | 供应商 ✅ | 技术领导力 ✅ | 技术指纹 ⬜
[C1] 高置信: X 项 | [C2] 中: X 项 | [C3] 低: X 项 | [C4] 未知: X 项

⚠️ [C3]/[C4] 项目请顾问与客户确认后修正。
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### 6.3 搜索过程摘要格式

每次预填完成后，引擎应在折叠块中附上搜索过程摘要:

```
<details>
<summary>🔍 搜索过程摘要 | Search Process Summary</summary>

搜索轮次: 4 轮
搜索查询数: 12 次
有效结果页: 8 页
WebFetch 深入: 3 页

轮次明细:
1. 年报搜索 (3 queries) → 找到 2024 年报信息化章节
2. 招聘搜索 (4 queries) → 发现 15 个技术相关岗位
3. 供应商搜索 (3 queries) → 确认 SAP 合作关系
4. 技术领导力 (2 queries) → 找到 CIO 访谈 1 篇

</details>
```

---

## 7. 与行业剧本的协作 | Integration with Industry Playbooks

联网搜索结果与行业剧本预填值的关系:

| 场景 | 处理方式 |
|---|---|
| 搜索结果与剧本一致 | 使用搜索结果(更具体)，置信度 [C1/C2] |
| 搜索结果与剧本冲突 | 以搜索结果为准，标注差异供顾问确认 |
| 搜索无结果 | 使用行业剧本默认值，标注 [C4]，提示顾问与客户确认 |
| 搜索发现剧本未覆盖的系统 | 补充进清单，标注为搜索发现 |

**优先级**: 联网搜索实时数据 > 客户导入资料 > 行业剧本默认值 > 训练数据

---

## 8. 行业专属情报采集规程 | Industry-Specific Intelligence Procedures

> 本节为 §2.2 IT系统清单情报工作流的**行业细化版本**。每个行业提供:
> - IT 系统参考矩阵（预期存在哪些系统、主流厂商是谁）
> - Phase 2 招聘搜索专属关键词
> - Phase 3 供应商反向搜索专属查询
> - 行业专属数据源与基准值
>
> 使用方式: 当 Q0.2 确定行业后，引擎自动切换到对应行业规程，将下方关键词注入 §2.2 的 5 阶段工作流中。
> 覆盖行业: 制造(§8.1)、零售(§8.2)、金融(§8.3)、医疗(§8.4)、专业服务(§8.5)、能源(§8.6)、交通物流(§8.7)、房地产建筑(§8.8)。

---

### 8.1 制造业 | Manufacturing

#### 8.1.1 IT 系统参考矩阵

| 系统类别 | 预期系统 | 主流厂商(中国) | 主流厂商(全球) | 搜索优先级 |
|---|---|---|---|---|
| ERP | 企业资源计划 | 用友 U9/NC, 金蝶 K/3/Cloud, 浪潮 GS | SAP S/4HANA, Oracle EBS/Cloud | ★★★ 必搜 |
| MES | 制造执行系统 | 宝信 MES, 中控 supMES, 鼎捷 | Siemens Opcenter, Rockwell FTPC, DELMIA Apriso | ★★★ 必搜 |
| PLM | 产品全生命周期 | 天喻 InteVue, 华天 CAPP | Siemens Teamcenter, PTC Windchill, Dassault ENOVIA | ★★★ 必搜 |
| SCADA/DCS | 工控系统 | 浙大中控 JX-300, 和利时 HOLLiAS | Siemens WinCC, Honeywell Experion, ABB 800xA | ★★☆ 建议搜 |
| WMS | 仓储管理 | 富勒 FLUX WMS, 唯智 | Manhattan, Blue Yonder WMS, Infor WMS | ★★☆ 建议搜 |
| QMS | 质量管理 | 盈飞无限 | ETQ, MasterControl, Sparta Systems TrackWise | ★☆☆ 可选 |
| APS | 高级排程 | 安达发, 永凯 | Asprova, Flexsche, o9 Solutions | ★☆☆ 可选 |
| CAD/CAE | 工程设计 | 中望 CAD, 浩辰 CAD | AutoCAD, SolidWorks, CATIA, NX | ★★☆ 建议搜 |
| IoT 平台 | 物联网/工业互联 | 树根互联, 海尔COSMOPlat, 徐工汉云 | PTC ThingWorx, AWS IoT, Azure IoT | ★☆☆ 可选 |
| SRM | 供应商管理 | 甄云, 企企通 | SAP Ariba, Coupa, Jaggaer | ★☆☆ 可选 |

#### 8.1.2 Phase 2 招聘搜索关键词

```
# MES/生产执行 — 制造业核心指标
WebSearch: "{公司全称}" 招聘 MES OR "制造执行" OR "生产调度" OR "车间管理"
WebSearch: "{公司全称}" 招聘 PLC OR SCADA OR DCS OR "工控" OR "自动化"
WebSearch: "{公司全称}" 招聘 PLM OR Teamcenter OR Windchill OR "产品数据管理"
WebSearch: "{公司全称}" 招聘 "SAP PP" OR "SAP MM" OR "SAP QM" OR "SAP PM"
WebSearch: "{公司全称}" 招聘 "用友 U9" OR "金蝶 K/3" OR "鼎捷" OR "浪潮 GS"
WebSearch: "{公司全称}" 招聘 APS OR "高级排程" OR "智能排产"
WebSearch: "{公司全称}" 招聘 IoT OR "物联网" OR "设备联网" OR "数采"

# 反推逻辑补充:
# "PLC 编程" → 有产线自动化 [C3]
# "MES 实施顾问" → 正在部署或已有 MES [C3]
# "SAP PP 顾问" → 使用 SAP 生产模块 [C3]
# "Teamcenter 管理员" → 使用 Siemens PLM [C3]
# "AGV 调度" → 有智能仓储/物流系统 [C3]
```

#### 8.1.3 Phase 3 供应商反向搜索

```
# 国内 MES/工控厂商
WebSearch: "宝信软件" OR "中控技术" OR "鼎捷软件" 客户案例 "{公司全称}"
WebSearch: "树根互联" OR "海尔COSMOPlat" OR "徐工汉云" 合作 "{公司全称}"
WebSearch: "{公司全称}" 签约 OR 中标 "智能制造" OR "工业互联网" OR "数字化车间"

# 国际 PLM/MES 厂商
WebSearch: "Siemens" OR "PTC" OR "Dassault" customer "{公司英文名或简称}"
WebSearch: "Rockwell" OR "Honeywell" OR "ABB" partner "{公司全称}"

# 政府项目/示范线索
WebSearch: "{公司全称}" "智能制造示范" OR "两化融合" OR "灯塔工厂"
WebSearch: "{公司全称}" "国家智能制造试点" OR "工业互联网试点"
```

#### 8.1.4 行业专属数据源与基准

```
专属数据源:
├── 工信部智能制造示范企业名单 (miit.gov.cn)
├── 两化融合管理体系贯标企业名单
├── 世界经济论坛"灯塔工厂"名单 (weforum.org)
├── e-works 智能制造案例库 (e-works.net.cn)
├── 中国智能制造网 (gkzhan.com)
└── 工控网 (gongkong.com)

IT 预算基准:
├── 制造业 IT 支出占营收: 1.5-3% (Gartner 2024)
├── 离散制造 vs 流程制造:
│   ├── 离散制造(汽车/电子/机械): 偏 PLM + MES + APS
│   └── 流程制造(化工/食品/制药): 偏 DCS/SCADA + QMS + LIMS
├── 规模分级:
│   ├── < 500 人: 通常用友/金蝶 + 基础 MES
│   ├── 500-5000 人: SAP/Oracle + 专业 MES + PLM
│   └── > 5000 人: SAP S/4HANA + 完整 ISA-95 架构
└── 数字化成熟度标杆:
    ├── 初级: ERP + OA + 基础财务 (多数中小制造企业)
    ├── 中级: ERP + MES + PLM + WMS 部分打通
    ├── 高级: ISA-95 全栈 + IoT + 数据中台
    └── 标杆: 灯塔工厂级 (如三一重工、海尔、美的)
```

---

### 8.2 零售业 | Retail & Consumer

#### 8.2.1 IT 系统参考矩阵

| 系统类别 | 预期系统 | 主流厂商(中国) | 主流厂商(全球) | 搜索优先级 |
|---|---|---|---|---|
| POS | 收银/门店系统 | 科脉, 海信商用, 客如云 | Oracle Retail Xstore, NCR Voyix, Toshiba | ★★★ 必搜 |
| ERP | 企业资源计划 | 用友, 金蝶, 百胜 | SAP S/4HANA Retail, Oracle Retail | ★★★ 必搜 |
| OMS | 订单管理 | 聚水潭, 旺店通, 管易云 | Manhattan OMS, IBM Sterling | ★★★ 必搜 |
| WMS | 仓储管理 | 富勒 FLUX, 唯智, 巨沃 | Manhattan WMS, Blue Yonder | ★★☆ 建议搜 |
| CRM/CDP | 客户数据平台 | 有赞, 微盟, 神策数据, 创略科技 | Salesforce, Adobe Experience Platform, Treasure Data | ★★★ 必搜 |
| 电商中台 | 全渠道运营 | 有赞, 微盟, 商派 | Shopify Plus, Magento/Adobe Commerce, VTEX | ★★★ 必搜 |
| SCM | 供应链管理 | 旺链科技, 准时达 | Blue Yonder, Kinaxis, o9 Solutions | ★★☆ 建议搜 |
| BI/数据分析 | 商业智能 | 帆软 FineBI, 永洪, 观远数据 | Tableau, Power BI, Looker | ★★☆ 建议搜 |
| 会员系统 | 忠诚度/私域 | 有赞, 企业微信+SCRM, 群脉 | SAP Emarsys, Salesforce Marketing Cloud | ★★☆ 建议搜 |

#### 8.2.2 Phase 2 招聘搜索关键词

```
# 全渠道/电商 — 零售核心
WebSearch: "{公司全称}" 招聘 "全渠道" OR "新零售" OR "O2O" OR "私域"
WebSearch: "{公司全称}" 招聘 OMS OR "订单管理" OR "聚水潭" OR "旺店通"
WebSearch: "{公司全称}" 招聘 POS OR "收银系统" OR "门店系统" OR "客如云"
WebSearch: "{公司全称}" 招聘 CRM OR CDP OR "客户数据" OR "会员运营"
WebSearch: "{公司全称}" 招聘 "SAP Retail" OR "百胜" OR "电商中台"
WebSearch: "{公司全称}" 招聘 "数据分析" OR "BI" OR "用户增长" OR "数据运营"

# 反推逻辑补充:
# "聚水潭运维" → 使用聚水潭 OMS [C3]
# "企业微信 SCRM" → 私域运营体系 [C3]
# "有赞开发" → 有赞电商体系 [C3]
# "门店数字化运营" → 有门店管理系统 [C3]
# "商品中台架构师" → 正在建设中台 [C3]
```

#### 8.2.3 Phase 3 供应商反向搜索

```
# 电商/全渠道生态
WebSearch: "有赞" OR "微盟" OR "聚水潭" 客户案例 "{公司全称}"
WebSearch: "神策数据" OR "GrowingIO" OR "观远数据" 合作 "{公司全称}"
WebSearch: "{公司全称}" 签约 "新零售" OR "全渠道" OR "智慧门店"

# 国际零售技术
WebSearch: "Salesforce" OR "Adobe" OR "SAP" retail customer "{公司英文名}"
WebSearch: "{公司全称}" "数字化门店" OR "智慧零售" OR "无人零售"

# 平台生态线索
WebSearch: "{公司全称}" "天猫" OR "京东" OR "拼多多" OR "抖音电商" 旗舰店
WebSearch: "{公司全称}" "小程序" OR "私域" OR "企业微信" OR "社群运营"
```

#### 8.2.4 行业专属数据源与基准

```
专属数据源:
├── 中国连锁经营协会 (CCFA) 百强榜
├── 联商网 (linkshop.com) — 零售行业资讯
├── 亿邦动力 (ebrun.com) — 电商行业数据
├── 国家统计局社会消费品零售数据
├── 各电商平台商家排行榜
└── 赢商网 (winshang.com) — 商业地产/门店数据

IT 预算基准:
├── 零售业 IT 支出占营收: 2-4% (Gartner 2024)
├── 业态分化:
│   ├── 线上为主电商: 偏 OMS + CDP + 数据分析 (IT占比更高 3-6%)
│   ├── 线下连锁零售: 偏 POS + ERP + WMS + 门店管理
│   ├── 全渠道品牌: OMS + CRM + 电商中台 + BI 全栈
│   └── 生鲜/便利: 偏 供应链 + 冷链 + 即时配送
├── 规模分级:
│   ├── < 50 门店: 轻量 SaaS (有赞/微盟 + 简易 ERP)
│   ├── 50-500 门店: 用友/金蝶 + 专业 POS + 区域仓 WMS
│   └── > 500 门店: SAP Retail + 全渠道中台 + 自建数据平台
└── 数字化成熟度标杆:
    ├── 初级: 单渠道 POS + 手工 Excel 管理
    ├── 中级: 线上+线下独立运营 + 基础会员体系
    ├── 高级: 全渠道统一库存 + CDP + 精准营销
    └── 标杆: 名创优品, 泡泡玛特, 百果园(全链路数字化)
```

---

### 8.3 金融服务业 | Financial Services

#### 8.3.1 IT 系统参考矩阵

| 系统类别 | 预期系统 | 主流厂商(中国) | 主流厂商(全球) | 搜索优先级 |
|---|---|---|---|---|
| 核心业务系统 | 核心银行/保险/证券 | 长亮科技, 神州信息, 宇信科技, 中科软 | Temenos, FIS, Infosys Finacle | ★★★ 必搜 |
| 交易系统 | 证券/基金交易 | 恒生电子 HUNDSUN, 金证股份 | Murex, Calypso, FIS | ★★★ 必搜(证券/基金) |
| 保险核心 | 核心保险平台 | 中科软, 易保网络 | Guidewire, Duck Creek, Majesco | ★★★ 必搜(保险) |
| 风控系统 | 风险管理/信用评估 | 同盾科技, 百融云创, 邦盛科技 | SAS, Moody's Analytics, FICO | ★★★ 必搜 |
| AML/KYC | 反洗钱/客户识别 | 安硕信息, 百融云创 | NICE Actimize, Oracle Financial Crime | ★★☆ 建议搜 |
| 渠道系统 | 网银/手机银行/柜面 | 科蓝软件, 宇信科技, 文思海辉 | Temenos Infinity, Backbase | ★★☆ 建议搜 |
| 支付/清算 | 支付网关/清算系统 | 银联, 网联, 拉卡拉 | FIS, ACI Worldwide, Stripe | ★★☆ 建议搜 |
| 监管报送 | 监管报表/合规报告 | 安硕信息, 恒生电子 | AxiomSL, Wolters Kluwer OneSumX, RegTek | ★☆☆ 可选 |
| 数据平台 | 大数据/数据仓库 | 星环科技, 数梦工场, 明略科技 | Cloudera, Teradata, Snowflake | ★★☆ 建议搜 |
| API 网关 | 开放银行/API管理 | 网易数帆, 阿里云 API 网关 | Kong, Apigee, MuleSoft | ★☆☆ 可选 |
| 中间件/ESB | 消息/集成平台 | 东方通 TongLINK, 普元 Primeton | IBM MQ, TIBCO, MuleSoft | ★☆☆ 可选 |
| CRM | 客户关系管理 | 销售易, 纷享销客 | Salesforce Financial Services Cloud | ★☆☆ 可选 |
| RPA | 流程自动化 | 弘玑 Cyclone, 来也科技 | UiPath, Blue Prism, Automation Anywhere | ★☆☆ 可选 |
| 灾备/安全 | 双活/等保 | 华为, 新华三 H3C | Dell EMC, Veritas, Splunk | ★☆☆ 可选 |

#### 8.3.2 Phase 2 招聘搜索关键词

```
# 核心系统/金融科技
WebSearch: "{公司全称}" 招聘 "核心系统" OR "核心银行" OR "核心交易" OR "清算"
WebSearch: "{公司全称}" 招聘 "风控" OR "反欺诈" OR "反洗钱" OR "AML" OR "KYC"
WebSearch: "{公司全称}" 招聘 "分布式" OR "微服务" OR "云原生" OR "容器化"
WebSearch: "{公司全称}" 招聘 "大数据" OR "数据仓库" OR "数据湖" OR "实时计算"
WebSearch: "{公司全称}" 招聘 "Kafka" OR "Flink" OR "Spark" OR "HBase" OR "TiDB"

# 金融行业子领域适配
# → 银行:
WebSearch: "{公司全称}" 招聘 "信贷系统" OR "网银" OR "手机银行" OR "支付清算"
# → 保险:
WebSearch: "{公司全称}" 招聘 "核保" OR "理赔" OR "精算" OR "保险核心"
# → 证券/基金:
WebSearch: "{公司全称}" 招聘 "交易系统" OR "柜台系统" OR "估值清算" OR "TA系统"

# 反推逻辑补充:
# "长亮核心开发" → 使用长亮核心银行系统 [C3]
# "Kafka 运维" → 有分布式消息队列架构 [C3]
# "风控模型工程师" → 有自研/采购风控平台 [C3]
# "等保三级" → 有完整安全合规体系 [C3]
# "分布式核心" → 核心系统正在或已完成分布式改造 [C3]
```

#### 8.3.3 Phase 3 供应商反向搜索

```
# 金融 IT 核心厂商
WebSearch: "长亮科技" OR "神州信息" OR "宇信科技" 客户案例 "{公司全称}"
WebSearch: "同盾科技" OR "百融云创" OR "邦盛科技" 合作 "{公司全称}"
WebSearch: "中科软" OR "科蓝软件" 签约 OR 中标 "{公司全称}"

# 金融云/基础设施
WebSearch: "{公司全称}" "金融云" OR "分布式核心" OR "信创" OR "国产化替代"
WebSearch: "华为" OR "阿里云" OR "腾讯云" 金融云 客户 "{公司全称}"

# 监管/合规线索
WebSearch: "{公司全称}" "监管科技" OR "RegTech" OR "数字化转型" OR "科技赋能"
WebSearch: "{公司全称}" site:pbc.gov.cn OR site:cbirc.gov.cn OR site:csrc.gov.cn
```

#### 8.3.4 行业专属数据源与基准

```
专属数据源:
├── 中国银保监会/证监会官网 (机构信息、处罚公告)
├── 中国人民银行金融科技委员会报告
├── 金融科技50强 / 毕马威金融科技榜
├── IDC 金融科技排名 (中国金融行业 IT 解决方案市场份额)
├── 零壹财经 (01caijing.com) — 金融科技资讯
├── 未央网 (weiyangx.com) — 金融科技研究
└── 中国金融信息化 (fcc.com.cn)

IT 预算基准:
├── 金融业 IT 支出占营收: 7-12% (行业最高)
├── 子领域分化:
│   ├── 大型银行: 核心+渠道+风控+大数据 全栈 (IT占比 8-15%)
│   ├── 中小银行: 核心+网银+基础风控 (外采为主)
│   ├── 保险公司: 核心保险+渠道+理赔 (IT占比 5-8%)
│   ├── 证券/基金: 交易+风控+合规 (IT占比 6-10%)
│   └── 消费金融/网贷: 风控+获客+大数据 (科技属性最强)
├── 监管要求:
│   ├── 信息技术投入占营业收入比例(银保监会关注指标)
│   ├── 等保三级(银行)/等保二级(保险/证券) 硬性要求
│   ├── 信创国产化替代时间表(2025-2028 关键窗口)
│   └── 数据安全法/个人信息保护法 合规要求
└── 数字化成熟度标杆:
    ├── 初级: 集中式核心 + 基础网银 + 手工风控
    ├── 中级: 分布式核心改造中 + 移动优先 + 规则引擎风控
    ├── 高级: 分布式微服务架构 + 开放银行 + AI风控
    └── 标杆: 招商银行, 平安集团, 微众银行(全栈自研)
```

---

### 8.4 医疗健康业 | Healthcare

#### 8.4.1 IT 系统参考矩阵

| 系统类别 | 预期系统 | 主流厂商(中国) | 主流厂商(全球) | 搜索优先级 |
|---|---|---|---|---|
| HIS | 医院信息系统 | 卫宁健康, 创业慧康, 东软 Neusoft, 万达信息 | Cerner(Oracle Health), Epic | ★★★ 必搜 |
| EMR/EHR | 电子病历 | 嘉和美康, 东华医为, 卫宁健康 | Epic, Cerner, Allscripts | ★★★ 必搜 |
| LIS | 检验信息系统 | 杏和科技, 天健科技 | Siemens Healthineers, Roche Diagnostics | ★★☆ 建议搜 |
| PACS | 影像归档系统 | 锐达科技, 深睿医疗, 东软医疗 | GE Healthcare, Philips, Agfa | ★★☆ 建议搜 |
| RIS | 放射信息系统 | 东软医疗, 安泰科技 | GE Healthcare, Philips | ★☆☆ 可选 |
| HRP | 医院资源规划 | 用友医疗, 金蝶医疗 | SAP, Oracle | ★☆☆ 可选 |
| 互联网医院 | 在线问诊/远程医疗 | 微医, 好大夫, 丁香园, 卫宁互联网医院 | Teladoc, Amwell | ★★☆ 建议搜 |
| 药品管理 | 药房/药库管理 | 海典软件, 九州通 | SAP, McKesson | ★☆☆ 可选 |
| CDR/数据平台 | 临床数据中心 | 卫宁健康, 东华医为, 森亿智能 | InterSystems HealthShare, IBM Watson Health | ★★☆ 建议搜 |
| 预约排班 | 门诊/检查预约与排班 | 卫宁健康, 金蝶医疗 | Epic Cadence, Cerner Scheduling | ★☆☆ 可选 |
| 医疗QMS | 医疗质量管理 | 海泰医疗, 嘉和美康 | Medisolv, Quantros, Qualitick | ★☆☆ 可选 |
| 医保结算 | 医保对接系统 | 各省医保局指定(久远银海等) | — | ★☆☆ (政策驱动) |

#### 8.4.2 Phase 2 招聘搜索关键词

```
# 医疗信息化核心
WebSearch: "{公司全称}" 招聘 HIS OR "医院信息" OR "电子病历" OR EMR OR EHR
WebSearch: "{公司全称}" 招聘 LIS OR PACS OR RIS OR "医学影像" OR "检验信息"
WebSearch: "{公司全称}" 招聘 "互联网医院" OR "远程医疗" OR "在线问诊" OR "智慧医疗"
WebSearch: "{公司全称}" 招聘 "临床数据" OR "CDR" OR "数据中心" OR "医疗大数据"

# 医疗行业子领域适配
# → 综合医院:
WebSearch: "{公司全称}" 招聘 "卫宁" OR "创业慧康" OR "东华医为" OR "嘉和美康"
# → 制药企业:
WebSearch: "{公司全称}" 招聘 "LIMS" OR "药品追溯" OR "GMP" OR "生产质量"
# → 医疗器械:
WebSearch: "{公司全称}" 招聘 "UDI" OR "医疗器械注册" OR "质量体系" OR "售后服务"
# → 连锁药店:
WebSearch: "{公司全称}" 招聘 "处方流转" OR "药品管理" OR "GSP" OR "电子监管码"

# 反推逻辑补充:
# "卫宁 HIS 运维" → 使用卫宁健康 HIS [C3]
# "PACS 管理员" → 有影像归档系统 [C3]
# "HL7/FHIR 开发" → 有医疗数据互操作需求 [C3]
# "DRG/DIP 专员" → 涉及医保支付改革 [C3]
# "智慧病房" → 有物联网+护理信息化 [C3]
```

#### 8.4.3 Phase 3 供应商反向搜索

```
# 医疗 IT 核心厂商
WebSearch: "卫宁健康" OR "创业慧康" OR "东华软件" 客户案例 "{公司全称}"
WebSearch: "东软" OR "万达信息" OR "嘉和美康" 签约 OR 中标 "{公司全称}"
WebSearch: "{公司全称}" "智慧医院" OR "电子病历评级" OR "互联互通"

# 医疗设备/影像厂商
WebSearch: "GE 医疗" OR "西门子医疗" OR "飞利浦" 合作 "{公司全称}"
WebSearch: "{公司全称}" PACS OR "医学影像" 供应商 OR 采购

# 政策/评级线索
WebSearch: "{公司全称}" "电子病历评级" OR "互联互通成熟度" OR "智慧医院评审"
WebSearch: "{公司全称}" "三甲" OR "三级医院" OR "等级评审"
WebSearch: "{公司全称}" site:nhc.gov.cn (国家卫健委)
```

#### 8.4.4 行业专属数据源与基准

```
专属数据源:
├── 国家卫健委统计信息中心 (医院信息化调查)
├── CHIMA (中国医院信息管理协会) 年度调查报告
├── 电子病历分级评价结果公示
├── 医院互联互通标准化成熟度测评结果
├── HIT 专家网 (hit180.com) — 医疗信息化资讯
├── HC3i (中国数字医疗网)
└── 丁香园/医脉通 — 行业讨论

IT 预算基准:
├── 医疗业 IT 支出占营收: 3-5%
├── 医疗子领域分化:
│   ├── 三甲综合医院: HIS+EMR+LIS+PACS 全栈 (投入 2000万-2亿/年)
│   ├── 二级医院: HIS+基础 EMR + 区域平台对接 (投入 500万-3000万/年)
│   ├── 社区卫生: 基层卫生信息系统 (区域统建为主)
│   ├── 制药企业: ERP+LIMS+MES+药品追溯 (偏制造业模式)
│   └── 连锁医疗/药店: HIS+连锁管理+互联网医院
├── 政策驱动因素:
│   ├── 电子病历评级要求 (4级以上需结构化 EMR)
│   ├── 互联互通成熟度标准 (四甲/五乙/五甲)
│   ├── DRG/DIP 医保支付改革 (倒逼数据治理)
│   ├── 智慧医院评审标准
│   └── 信息安全等保 (三级甲等医院需等保三级)
└── 数字化成熟度标杆:
    ├── 初级: 基础 HIS + 手写病历 + 纸质流转
    ├── 中级: 结构化 EMR + LIS/PACS + 基础互联互通
    ├── 高级: CDR/数据平台 + AI辅助诊断 + 互联网医院
    └── 标杆: 北京协和, 浙大一院, 华西医院(电子病历7级+)
```

---

### 8.5 专业服务业 | Professional Services

#### 8.5.1 IT 系统参考矩阵

| 系统类别 | 预期系统 | 主流厂商(中国) | 主流厂商(全球) | 搜索优先级 |
|---|---|---|---|---|
| PSA | 专业服务自动化 | 泛微 e-cology(定制), 金蝶 | Certinia (FinancialForce), Kantata (Mavenlink), Workday PSA | ★★★ 必搜 |
| CRM | 客户关系管理 | 销售易, 纷享销客, 六度人和 EC | Salesforce, Microsoft Dynamics 365, HubSpot | ★★★ 必搜 |
| ERP/财务 | 企业资源/财务管理 | 用友, 金蝶, 浪潮 | SAP, Oracle NetSuite, Workday | ★★★ 必搜 |
| KM | 知识管理系统 | 蓝凌, 泛微, 致远 | Confluence, SharePoint, Guru | ★★☆ 建议搜 |
| PM/PPM | 项目管理 | 禅道 ZenTao, Teambition, 飞书项目 | Jira, Monday.com, Asana, MS Project | ★★☆ 建议搜 |
| 协同办公 | 即时通讯/文档协作 | 飞书, 钉钉, 企业微信 | Microsoft 365, Google Workspace, Slack | ★★☆ 建议搜 |
| HCM | 人力资本管理 | 北森, 薪人薪事, 盖雅工场 | Workday HCM, SAP SuccessFactors | ★☆☆ 可选 |
| BI | 商业智能/报表 | 帆软 FineReport, 永洪 | Tableau, Power BI, Qlik | ★☆☆ 可选 |
| T&E | 工时/差旅/费控 | 每刻报销, 汇联易, 分贝通 | SAP Concur, Replicon, Expensify | ★★☆ 建议搜 |
| 行业专用 | 律所/咨询/会计所专用 | Alpha 法律智能, iCourt, 慧算账 | Thomson Reuters, Wolters Kluwer, Clio | ★★☆ 建议搜 |

#### 8.5.2 Phase 2 招聘搜索关键词

```
# 专业服务核心系统
WebSearch: "{公司全称}" 招聘 CRM OR "客户关系" OR "商机管理" OR "Salesforce"
WebSearch: "{公司全称}" 招聘 "知识管理" OR "KM" OR "案例库" OR "方法论库"
WebSearch: "{公司全称}" 招聘 "项目管理" OR "PMO" OR "Jira" OR "项目交付"
WebSearch: "{公司全称}" 招聘 "数据分析" OR "BI" OR "Power BI" OR "Tableau"

# 专业服务子领域适配
# → 管理咨询:
WebSearch: "{公司全称}" 招聘 "知识管理" OR "提案管理" OR "方法论" OR "内部培训"
# → 律所:
WebSearch: "{公司全称}" 招聘 "Alpha" OR "iCourt" OR "案件管理" OR "法律数据库"
# → 会计师事务所:
WebSearch: "{公司全称}" 招聘 "审计系统" OR "底稿管理" OR "财务审计软件"
# → IT 服务/外包:
WebSearch: "{公司全称}" 招聘 "ITSM" OR "ServiceNow" OR "工单系统" OR "SLA管理"

# 反推逻辑补充:
# "Salesforce 管理员" → 使用 Salesforce CRM [C3]
# "Confluence 运维" → 使用 Atlassian 协作套件 [C3]
# "飞书集成开发" → 使用飞书办公套件 [C3]
# "知识图谱工程师" → 有知识管理数字化建设 [C3]
# "ServiceNow 顾问" → 有 ITSM 系统 [C3]
```

#### 8.5.3 Phase 3 供应商反向搜索

```
# 专业服务 IT 厂商
WebSearch: "销售易" OR "纷享销客" OR "六度人和" 客户案例 "{公司全称}"
WebSearch: "泛微" OR "蓝凌" OR "致远" 签约 OR 合作 "{公司全称}"
WebSearch: "北森" OR "薪人薪事" 客户 "{公司全称}"

# 国际 SaaS 厂商
WebSearch: "Salesforce" OR "Microsoft 365" OR "Workday" customer "{公司英文名}"
WebSearch: "{公司全称}" "数字化转型" OR "智慧办公" OR "协同平台"

# 行业专属厂商
# → 律所: WebSearch: "Alpha" OR "iCourt" OR "威科先行" 合作 "{公司全称}"
# → 会计所: WebSearch: "安永" OR "德勤" OR "普华永道" 审计工具 数字化
# → IT 服务: WebSearch: "ServiceNow" OR "BMC Remedy" 客户 "{公司全称}"
```

#### 8.5.4 行业专属数据源与基准

```
专属数据源:
├── 中国管理咨询业年度排名 (管理咨询协会)
├── ALB China (亚洲法律杂志) 律所排名
├── 中国注册会计师协会事务所排名
├── IT 服务企业百强 (中国软件行业协会)
├── Vault Consulting Rankings (全球)
├── The Lawyer / Chambers and Partners (全球律所)
└── 各行业协会会员名录

IT 预算基准:
├── 专业服务业 IT 支出占营收: 4-8%
├── 子领域分化:
│   ├── 管理咨询: CRM+KM+协同 为核心 (人均 IT 成本较高)
│   ├── 律所: 案件管理+法律数据库+文档管理 为核心
│   ├── 会计师事务所: 审计系统+底稿管理+风控 为核心
│   ├── IT 服务/外包: PSA+ITSM+DevOps工具链 为核心
│   └── 设计/广告: DAM+项目管理+创意工具 为核心
├── 关键特征:
│   ├── 人力密集型: 人效和知识复用是 IT 投入核心驱动
│   ├── 项目制运营: 项目管理+资源调度+工时跟踪 三位一体
│   ├── 知识资产: 知识管理系统是长期竞争力基础
│   └── 合伙制决策: IT 投资决策需合伙人共识(采购周期长)
└── 数字化成熟度标杆:
    ├── 初级: 邮件+Excel+文件服务器 (仍有大量中小所)
    ├── 中级: OA+基础 CRM + 项目管理 + 云存储
    ├── 高级: 集成 PSA + CRM + KM + BI + AI 辅助
    └── 标杆: 麦肯锡(自建工具), 金杜(律所数字化), 德勤(全栈AI)
```

---

### 8.6 能源与公用事业 | Energy & Utilities

#### 8.6.1 IT 系统参考矩阵

| 系统类别 | 预期系统 | 主流厂商(中国) | 主流厂商(全球) | 搜索优先级 |
|---|---|---|---|---|
| EMS/SCADA | 能量管理/数据采集与监控 | 南瑞集团, 国电南自, 许继电气 | ABB Ability, Siemens Spectrum, GE Vernova | ★★★ 必搜 |
| DCS | 分散控制系统 | 浙大中控 JX-300, 和利时 HOLLiAS | Honeywell Experion, Emerson DeltaV, Yokogawa | ★★★ 必搜(发电/油气) |
| GIS | 地理信息系统 | 超图 SuperMap, 中地数码 | Esri ArcGIS, Schneider ArcFM | ★★★ 必搜(电网/水务) |
| OMS | 停电管理系统 | 南瑞集团, 积成电子 | Oracle Utilities NMS, GE PowerOn | ★★☆ 建议搜(电网) |
| AMI | 高级计量系统 | 威胜集团, 许继电气, 海兴电力 | Itron, Landis+Gyr, Honeywell Elster | ★★★ 必搜 |
| EAM/APM | 资产管理/资产绩效 | 朗坤智慧, 容知日新 | IBM Maximo, SAP EAM, GE APM, Bentley AssetWise | ★★★ 必搜 |
| ERP | 企业资源计划 | 用友, 远光软件 | SAP IS-U, Oracle Utilities | ★★☆ 建议搜 |
| DERMS | 分布式能源管理 | 南瑞集团, 国网信通 | Schneider DERMS, Siemens, GE | ★☆☆ 可选(新能源) |
| CIS | 客户信息系统 | 朗新科技, 恒华科技 | Oracle Utilities CIS/CC&B, SAP IS-U | ★★☆ 建议搜 |
| PI Historian | 实时数据库 | 庚顿数据 | OSIsoft PI (AVEVA), Honeywell PHD | ★★☆ 建议搜 |
| ADMS | 高级配网管理 | 南瑞集团 | Schneider ADMS, GE Vernova, Oracle Utilities | ★☆☆ 可选(配电) |

#### 8.6.2 Phase 2 招聘搜索关键词

```
# 能源核心系统
WebSearch: "{公司全称}" 招聘 SCADA OR EMS OR DCS OR "调度自动化" OR "能量管理"
WebSearch: "{公司全称}" 招聘 GIS OR "地理信息" OR "配网" OR "管网" OR "线路管理"
WebSearch: "{公司全称}" 招聘 "智能电表" OR AMI OR "用电信息采集" OR "计量自动化"
WebSearch: "{公司全称}" 招聘 EAM OR "资产管理" OR "设备管理" OR "检修管理" OR IBM Maximo
WebSearch: "{公司全称}" 招聘 "PI Historian" OR "实时数据库" OR "数据采集" OR OSIsoft

# 子领域适配
# → 电网:
WebSearch: "{公司全称}" 招聘 "配网自动化" OR ADMS OR "故障定位" OR "馈线自动化"
# → 油气:
WebSearch: "{公司全称}" 招聘 "油藏" OR "管道完整性" OR "PIMS" OR "HSE" OR "测井"
# → 新能源:
WebSearch: "{公司全称}" 招聘 "功率预测" OR "风电" OR "光伏" OR "储能" OR "并网"

# 反推逻辑:
# "南瑞继保运维" → 使用南瑞继电保护/调度系统 [C3]
# "GIS 数据维护" → 有地理信息系统(电网/管网) [C3]
# "PI 管理员" → 使用 OSIsoft PI 实时数据库 [C3]
# "Maximo 开发" → 使用 IBM Maximo 资产管理 [C3]
# "用采系统运维" → 有用电信息采集系统 [C3]
```

#### 8.6.3 Phase 3 供应商反向搜索

```
# 电力/能源 IT 核心厂商
WebSearch: "南瑞集团" OR "国电南自" OR "许继电气" 客户案例 "{公司全称}"
WebSearch: "朗坤智慧" OR "远光软件" OR "朗新科技" 签约 OR 合作 "{公司全称}"
WebSearch: "{公司全称}" "数字电网" OR "数字化变电站" OR "智慧能源"

# 国际能源 IT 厂商
WebSearch: "ABB" OR "Siemens" OR "GE Vernova" OR "Schneider" energy "{公司英文名}"
WebSearch: "Oracle Utilities" OR "SAP IS-U" customer "{公司全称}"

# 政策/示范线索
WebSearch: "{公司全称}" "新型电力系统" OR "源网荷储" OR "虚拟电厂"
WebSearch: "{公司全称}" "智慧矿山" OR "数字油田" OR "智慧水务"
WebSearch: "{公司全称}" site:nea.gov.cn OR site:ndrc.gov.cn (国家能源局/发改委)
```

#### 8.6.4 行业专属数据源与基准

```
专属数据源:
├── 国家能源局 (nea.gov.cn) — 能源政策、项目审批
├── 中电联 (cec.org.cn) — 电力统计年报
├── 中国石油和化学工业联合会 — 油气行业数据
├── 国家电网/南方电网年报 — 电网投资数据
├── 北极星电力网 (bjx.com.cn) — 电力行业资讯
├── 中国能源网 (china5e.com)
└── IHS Markit / Wood Mackenzie — 全球能源数据

IT 预算基准:
├── 能源业 IT 支出占营收: 3-5%
├── 子领域分化:
│   ├── 电网公司: 偏 SCADA/GIS/AMI/OMS (IT占比 2-4%, 但绝对值大)
│   ├── 发电集团: 偏 DCS/EAM/PI Historian (燃煤/燃气/核电)
│   ├── 油气企业: 偏 SCADA/DCS/MES/HSE (勘探+炼化双线)
│   ├── 新能源: 偏 SCADA/功率预测/DERMS (数字化程度较高)
│   └── 水务/燃气: 偏 GIS/SCADA/CIS/AMI (市政公用特征)
├── 监管特征:
│   ├── 电网/油气: 央企主导，IT采购流程长(集采为主)
│   ├── 信创国产化: 能源央企是信创替代重点行业
│   └── 网络安全: 等保三级+关键信息基础设施保护(CIIP)
└── 数字化成熟度标杆:
    ├── 初级: 基础 SCADA + 手工台账
    ├── 中级: 数字化调度 + EAM + GIS
    ├── 高级: 数字电网/数字油田 + AI巡检 + 大数据平台
    └── 标杆: 国家电网(数字新基建), 中石油(梦想云), 金风科技(风电数字化)
```

---

### 8.7 交通运输与物流 | Transportation & Logistics

#### 8.7.1 IT 系统参考矩阵

| 系统类别 | 预期系统 | 主流厂商(中国) | 主流厂商(全球) | 搜索优先级 |
|---|---|---|---|---|
| TMS | 运输管理系统 | 运满满/满帮, 路歌, 福佑卡车, oTMS | SAP TM, Oracle TMS, Blue Yonder TMS, MercuryGate | ★★★ 必搜 |
| WMS | 仓储管理系统 | 富勒 FLUX, 唯智, 京东物流 WMS, 巨沃 | Manhattan WMS, Blue Yonder, Infor WMS, Körber | ★★★ 必搜 |
| OMS | 订单管理系统 | 聚水潭, 旺店通, 管易云, 科箭 | Manhattan OMS, IBM Sterling, Fluent Commerce | ★★★ 必搜 |
| FMS | 车辆/车队管理 | G7物联, 中交兴路, 易流科技 | Geotab, Samsara, Verizon Connect | ★★★ 必搜 |
| YMS | 场站管理系统 | 科箭, 唯智 | 4SIGHT, C3 Solutions, Manhattan YMS | ★☆☆ 可选 |
| 路径优化 | 配送路径/调度 | 地图供应商(高德/百度), 极智嘉 | Google OR Tools, ORTEC, Descartes | ★★☆ 建议搜 |
| Track & Trace | 全程追踪 | 中远海控 SYNCON, 顺丰丰溯 | project44, FourKites, Shippeo | ★★☆ 建议搜 |
| 关务系统 | 报关/清关 | 云关通, 微码邓白氏 | SAP GTS, Descartes Customs, Integration Point | ★☆☆ 可选(跨境) |
| ERP | 企业资源计划 | 用友, 金蝶 | SAP, Oracle NetSuite | ★★☆ 建议搜 |
| CRM | 客户关系管理 | 纷享销客, 销售易 | Salesforce, Microsoft Dynamics | ★☆☆ 可选 |
| BI | 商业智能 | 帆软 FineBI, 永洪 | Power BI, Tableau | ★☆☆ 可选 |

#### 8.7.2 Phase 2 招聘搜索关键词

```
# 物流核心系统
WebSearch: "{公司全称}" 招聘 TMS OR "运输管理" OR "调度系统" OR "运力管理"
WebSearch: "{公司全称}" 招聘 WMS OR "仓储管理" OR "库位管理" OR "拣选系统"
WebSearch: "{公司全称}" 招聘 "车联网" OR "GPS" OR "车队管理" OR G7 OR "物联网"
WebSearch: "{公司全称}" 招聘 "路径优化" OR "配送调度" OR "智能排线" OR "末端配送"
WebSearch: "{公司全称}" 招聘 "AGV" OR "AMR" OR "自动化仓储" OR "分拣机器人"

# 子领域适配
# → 快递快运:
WebSearch: "{公司全称}" 招聘 "中转" OR "分拣" OR "快递面单" OR "末端驿站"
# → 港口航运:
WebSearch: "{公司全称}" 招聘 "TOS" OR "堆场管理" OR "船舶调度" OR "集装箱"
# → 冷链:
WebSearch: "{公司全称}" 招聘 "冷链" OR "温控" OR "冷藏" OR "GSP" OR "温度监控"

# 反推逻辑:
# "满帮运维" → 使用满帮/运满满平台 [C3]
# "G7 数据分析" → 使用 G7 车联网 [C3]
# "WMS 实施" → 有专业仓储管理系统 [C3]
# "自动分拣工程师" → 有自动化分拣线 [C3]
# "报关系统开发" → 有自建/采购关务系统 [C3]
```

#### 8.7.3 Phase 3 供应商反向搜索

```
# 物流科技核心厂商
WebSearch: "满帮" OR "G7物联" OR "中交兴路" OR "易流科技" 客户案例 "{公司全称}"
WebSearch: "科箭" OR "唯智" OR "富勒" 签约 OR 合作 "{公司全称}"
WebSearch: "{公司全称}" "智慧物流" OR "数字化物流" OR "物流科技"

# 国际物流科技
WebSearch: "Blue Yonder" OR "Manhattan" OR "project44" customer "{公司英文名}"
WebSearch: "SAP TM" OR "Oracle TMS" 客户 "{公司全称}"

# 行业线索
WebSearch: "{公司全称}" "无车承运" OR "网络货运" OR "多式联运" OR "5A级物流"
WebSearch: "{公司全称}" "智慧港口" OR "自动化码头" OR "智能仓储"
WebSearch: "{公司全称}" site:mot.gov.cn (交通运输部)
```

#### 8.7.4 行业专属数据源与基准

```
专属数据源:
├── 交通运输部 (mot.gov.cn) — 行业统计、资质审批
├── 中国物流与采购联合会 (chinawuliu.com.cn) — 物流业景气指数
├── 中国交通通信信息中心 — 网络货运平台数据
├── 运联智库 (tucmedia.com) — 物流行业研究
├── 亿豹网 (ebaowang.com) — 快递行业数据
├── 罗戈研究 (logclub.com)
└── Armstrong & Associates — 全球 3PL 排名

IT 预算基准:
├── 交通物流 IT 支出占营收: 2-4%
├── 子领域分化:
│   ├── 快递快运: 偏 分拣自动化+末端网络+面单系统 (IT占比 3-5%)
│   ├── 合同物流/3PL: 偏 TMS+WMS+OMS+客户集成 (IT占比 2-4%)
│   ├── 港口航运: 偏 TOS+自动化码头+航运平台 (单港投资大)
│   ├── 公路货运: 偏 FMS+GPS+调度 (平台型 vs 自营差异大)
│   └── 冷链物流: 偏 温控IoT+WMS+全程追溯 (合规驱动)
├── 关键特征:
│   ├── 利润率低(2-5%): IT投资必须快速见效
│   ├── 平台化趋势: 数字货运平台(满帮/福佑)改变行业格局
│   └── 自动化加速: AGV/AMR/自动分拣是近年投入重点
└── 数字化成熟度标杆:
    ├── 初级: Excel+电话调度+纸质回单
    ├── 中级: TMS/WMS上线+GPS追踪+基础BI
    ├── 高级: 全链路可视+智能调度+自动化仓储
    └── 标杆: 顺丰(全栈自研), 京东物流(仓配一体), 中远海控(航运数字化)
```

---

### 8.8 房地产与建筑 | Real Estate & Construction

#### 8.8.1 IT 系统参考矩阵

| 系统类别 | 预期系统 | 主流厂商(中国) | 主流厂商(全球) | 搜索优先级 |
|---|---|---|---|---|
| BIM | 建筑信息模型 | 广联达 BIMMAKE, 鲁班软件, 品茗科技 | Autodesk Revit, Bentley, Trimble Tekla | ★★★ 必搜 |
| 项目管理 | 工程项目管理 | 广联达, 明源云, 新中大 | Oracle Primavera, Microsoft Project, Procore | ★★★ 必搜 |
| 成本管理 | 造价/成本 | 广联达 GCCP, 斯维尔, 鹏业软件 | Sage Estimating, CostX | ★★★ 必搜 |
| 智慧工地 | 安全/进度监控 | 品茗科技, 广联达, 中建信息 | Oracle Aconex, Procore, PlanGrid | ★★☆ 建议搜 |
| CRM/营销 | 案场/售楼 | 明源云 ERP, 思为科技, 飞渡科技 | Salesforce, HubSpot | ★★★ 必搜(开发商) |
| 物业管理 PMS | 物业服务平台 | 极致科技, 点都软件, 思源 | Yardi, RealPage, MRI Software | ★★★ 必搜(物业) |
| BMS/IBMS | 楼宇自控/智慧建筑 | 特斯联, 美的楼宇, 台达 | Honeywell, Johnson Controls, Siemens | ★★☆ 建议搜 |
| 招采平台 | 招标采购 | 明源云采购, 筑集采, 广联达 | SAP Ariba, Oracle Procurement | ★★☆ 建议搜 |
| ERP | 企业资源计划 | 用友, 金蝶, 明源云 | SAP RE-FX, Oracle | ★★☆ 建议搜 |
| OA/协同 | 办公协同 | 泛微, 致远, 钉钉 | Microsoft 365, Google Workspace | ★☆☆ 可选 |

#### 8.8.2 Phase 2 招聘搜索关键词

```
# 地产/建筑核心系统
WebSearch: "{公司全称}" 招聘 BIM OR Revit OR "建筑信息模型" OR "BIM工程师"
WebSearch: "{公司全称}" 招聘 "工程管理" OR "项目管理" OR Primavera OR "甲方代表"
WebSearch: "{公司全称}" 招聘 "成本管理" OR "造价" OR "广联达" OR "算量"
WebSearch: "{公司全称}" 招聘 "智慧工地" OR "安全监控" OR "塔吊监测" OR "AI巡检"
WebSearch: "{公司全称}" 招聘 "明源" OR "售楼系统" OR "案场管理" OR "客户关系"

# 子领域适配
# → 开发商:
WebSearch: "{公司全称}" 招聘 "投资拓展" OR "营销策划" OR "客户服务" OR "交付管理"
# → 工程建筑:
WebSearch: "{公司全称}" 招聘 "项目部" OR "总承包" OR "施工组织" OR "钢结构"
# → 物业管理:
WebSearch: "{公司全称}" 招聘 "物业系统" OR "社区运营" OR "设施管理" OR "智慧社区"

# 反推逻辑:
# "明源 ERP 管理员" → 使用明源云地产 ERP [C3]
# "BIM 正向设计" → BIM 已深度应用于设计阶段 [C3]
# "广联达造价" → 使用广联达成本管理 [C3]
# "智慧工地项目经理" → 有工地 IoT 监控系统 [C3]
# "Yardi 运维" → 使用 Yardi 物业管理(外资物业) [C3]
```

#### 8.8.3 Phase 3 供应商反向搜索

```
# 地产/建筑 IT 核心厂商
WebSearch: "广联达" OR "明源云" OR "品茗科技" 客户案例 "{公司全称}"
WebSearch: "鲁班软件" OR "斯维尔" OR "新中大" 签约 OR 合作 "{公司全称}"
WebSearch: "{公司全称}" "数字化建造" OR "智慧建造" OR "BIM应用"

# 物业/楼宇科技
WebSearch: "极致科技" OR "点都" OR "特斯联" 客户案例 "{公司全称}"
WebSearch: "Honeywell" OR "Johnson Controls" OR "Siemens" 楼宇 "{公司全称}"

# 行业线索
WebSearch: "{公司全称}" "装配式建筑" OR "绿色建筑" OR "智慧社区" OR "数字孪生"
WebSearch: "{公司全称}" "中国建筑业协会" OR "鲁班奖" OR "国家优质工程"
WebSearch: "{公司全称}" site:mohurd.gov.cn (住建部)
```

#### 8.8.4 行业专属数据源与基准

```
专属数据源:
├── 住建部 (mohurd.gov.cn) — 建筑业统计、资质管理
├── 中国建筑业协会 — 行业排名、鲁班奖
├── 中国房地产协会 — 开发商排名、行业报告
├── 克而瑞 (cricchina.com) — 地产销售排行榜
├── 亿翰智库 — 房企研究
├── 明源云研究院 — 地产数字化案例
└── ENR (Engineering News-Record) — 全球工程承包商排名

IT 预算基准:
├── 房地产与建筑 IT 支出占营收: 1-2.5%
├── 子领域分化:
│   ├── 住宅开发商: 偏 营销CRM+ERP+成本+OA (IT占比 0.5-2%)
│   ├── 商业地产: 偏 BMS/IBMS+物业PMS+租赁系统 (运营驱动)
│   ├── 工程建筑: 偏 BIM+项目管理+成本+智慧工地 (IT占比 1-3%)
│   ├── 物业管理: 偏 PMS+社区APP+设施管理+IoT (IT占比 2-4%)
│   └── 设计院: 偏 CAD/BIM+协同+知识管理 (工具驱动)
├── 行业特征:
│   ├── 传统 IT 投入极低: 行业数字化起步晚(尤其施工环节)
│   ├── 政策驱动: BIM 强制要求(部分省市)、绿建标准、装配式指标
│   ├── 项目制: 每个项目独立采购，难以形成集团统一标准
│   └── 周期敏感: 地产下行期 IT 预算首先被砍
└── 数字化成熟度标杆:
    ├── 初级: CAD+Excel+纸质签字 (仍有大量中小施工企业)
    ├── 中级: 基础 ERP+OA+部分 BIM 应用
    ├── 高级: BIM 全生命周期+智慧工地+数字化营销
    └── 标杆: 中国建筑(智慧建造), 碧桂园(博智林机器人), 万科(万翼科技)
```

---

### 8.9 跨行业通用系统 | Cross-Industry Common Systems

> 以下系统在所有行业中普遍存在，引擎应默认搜索:

| 系统 | 说明 | 搜索必要性 |
|---|---|---|
| OA | 办公自动化(泛微/致远/钉钉/飞书) | 通常已有，确认具体产品即可 |
| 财务系统 | 财务核算(用友/金蝶/SAP FI) | 必有，确认与 ERP 的关系 |
| HR/HCM | 人力资源(北森/SAP SF/Workday) | 大中型企业通常有 |
| 邮件/协同 | Exchange/飞书/钉钉/企业微信 | 确认主协同平台 |
| BI/商业智能 | 帆软 FineBI/FineReport、永洪、Power BI、Tableau、Qlik | 中大型企业普遍有，确认工具和使用范围 |
| CRM | 客户关系管理(Salesforce/销售易/纷享销客) | 有销售团队的企业通常有 |
| 网络安全 | 防火墙/WAF/堡垒机 | 通常不公开，低优先级 |
| 数据库 | Oracle/MySQL/PostgreSQL/达梦/OceanBase | 从招聘 DBA 岗位推断 |

---

*企业情报采集引擎 v1.2 | Enterprise Intelligence Gathering Engine v1.2*
*融合 OSINT 结构化工作流 + Web 采集最佳实践 + 中国市场情报源编目 + 八大行业专属情报规程*
*Fuses OSINT structured workflows + web scraping best practices + China market intelligence source catalog + 8 industry-specific intelligence procedures*
