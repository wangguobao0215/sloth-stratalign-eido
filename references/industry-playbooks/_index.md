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
| 能源与公用事业 Energy & Utilities | `energy-utilities.md` | 电力/电网、油气、水务、新能源(风电/光伏)、矿业、燃气 |
| 交通运输与物流 Transportation & Logistics | `transportation-logistics.md` | 货运物流、快递快运、航空运输、港口航运、仓储配送、冷链物流 |
| 房地产与建筑 Real Estate & Construction | `real-estate-construction.md` | 住宅开发、商业地产、物业管理、工程建筑、建筑设计 |

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

顾问可基于现有剧本创建自定义版本。详细流程如下：

### 自定义步骤

1. **选择基线剧本**：复制与目标客户最接近的行业剧本作为模板
2. **调整行业特征**：更新行业定义、子行业覆盖范围、核心指标
3. **定制战略主题**：根据客户实际情况修改 5 个预设战略主题，确保映射 BSC 四维
4. **更新痛点库**：替换或补充 10 个常见数字化转型痛点，按对客户的影响程度排序
5. **调整 IT 基准**：修改核心 IT 系统版图及成熟度基准，反映行业真实水平
6. **修订 L1-L2 能力地图**：调整业务能力分解，匹配客户的组织架构
7. **预评分 AI 场景**：基于行业知识为 7 个 AI 应用场景进行 D1-D4 四维预评分
8. **修改 BSC 基准指标**：更新四维基准指标及目标值
9. **设置问卷预填默认值**：为 Module 1-4 各模块配置 YAML 格式的预设默认值
10. **添加顾问贴士**：记录行业特有的咨询注意事项和常见陷阱
11. **保存并加载**：保存为新文件（`custom-industry-name.md`），在 Module 0 中选择"自定义剧本"并指定文件路径

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

## 多业态企业剧本加载策略 | Multi-Business Playbook Loading

当客户企业涉及多个业态（如海尔集团涉及智慧家庭、工业互联网、大健康）时：

### 加载规则

1. **主剧本确定**：按营收占比最高的业务板块确定主行业剧本，作为诊断的主要框架
2. **辅助剧本引用**：对次要业务板块（营收占比 >15%），引用对应行业剧本的以下部分：
   - BSC 基准指标（用于该板块的目标设定）
   - AI 机会目录（用于该板块的 AI 场景识别）
   - IT 基准模板（用于该板块的系统盘点）
3. **跨板块整合**：在 Module 4 投资组合阶段，将各板块的推荐项目合并到统一的投资组合中，标注项目所属板块
4. **报告输出**：诊断报告中按板块分别呈现分析结果，并在 Executive Summary 中给出跨板块协同建议

### 操作示例

```
顾问: 客户是海尔集团，涉及智慧家庭和工业互联网两个板块
系统: 检测到多业态企业。主业务"智慧家庭"加载制造业-家电剧本，
      次要业务"工业互联网"加载制造业-装备制造剧本作为辅助。
      是否确认？或需要调整主次关系？
```

---

*行业剧本库 v1.1.0 | Industry Playbook Library v1.1.0*
