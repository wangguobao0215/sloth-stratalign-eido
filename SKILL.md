---
name: Sloth-StratAlign-Eido
version: 1.0.0
description: "Strategic Alignment Accelerator for Management Consultants — from strategy decoding to actionable digital investment portfolio with AI-Native scoring, industry playbooks, and consultant-grade narrative reports."
description_zh: "管理咨询顾问的战略对齐加速器：从战略解码到可执行数字化投资组合，内置 AI 原生潜力评分、行业剧本库、顾问级叙事报告。"
author: sloth-lab
tags:
  - management-consulting
  - digital-transformation
  - strategic-alignment
  - enterprise-architecture
  - ai-native-scoring
  - balanced-scorecard
  - industry-playbook
---

# 同辙 · StratAlign

> <p align="center"><img src="https://raw.githubusercontent.com/wangguobao0215/Sloth-StratAlign-Eido/main/assets/qrcode.jpg" width="80" /><br/><sub>扫码关注 <b>树懒老K</b> · 获取更多 AI 技能</sub><br/><i>慢一点，深一度</i></p>
>
> 让顾问从"收集数据"中解放出来，聚焦在"产出洞察"上。
> Free consultants from data collection — focus on generating insights.

## 概述 | Overview

同辙 · StratAlign 是一款面向**管理咨询顾问**的战略对齐加速器。它通过行业剧本预填、结构化问卷引擎和 AI 原生潜力评分，将顾问在数字化转型战略项目中的数据收集、分析建模、报告撰写效率提升 3-5 倍。

StratAlign is a **strategic alignment accelerator for management consultants**. Through industry playbook pre-fills, a structured questionnaire engine, and AI-Native Potential Scoring, it boosts consultant efficiency 3-5x in data collection, analytical modeling, and report writing for digital transformation strategy engagements.

### 核心价值主张 | Core Value Proposition

| 传统方式 Traditional | 使用 StratAlign | 效率提升 |
|---|---|---|
| 2-3 周收集客户数据 | 行业剧本预填 + 加速模式，1-2 天完成 | 5-10x |
| 手工构建 BSC 与因果链 | 自动矛盾检测 + 假设清单生成 | 3-5x |
| Excel 手算 AI 场景评分 | 四维加权模型 + 敏感性分析自动计算 | 10x |
| 2-3 周撰写诊断报告 | 叙事模板 + 自动 ROI 计算，2-3 天出稿 | 5x |

---

## 目标用户 | Target Audience

**主要用户**: 管理咨询顾问（初级顾问到合伙人均适用）

- 战略咨询顾问 | Strategy Consultants
- 数字化转型顾问 | Digital Transformation Consultants
- IT 战略咨询师 | IT Strategy Advisors
- 企业架构咨询师 | Enterprise Architecture Consultants
- 独立顾问 / 精品咨询公司 | Independent / Boutique Consultants

**次要用户**: 企业内部数字化转型负责人（CIO/CDO/战略规划部）可在顾问指导下使用。

---

## 顾问三种工作模式 | Three Consultant Modes

| 模式 Mode | 场景 When to Use | 问卷量 Questions | 预填 Pre-fill |
|---|---|---|---|
| **完整发现** Full Discovery | 首次接触新客户，无现有资料 | 全部 (~40 题) | 行业默认值可参考 |
| **加速模式** Accelerated | 有行业经验或部分客户资料 | ~50% (~20 题) | 行业剧本预填，顾问确认/调整 |
| **专家模式** Expert | 顾问已有完整客户数据 | 最少 (~12 题必答) | 顾问直接导入数据，引擎验证完整性 |

---

## 核心工作流 | Core Workflow

