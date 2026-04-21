# 行业剧本库索引 | Industry Playbook Library Index

> 为管理咨询顾问提供行业预设模板，加速数字化转型战略诊断。
> Provides industry preset templates for management consultants to accelerate digital transformation strategic diagnosis.

---

## 使用说明 | How to Use

1. 在 Module 0 启动时选择行业，系统自动加载对应剧本
2. 剧本内容作为问卷引擎的预填默认值
3. 顾问可在预填基础上确认、调整或覆盖
4. 如客户行业不在预设列表中，选择最接近的行业或从空白开始

1. Select industry during Module 0 kickoff; the system auto-loads the corresponding playbook
2. Playbook content serves as pre-fill defaults for the questionnaire engine
3. Consultants may confirm, adjust, or override on top of pre-filled values
4. If client industry is not in the preset list, select the closest match or start from blank

---

## 可用剧本 | Available Playbooks

| 行业 Industry | 文件 File | 适用范围 Scope |
|---|---|---|
| 制造业 Manufacturing | `manufacturing.md` | 离散制造、流程制造、汽车零部件、电子制造、装备制造 |
| 零售业 Retail | `retail.md` | 品牌零售、连锁门店、电商、快消品、商超 |
| 金融服务 Financial Services | `financial-services.md` | 银行、保险、证券、基金、金融科技 |
| 医疗健康 Healthcare | `healthcare.md` | 综合医院、专科医院、医疗集团、医药企业 |
| 专业服务 Professional Services | `professional-services.md` | 管理咨询、IT咨询、律所、会计师事务所、工程咨询 |

---

## 剧本结构 | Playbook Structure

每个剧本包含 9 个标准章节:
Each playbook contains 9 standard sections:

| # | 章节 Section | 说明 Description |
|---|---|---|
| 一 | 行业特征 Industry Profile | 行业定义、子行业覆盖、关键特征、核心指标 |
| 二 | 典型战略主题 Strategic Themes | 5 个预设战略主题，映射 BSC 四维 |
| 三 | 痛点库 Pain Point Library | 10 个常见数字化转型痛点，按影响排序 |
| 四 | IT 基准模板 IT Baseline Template | 核心 IT 系统版图及成熟度基准 |
| 五 | L1-L2 能力地图 Capability Map | 业务能力分解 (L1 一级域 + L2 二级能力) |
| 六 | AI 机会目录 AI Opportunity Catalog | 7 个预评分 AI 应用场景 (D1-D4 四维评分) |
| 七 | BSC 基准指标 BSC Benchmarks | 四维基准指标及目标值 |
| 八 | 问卷预填默认值 Questionnaire Pre-fill Defaults | Module 1-4 各模块的预设默认值 (YAML 格式) |
| 九 | 顾问贴士 Consultant Tips | 行业特有的咨询注意事项和常见陷阱 |

---

## 自定义剧本 | Custom Playbooks

顾问可基于现有剧本创建自定义版本:
Consultants can create custom versions based on existing playbooks:

- 复制最接近的行业剧本 — Copy the closest industry playbook
- 调整战略主题、痛点、AI 场景 — Adjust strategic themes, pain points, AI scenarios
- 修改 BSC 基准指标 — Modify BSC benchmark indicators
- 保存为新文件并在 Module 0 中选择 — Save as new file and select in Module 0

### 命名规范 | Naming Convention

- 文件名使用小写英文 + 连字符: `industry-name.md`
- 标题使用中英双语格式: `# 行业名行业剧本 | Industry Name Industry Playbook`
- 版本号遵循语义化版本: `v1.0.0`

### 贡献流程 | Contribution Process

1. 基于现有剧本或模板创建新行业剧本
2. 确保 9 个标准章节齐全
3. 更新本索引文件 `_index.md` 的可用剧本表
4. 经至少一位行业专家审核后合并

---

*行业剧本库 v1.0.0 | Industry Playbook Library v1.0.0*
