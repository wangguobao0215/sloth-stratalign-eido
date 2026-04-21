<p align="center">
  <img src="assets/sloth-avatar-round.png" width="120" />
</p>

<h1 align="center">Sloth-StratAlign-Eido</h1>

<p align="center">
  <strong>同辙 · StratAlign — 管理咨询顾问的战略对齐加速器</strong><br/>
  从战略解码到可执行数字化投资组合，内置 AI 原生潜力评分、行业剧本库、顾问级叙事报告。
</p>

<p align="center">
  <img src="assets/qrcode.jpg" width="140" /><br/>
  <sub>扫码关注 <strong>树懒老K</strong> · 获取更多 AI 技能</sub><br/>
  <em>慢一点，深一度</em>
</p>

![Version](https://img.shields.io/badge/version-1.0.0-blue)
![License](https://img.shields.io/badge/license-MIT-green)

---

## 这是什么？

同辙 · StratAlign 是一款面向**管理咨询顾问**的战略对齐加速器。通过行业剧本预填、结构化问卷引擎和 AI 原生潜力评分，将顾问在数字化转型战略项目中的数据收集、分析建模、报告撰写效率提升 3-5 倍。

## 功能概览

### 六大模块
1. **行业检测与顾问配置** (Module 0) — 选择行业自动加载剧本，三种顾问模式（完整/加速/专家）
2. **战略解码** — BSC 四维目标 + 矛盾检测 + 战略假设清单 (If-Then-Because)
3. **瓶颈扫描** — 痛点识别 + L1-L2 能力分层 + 根因 vs 症状分类
4. **AI 原生潜力分诊** — 四维加权评分 + 场景级数据系数 + 敏感性分析
5. **覆盖分析** — IT 映射 + 应用组合健康度四象限 + 能力热力图
6. **投资组合** — ROI 完整计算 (NPV + 回收期) + 三情景分析 + 风险登记册

### v1.0.0 核心升级
- **用户定位聚焦**: 管理咨询顾问效率工具
- **AI 评分模型**: 纯乘法 → 四维加权模型 (规则 25% + 数据 30% + 频率 20% + 实施复杂度 25%)，0-100 分制
- **行业剧本库**: 制造业 / 零售 / 金融服务 / 医疗健康 / 专业服务
- **报告模板**: 填空式 → 叙事结构 + Executive Summary + 风险情景分析
- **方法论增强**: 战略假设清单 + L1-L2 能力分层 + 应用健康度四象限 + ROI 计算模板
- **问卷引擎**: Module 0 行业检测 + 三种顾问模式 + 预填默认值 + 完整性验证

## AI 评分公式 (v1.0)

```
加权原始分 = 0.25×规则显性度 + 0.30×数据模态 + 0.20×决策频率 + 0.25×实施复杂度
归一化得分 = (加权原始分 - 1) / 4 × 100    (0-100 分)
最终得分 = 归一化得分 × 场景数据系数 (0.4 / 0.6 / 0.8 / 1.0)

分级: ≥75 立即启动 | 50-74 短期规划 | 25-49 夯实基础 | <25 暂缓
```

## 文件结构

```
Sloth-StratAlign-Eido/
├── SKILL.md                          # 技能定义 (主入口)
├── references/
│   ├── methodology.md                # BSC + EA + 假设清单 + L1-L2 + 应用健康度 + ROI
│   ├── questionnaire-engine.md       # 六模块问卷引擎 (Module 0-4)
│   ├── ai-native-scoring.md          # 四维加权 AI 评分标准
│   ├── report-template.md            # 叙事诊断报告模板
│   ├── report-template-mini.md       # 迷你诊断卡 (200 词)
│   ├── term-dictionary.md            # 24 术语简化词典
│   ├── examples.md                   # 顾问视角示例
│   └── industry-playbooks/           # 行业剧本库
│       ├── _index.md                 # 剧本索引
│       ├── manufacturing.md          # 制造业
│       ├── retail.md                 # 零售业
│       ├── financial-services.md     # 金融服务
│       ├── healthcare.md             # 医疗健康
│       └── professional-services.md  # 专业服务
├── assets/                           # 品牌资源
├── README.md                         # 本文件
├── README_EN.md                      # English README
├── CHANGELOG.md                      # 变更日志
└── LICENSE                           # MIT
```

## 快速开始

作为顾问启动：

```
> 我有一个制造业客户要做数字化转型诊断，帮我启动 StratAlign。
→ 自动进入 Module 0，加载制造业剧本，选择顾问模式。
```

加速模式：

```
> 用加速模式，制造业，中型企业。
→ 加载预填值，顾问确认/调整，直接进入核心问题。
```

生成报告：

```
> 生成诊断报告
→ 输出含 Executive Summary 的叙事诊断报告 + ROI 计算 + 风险情景
```

## 适用对象

**主要用户**: 管理咨询顾问（战略咨询、数字化转型、IT 战略、企业架构、独立顾问）

**次要用户**: 企业内部 CIO/CDO/战略规划部（在顾问指导下使用）

## 版本

- 当前版本: **1.0.0**
- 完整变更日志见 [CHANGELOG.md](CHANGELOG.md)

## 许可证

MIT License