```
[Module 0] 行业检测与顾问配置 Industry Detection & Setup
    │  ├─ 选择行业 → 自动加载行业剧本
    │  ├─ 选择公司规模
    │  ├─ 选择顾问模式 (完整/加速/专家)
    │  └─ 导入客户资料 (可选)
    │
    ▼
[Module 1] 战略解码 Strategic Decoding
    │  ├─ 愿景/使命/价值观澄清
    │  ├─ 战略主题提取 (3-5 themes)
    │  ├─ BSC 四维目标展开
    │  ├─ ⚠️ 矛盾检测 Contradiction Detection
    │  └─ 🆕 战略假设清单 Strategy Hypothesis Register (If-Then-Because)
    │
    ▼
[Module 2] 瓶颈扫描 Bottleneck Scan
    │  ├─ 业务流程痛点 (按部门)
    │  ├─ 能力差距分析 (L1-L2 能力分层)
    │  ├─ 技术/组织债务评估
    │  └─ 🆕 根因 vs 症状分类 Root Cause vs Symptom
    │
    ▼
[Module 2.5] AI 原生潜力分诊 AI-Native Triage
    │  ├─ 🆕 四维加权评分 (规则×数据×频率×实施复杂度)
    │  ├─ 🆕 场景级数据系数 (替代全局系数)
    │  ├─ 🆕 敏感性分析 Sensitivity Analysis
    │  └─ 场景排序 & Top-N 推荐
    │
    ▼
[Module 3] 覆盖分析 Coverage Analysis
    │  ├─ IT 系统现状盘点
    │  ├─ 🆕 L1-L2 能力热力图 Capability Heat Map
    │  ├─ 🆕 应用组合健康度四象限 App Portfolio Health Quadrant
    │  └─ 覆盖率计算 & 空白标记
    │
    ▼
[Module 4] 投资组合 Investment Portfolio
    │  ├─ 项目分组 (快赢/战略/基础)
    │  ├─ 🆕 完整 ROI 计算 (成本分解 + 收益量化 + NPV + 回收期)
    │  ├─ 🆕 现金流时间线 Cash Flow Timeline
    │  ├─ 🆕 三情景分析 (乐观/基准/悲观)
    │  └─ 🆕 风险登记册 Risk Register
    │
    ▼
[双向验证 Bidirectional Verification]
    │  ├─ 自顶向下: 战略 → 目标 → AI场景 → IT覆盖 → 投资
    │  └─ 自底向上: 投资 → IT覆盖 → 目标 → 战略
    │
    ▼
[输出 Output]
    ├─ 🆕 顾问级叙事诊断报告 Consultant-Grade Narrative Report
    │    ├─ 高管摘要 Executive Summary (1 页)
    │    ├─ 叙事分析 (每章含 "So What" 洞察段)
    │    ├─ 风险情景分析 Risk Scenario Analysis
    │    └─ 分阶段实施路线图 Phase-Gate Roadmap
    └─ 迷你诊断卡 Mini Diagnostic Card (200 词)
```

---

## AI 原生潜力评分模型 | AI-Native Scoring Model (v1.0)

### 四维加权模型 | Four-Dimension Weighted Model

旧版使用纯乘法 (D1×D2×D3)，一个维度低分会"拖垮"整体。新版采用**加权求和**，各维度贡献均衡。

| 维度 Dimension | 含义 Meaning | 默认权重 Weight |
|---|---|---|
| 规则显性度 Rule Explicitness | 业务规则文档化/标准化程度 | 25% |
| 数据模态 Data Modality | 数据数字化/结构化水平 | 30% |
| 决策频率 Decision Frequency | 决策发生的时间频率 | 20% |
| 🆕 实施复杂度 Implementation Complexity | 实施难度 (5=最容易) | 25% |

**评分公式 | Scoring Formula:**

```
加权原始分 = w1×D1 + w2×D2 + w3×D3 + w4×D4   (范围 1-5)
归一化得分 = (加权原始分 - 1) / 4 × 100          (范围 0-100)
最终得分 = 归一化得分 × 场景数据系数 Cs           (范围 0-100)
```

### 场景级数据系数 | Per-Scenario Data Coefficient

| 数据就绪度 | 系数 Cs | 说明 |
|---|---|---|
| 无相关数据 | 0.4 | 该场景无可用数据 |
| 分散/部分数据 | 0.6 | 有数据但分散或不完整 |
| 已集成但有缺口 | 0.8 | 数据已集成，少量缺口 |
| 完整结构化数据 | 1.0 | 该场景数据完整可用 |

### 分级推荐 | Score Tiers

| 得分 Score | 级别 Tier | 行动 Action |
|---|---|---|
| ≥ 75 | 立即启动 Immediate Priority | 启动 POC / 试点 |
| 50-74 | 短期规划 Short-term Plan | 6 个月内纳入规划 |
| 25-49 | 夯实基础 Foundation First | 先补数据/流程基础 |
| < 25 | 暂缓 Defer | 条件不成熟，持续关注 |

详细评分标准 → `references/ai-native-scoring.md`

---

## 行业剧本库 | Industry Playbook Library

预置 5 大行业剧本，启动时自动加载，大幅减少顾问数据收集时间。

| 行业 Industry | 文件 File | 预设内容 |
|---|---|---|
| 制造业 Manufacturing | `industry-playbooks/manufacturing.md` | 智能制造主题、质检/排产/维护 AI 场景、MES/ERP 基准 |
| 零售业 Retail | `industry-playbooks/retail.md` | 全渠道主题、需求预测/推荐 AI 场景、POS/CDP 基准 |
| 金融服务 Financial Services | `industry-playbooks/financial-services.md` | 数字银行/保险主题、风控/反欺诈 AI 场景 |
| 医疗健康 Healthcare | `industry-playbooks/healthcare.md` | 患者体验主题、临床决策/影像 AI 场景 |
| 专业服务 Professional Services | `industry-playbooks/professional-services.md` | 知识变现主题、智能排班/提案生成 AI 场景 |

顾问可自定义行业剧本或在现有剧本基础上调整。

---

## 方法论基础 | Methodology Foundation

| 方法论 | 应用场景 | 版本亮点 |
|---|---|---|
| 平衡计分卡 (BSC) | 四维战略解码 | 🆕 战略假设清单 (If-Then-Because) |
| 企业架构 (EA) | IT 能力映射 | 🆕 L1-L2 能力分层 + 应用健康度四象限 |
| AI 原生潜力评分 | 场景优先级 | 🆕 四维加权模型 + 敏感性分析 |
| 投资组合管理 | 项目分组与排序 | 🆕 完整 ROI 计算 + 三情景分析 |
| 双向验证 | 战略-投资对齐 | 保持 Top-Down / Bottom-Up 双向 |

详细方法论 → `references/methodology.md`

---

## 术语简化 | Term Simplification

本技能面向顾问，默认使用专业术语。但在面对客户的报告中，建议使用通俗表达：

| 专业术语 | 通俗表达 (面向客户) | English |
|---|---|---|
| 平衡计分卡 | 四维战略仪表盘 | Balanced Scorecard |
| 企业架构 | 企业能力地图 | Enterprise Architecture |
| 数据基础设施系数 | 数据就绪度 | Data Readiness |

完整词典 → `references/term-dictionary.md`

---

## 引用文件 | Referenced Files

| 文件 File | 说明 Description |
|---|---|
| `references/methodology.md` | 方法论：BSC + EA + 假设清单 + L1-L2 分层 + 应用健康度 + ROI 模板 |
| `references/questionnaire-engine.md` | 问卷引擎：Module 0-4 + 顾问模式 + 行业预填 + 完整性验证 |
| `references/ai-native-scoring.md` | AI 评分：四维加权模型 + 敏感性分析 + 顾问指南 |
| `references/report-template.md` | 报告模板：Executive Summary + 叙事结构 + 风险情景 + ROI 过程 |
| `references/term-dictionary.md` | 24 术语简化词典 |
| `references/report-template-mini.md` | 迷你诊断卡模板 (200 词) |
| `references/examples.md` | 顾问视角示例：新模型 + 叙事报告 + ROI 计算 |
| `references/industry-playbooks/_index.md` | 行业剧本库索引 |
| `references/industry-playbooks/manufacturing.md` | 制造业剧本 |
| `references/industry-playbooks/retail.md` | 零售业剧本 |
| `references/industry-playbooks/financial-services.md` | 金融服务业剧本 |
| `references/industry-playbooks/healthcare.md` | 医疗健康剧本 |
| `references/industry-playbooks/professional-services.md` | 专业服务业剧本 |

---

## 使用方式 | How to Use

### 快速启动 | Quick Start (顾问场景)

```
顾问: 我有一个制造业客户要做数字化转型诊断，帮我启动 StratAlign。
→ 自动进入 Module 0，加载制造业剧本，提示选择顾问模式。

Consultant: I have a manufacturing client needing a digital transformation diagnostic.
→ Auto-enter Module 0, load manufacturing playbook, prompt for consultant mode.
```

### 加速模式 | Accelerated Mode

```
顾问: 用加速模式，制造业，中型企业。
→ 加载制造业剧本预填值，展示行业默认 BSC 目标、典型痛点、AI 场景。
→ 顾问确认或调整后，直接进入 Module 1 核心问题。
```

### 生成报告 | Generate Report

```
顾问: 生成诊断报告
→ 检查数据完整性 (Report Readiness Score)
→ 生成含 Executive Summary 的叙事诊断报告
→ 包含 ROI 计算过程、敏感性分析、风险情景
```

### 指定模块 | Jump to Module

```
顾问: 直接做 AI 场景评估
→ 进入 Module 2.5，使用四维加权模型评分
```

---

## 交互原则 | Interaction Principles

1. **顾问视角优先**: 所有输出假设使用者是专业顾问，使用专业术语，提供方法论依据
2. **效率至上**: 能预填就预填，能跳过就跳过，绝不浪费顾问时间
3. **可交付质量**: 每一段输出都应达到"可直接放入客户PPT/报告"的质量标准
4. **透明计算**: 所有评分、ROI 计算必须展示完整过程，便于顾问向客户解释
5. **假设驱动**: 鼓励将所有关键判断表述为可验证的假设 (If-Then-Because)
6. **行业锚定**: 始终以行业剧本为锚点，避免脱离行业语境的泛泛而谈

---

## 版本 | Version

- 当前版本 Current: **1.0.0**
- 升级内容 What's New:
  - 用户定位从混合受众聚焦为管理咨询顾问
  - AI 评分：纯乘法 → 四维加权模型 + 实施复杂度 + 场景级数据系数
  - 新增战略假设清单 (If-Then-Because)
  - 新增 L1-L2 能力分层 + 应用组合健康度四象限
  - 新增完整 ROI 计算模板 (NPV + 敏感性分析 + 三情景)
  - 报告模板：填空式 → 叙事结构 + Executive Summary + 风险情景
  - 新增 5 大行业剧本库
  - 问卷引擎：行业检测前置 + 三种顾问模式 + 预填默认值
- 上一版本 Previous: 0.5.0-beta
- 变更日志 → `CHANGELOG.md`

---

## 许可 | License

MIT License. 详见项目根目录。
