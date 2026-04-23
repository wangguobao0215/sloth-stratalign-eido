---
name: sloth-stratalign-eido
version: 1.4.0
description: "Strategic Alignment Accelerator for Management Consultants — from strategy decoding to actionable digital investment portfolio with AI-Native scoring, industry playbooks, and consultant-grade narrative reports. Use when conducting enterprise digital transformation diagnostics, strategic alignment analysis, AI-native potential scoring, or layer-by-layer strategy decoding."
description_zh: "深略 · 战略对齐 — 管理咨询顾问的战略对齐加速器：从战略解码到可执行数字化投资组合，内置 AI 原生潜力评分、行业剧本库、顾问级叙事报告。"
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

# 深略 · StratAlign

> <p align="center"><img src="https://raw.githubusercontent.com/wangguobao0215/Sloth-StratAlign-Eido/main/assets/qrcode.jpg" width="80" /><br/><sub>扫码关注 <b>树懒老K</b> · 获取更多 AI 技能</sub><br/><i>慢一点，深一度</i></p>
>
> 让顾问从"收集数据"中解放出来，聚焦在"产出洞察"上。
> Free consultants from data collection — focus on generating insights.

---

## 欢迎页面 | Welcome Page

> **重要**: 当用户激活本技能时，引擎必须首先展示以下欢迎页面。欢迎页面**始终使用中英双语**显示，不受后续语言选择影响。
> **IMPORTANT**: When the user activates this skill, the engine MUST first display the following welcome page. The welcome page is **ALWAYS displayed bilingually** (Chinese + English), regardless of subsequent language selection.

引擎激活后，**第一步**展示欢迎页面（始终双语）：

Upon activation, **Step 1** — display the welcome page (always bilingual):

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  深略 · StratAlign — 战略对齐加速器 | Strategic Alignment Accelerator

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  帮助管理咨询顾问快速完成数字化转型战略诊断，从战略解码到可执行投资组合。
  Helps management consultants rapidly complete digital transformation
  strategic diagnostics — from strategy decoding to actionable investment portfolio.

  核心能力 | Core Capabilities:

  1. 行业剧本预填 | Industry Playbook Pre-fill
     → 8 大行业剧本，自动加载行业默认值，减少 50-80% 数据收集时间
     → 8 industry playbooks with auto-loaded defaults, reducing data collection by 50-80%

  2. 结构化问卷引擎 | Structured Questionnaire Engine
     → 六模块渐进式对话，三种顾问模式（完整/加速/专家）
     → Six-module progressive dialogue, three consultant modes (Full/Accelerated/Expert)

  3. AI 原生潜力评分 | AI-Native Potential Scoring
     → 四维加权模型 + 敏感性分析，自动排序 AI 场景优先级
     → 4D weighted model + sensitivity analysis, automatic AI scenario prioritization

  4. 顾问级叙事报告 | Consultant-Grade Narrative Report
     → 含高管摘要、ROI 计算、风险情景分析、分阶段路线图
     → Includes executive summary, ROI calculations, risk scenarios, phased roadmap

  使用向导 | Getting Started:

  Step 2 → 选择交互语言（中文/英文）
            Choose interaction language (Chinese/English)
  Step 3 → 选择成果物语言（中文/中英双语/英文）
            Choose deliverable language (Chinese/Bilingual/English)
  Step 4 → 输入客户名称，系统自动补全正式名称
            Enter client name — system auto-completes formal name
  Step 5 → 系统自动识别行业，确认或修改（支持多业态企业）
            System auto-detects industry — confirm or modify (supports multi-business)
  Step 6 → 系统自动获取企业规模（获取不到则手动输入），选择顾问模式，开始问卷
            System auto-detects company size (manual input if unavailable), select consultant mode, begin

  (本欢迎页即 Step 1 — 始终中英双语展示)
  (This welcome page is Step 1 — always displayed bilingually)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

欢迎页面展示完毕后，引擎立即进入**交互语言选择**。

After the welcome page is displayed, the engine immediately proceeds to **interaction language selection**.

---

## 语言配置 | Language Configuration

> **重要**: 本技能将语言分为两层——**交互语言**（引擎与用户对话的语言）和**成果物语言**（生成报告、问卷清单等可交付物的语言）。两者独立设置。
> **IMPORTANT**: This skill separates language into two layers — **interaction language** (the language the engine uses to converse with the user) and **deliverable language** (the language used for generated reports, questionnaire outputs, etc.). They are configured independently.

### Step 2: 交互语言选择 | Interaction Language Selection

欢迎页面之后，引擎询问交互语言偏好：

After the welcome page, the engine asks for interaction language preference:

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🌐 交互语言 / Interaction Language
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

请选择后续对话使用的语言 / Please select the language for subsequent interactions:

  A. 中文 (Chinese)  — 后续所有对话使用中文
  B. English         — All subsequent interactions in English

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### Step 3: 成果物语言选择 | Deliverable Language Selection

交互语言确认后，引擎询问成果物默认语言。成果物语言支持**三种选项**，含中英双语：

After interaction language is confirmed, the engine asks for the default deliverable language. Deliverable language supports **three options**, including bilingual:

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📄 成果物语言 / Deliverable Language
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

每个阶段生成的成果（问题清单、诊断报告、迷你卡等）使用什么语言？
What language should the deliverables (question lists, reports, mini cards, etc.) use?

  A. 中文             — 成果物全部使用中文
  B. 中英双语 Bilingual — 成果物同时包含中文和英文
  C. English          — All deliverables in English

  提示: 此为默认设置，每次生成成果物时仍可临时切换。
  Note: This is the default. You can override it each time before generating a deliverable.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### 语言规则 | Language Rules

选定语言后，以下规则生效 / Once language is selected, the following rules apply:

| 规则 Rule | 中文模式 Chinese Mode | 英文模式 English Mode |
|---|---|---|
| 引擎交互语言 Interaction Language | 全部使用中文对话 | All conversations in English |
| 问卷展示 Questionnaire Display | 仅展示中文题目和选项 | Display English questions and options only |
| 行业剧本预填 Playbook Pre-fill | 使用中文描述 | Use English descriptions |
| 术语使用 Terminology | 专业中文术语（可附英文缩写） | Professional English terms |

成果物语言遵循用户在 Step 3 的选择，**独立于交互语言**：

Deliverable language follows the user's Step 3 selection, **independent of interaction language**:

| 成果物 Deliverable | 中文 Chinese | 中英双语 Bilingual | 英文 English |
|---|---|---|---|
| 问卷清单 / 答卷 Questionnaire | 中文题目+选项 | 中英对照并列 | English questions+options |
| 诊断报告 Report | 中文叙事、中文标题、中文表头 | 中文为主体 + 英文对照段 | English narrative, headings, tables |
| 迷你诊断卡 Mini Card | 中文版 | 中英双语版 | English version |
| AI 评分说明 AI Scoring | 中文解释 | 中英并列 | English explanations |
| ROI / 路线图 Roadmap | 中文标注 | 双语标注 | English labels |

### 语言切换指令 | Language Switch Commands

| 指令 Command | 说明 Description |
|---|---|
| `切换英文` / `switch to English` | 将交互语言切换为英文 Switch interaction language to English |
| `切换中文` / `switch to Chinese` | 将交互语言切换为中文 Switch interaction language to Chinese |
| `用英文生成` / `generate in English` | 仅本次成果物使用英文（不改变默认设置）This deliverable in English only (default unchanged) |
| `用中文生成` / `generate in Chinese` | 仅本次成果物使用中文（不改变默认设置）This deliverable in Chinese only (default unchanged) |
| `用双语生成` / `generate bilingual` | 仅本次成果物使用中英双语（不改变默认设置）This deliverable bilingual (default unchanged) |
| `成果物语言切换` / `switch deliverable language` | 永久更改成果物默认语言 Permanently change default deliverable language |

### 每阶段成果物语言提示 | Per-Stage Deliverable Language Prompt

在每次生成重要成果物之前，引擎应提示用户确认输出语言：

Before generating each major deliverable, the engine should prompt the user to confirm the output language:

```
📄 本次成果物语言 / Deliverable Language for This Output:
   当前默认 Current default: [中文 / 中英双语 / English]
   如需切换，请输入: "用英文生成" / "用中文生成" / "用双语生成"
   否则按默认语言继续。
   To override: "generate in English" / "generate in Chinese" / "generate bilingual"
   Otherwise, the default language will be used.
```

### 参考文件的语言处理 | Language Handling for Reference Files

本技能的所有参考文件（`references/` 目录）均包含中英双语内容。引擎在读取参考文件时应：

All reference files in this skill (`references/` directory) contain bilingual content. When reading reference files, the engine should:

- **中文模式**: 提取中文内容作为主要内容，忽略英文对照部分
- **英文模式**: 提取英文内容作为主要内容，忽略中文对照部分
- **双语模式**: 同时提取中英文内容，保持对照结构
- **Chinese Mode**: Extract Chinese content as primary, ignore English parallel text
- **English Mode**: Extract English content as primary, ignore Chinese parallel text
- **Bilingual Mode**: Extract both Chinese and English content, maintain parallel structure

---

## 概述 | Overview

深略 · StratAlign 是一款面向**管理咨询顾问**的战略对齐加速器。它通过行业剧本预填、结构化问卷引擎和 AI 原生潜力评分，将顾问在数字化转型战略项目中的数据收集、分析建模、报告撰写效率提升 3-5 倍。

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
[Welcome] 欢迎页面 Welcome Page (始终中英双语 Always Bilingual)
    │  └─ 技能介绍 + 使用向导
    │
    ▼
[Step 2] 交互语言选择 Interaction Language Selection
    │  └─ 中文 (Chinese) / English
    │
    ▼
[Step 3] 成果物语言选择 Deliverable Language Selection
    │  └─ 中文 / 中英双语 Bilingual / English
    │
    ▼
[Module 0] 客户识别与顾问配置 Client Recognition & Setup
    │  ├─ Step 4: 输入客户名称 → 自动补全正式名称 → 用户确认
    │  ├─ Step 5: 自动识别行业 → 用户确认(支持多业态修改) → 加载行业剧本
    │  ├─ 自动获取企业规模 → 用户确认（获取不到则手动选择）
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

预置 8 大行业剧本，启动时自动加载，大幅减少顾问数据收集时间。

| 行业 Industry | 文件 File | 预设内容 |
|---|---|---|
| 制造业 Manufacturing | `industry-playbooks/manufacturing.md` | 智能制造主题、质检/排产/维护 AI 场景、MES/ERP 基准 |
| 零售业 Retail | `industry-playbooks/retail.md` | 全渠道主题、需求预测/推荐 AI 场景、POS/CDP 基准 |
| 金融服务 Financial Services | `industry-playbooks/financial-services.md` | 数字银行/保险主题、风控/反欺诈 AI 场景 |
| 医疗健康 Healthcare | `industry-playbooks/healthcare.md` | 患者体验主题、临床决策/影像 AI 场景 |
| 专业服务 Professional Services | `industry-playbooks/professional-services.md` | 知识变现主题、智能排班/提案生成 AI 场景 |
| 能源与公用事业 Energy & Utilities | `industry-playbooks/energy-utilities.md` | 数字电网/数字油田、预测性维护/负荷预测 AI 场景 |
| 交通运输与物流 Transportation & Logistics | `industry-playbooks/transportation-logistics.md` | 智慧物流主题、路径优化/自动仓储 AI 场景 |
| 房地产与建筑 Real Estate & Construction | `industry-playbooks/real-estate-construction.md` | 智慧建造/BIM主题、安全监控/成本估算 AI 场景 |

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
| `references/intelligence-gathering.md` | 企业情报采集引擎：OSINT 工作流 + Web 采集 + 情报源编目 + 置信度体系 |
| `references/report-template-mini.md` | 迷你诊断卡模板 (200 词) |
| `references/examples.md` | 顾问视角示例：新模型 + 叙事报告 + ROI 计算 |
| `references/industry-playbooks/_index.md` | 行业剧本库索引 |
| `references/industry-playbooks/manufacturing.md` | 制造业剧本 |
| `references/industry-playbooks/retail.md` | 零售业剧本 |
| `references/industry-playbooks/financial-services.md` | 金融服务业剧本 |
| `references/industry-playbooks/healthcare.md` | 医疗健康剧本 |
| `references/industry-playbooks/professional-services.md` | 专业服务业剧本 |
| `references/industry-playbooks/energy-utilities.md` | 能源与公用事业剧本 |
| `references/industry-playbooks/transportation-logistics.md` | 交通运输与物流剧本 |
| `references/industry-playbooks/real-estate-construction.md` | 房地产与建筑剧本 |

---

## 使用方式 | How to Use

### 快速启动 | Quick Start (顾问场景)

```
顾问: 启动 StratAlign，帮我做一个客户的数字化转型诊断。
→ Step 1: 展示双语欢迎页面（技能介绍 + 使用向导）
→ Step 2: 询问交互语言偏好（中文/English）
→ Step 3: 询问成果物语言偏好（中文/中英双语/English）
→ Step 4: 请输入客户名称 → 输入"三一" → 自动补全"三一重工股份有限公司"
   → 确认: "您指的是三一重工股份有限公司？(简称可能有重名，请确认)"
→ Step 5: 自动识别行业"制造业-装备制造" → 用户确认或修改
→ 加载制造业剧本，提示选择企业规模和顾问模式

Consultant: Start StratAlign for a client digital transformation diagnostic.
→ Step 1: Display bilingual welcome page (features + getting started guide)
→ Step 2: Ask interaction language (Chinese/English)
→ Step 3: Ask deliverable language (Chinese/Bilingual/English)
→ Step 4: Enter client name → "Sany" → auto-complete to "Sany Heavy Industry Co., Ltd."
   → Confirm: "Do you mean Sany Heavy Industry Co., Ltd.?"
→ Step 5: Auto-detect industry "Manufacturing - Equipment" → user confirms or modifies
→ Load manufacturing playbook, prompt for company size and consultant mode
```

### 加速模式 | Accelerated Mode

```
顾问: 用加速模式，客户是海尔。
→ 自动补全"海尔智家股份有限公司" → 用户确认
→ 自动识别"制造业-家电" → 用户确认
  (提示: 海尔集团涉及多业态——智慧家庭、工业互联网、大健康，
   是否按"制造业"为主行业？如需调整请告知)
→ 加载制造业剧本预填值，展示行业默认 BSC 目标、典型痛点、AI 场景
→ 顾问确认或调整后，直接进入 Module 1 核心问题
```

### 生成报告 | Generate Report

```
顾问: 生成诊断报告
→ 检查数据完整性 (Report Readiness Score)
→ 提示确认报告输出语言（默认跟随成果物语言设置，可临时切换为中文/双语/英文）
→ 生成含 Executive Summary 的叙事诊断报告
→ 包含 ROI 计算过程、敏感性分析、风险情景

Consultant: Generate diagnostic report
→ Check data completeness (Report Readiness Score)
→ Prompt to confirm report language (default follows deliverable language setting, can override to Chinese/Bilingual/English)
→ Generate narrative diagnostic report with Executive Summary
→ Include ROI calculations, sensitivity analysis, risk scenarios
```

### 指定模块 | Jump to Module

```
顾问: 直接做 AI 场景评估
→ 进入 Module 2.5，使用四维加权模型评分
```

---

## 交互原则 | Interaction Principles

1. **语言一致性 Language Consistency**: 交互语言与成果物语言独立管理；交互严格遵循用户选择的交互语言，成果物遵循用户选择的成果物语言（支持中文/双语/英文三选一）；欢迎页面始终双语
2. **顾问视角优先 Consultant Perspective First**: 所有输出假设使用者是专业顾问，使用专业术语，提供方法论依据
3. **效率至上 Efficiency First**: 能预填就预填，能跳过就跳过，绝不浪费顾问时间
4. **可交付质量 Deliverable Quality**: 每一段输出都应达到"可直接放入客户PPT/报告"的质量标准
5. **透明计算 Transparent Calculation**: 所有评分、ROI 计算必须展示完整过程，便于顾问向客户解释
6. **假设驱动 Hypothesis-Driven**: 鼓励将所有关键判断表述为可验证的假设 (If-Then-Because)
7. **行业锚定 Industry Anchored**: 始终以行业剧本为锚点，避免脱离行业语境的泛泛而谈

---

## 联网情报采集协议 | Online Intelligence Gathering Protocol

> **核心原则**: 预填任何客户相关数据时，引擎**必须优先使用 WebSearch 联网搜索**获取实时数据，**严禁仅凭训练数据臆造**。每条预填信息必须标注数据来源和置信度。
> **Core Principle**: When pre-filling any client data, the engine **MUST prioritize WebSearch** for real-time data. **NEVER fabricate data from training knowledge alone**. Every pre-filled item must be tagged with source and confidence level.

> 本技能内置完整的企业情报采集引擎，融合 OSINT 结构化情报方法论（改编自 danielmiessler 279源编目与分阶段工作流）和 Web 采集最佳实践（改编自 mindrally 爬虫知识库），并扩展了中国市场 7 类情报源编目。
> This skill embeds a full Enterprise Intelligence Gathering Engine, fusing OSINT structured methodology (adapted from danielmiessler 279-source catalog and phased workflows) and web scraping best practices (adapted from mindrally scraping knowledge base), extended with a 7-category China market intelligence source catalog.

**完整方法论详见 → `references/intelligence-gathering.md`**，包含:
- 5 阶段企业全景画像工作流（实体识别→行业定位→规模获取）
- 5 阶段 IT 系统清单情报工作流（年报→招聘→供应商→技术领导力→技术指纹）
- 财务情报工作流 + 竞争情报工作流
- 中国市场 7 类 + 全球 10 类情报源编目
- 4 种搜索策略模式（景观扫描/时效脉冲/上游追溯/饱和停止）
- 数据质量控制（提取规则/去重合并/冲突处理）
- 输出格式规范（预填格式/IT清单格式/搜索过程摘要格式）
- 伦理与合规准则

### 置信度标注体系 | Confidence Rating System

| 等级 Level | 标记 Tag | 判定标准 Criteria |
|---|---|---|
| 高 HIGH | `[C1]` | 多源交叉验证（至少 2 个独立来源互相印证） |
| 中 MEDIUM | `[C2]` | 单一可信来源（年报/官方公告/工商数据等） |
| 低 LOW | `[C3]` | 间接推断（招聘信息推断/行业惯例/非权威来源） |
| 未知 UNKNOWN | `[C4]` | 搜索无结果，仅行业默认值占位 |

### 强制搜索触发点 | Mandatory Search Triggers

| 触发环节 Trigger | 搜索目标 | 搜索规程 (→ intelligence-gathering.md) |
|---|---|---|
| Q0.1 客户名称补全 | 企业正式注册名称 | §2.1 Phase 1: 实体识别 |
| Q0.2 行业识别 | 行业分类、主营业务 | §2.1 Phase 2: 行业定位 |
| Q0.3 员工规模 | 员工人数、企业规模 | §2.1 Phase 3: 企业规模 |
| Q3.1 IT系统清单 | 在用IT系统、技术栈 | **§2.2 完整5阶段工作流（强制）** |
| Q1.4 财务目标 | 营收、利润等 | §2.3: 财务情报工作流 |
| 全模块预填 | 行业趋势、竞品动态 | §2.4 + §4.2 景观扫描 |

### 搜索质量规则 | Search Quality Rules

1. **至少 3 轮搜索**: Q3.1 IT系统清单必须执行至少3轮不同角度的搜索
2. **时效性优先**: 优先使用最近 2 年内的数据，超过 3 年标注 `(⚠️ 数据可能过时)`
3. **多源交叉验证**: 重要结论应有至少 2 个独立来源印证才能标 [C1]
4. **明确标注猜测**: 推测内容必须标注 `[C3] 行业推断`，不得伪装成确认事实
5. **搜索失败透明**: 搜索无结果时如实告知，不得用行业默认值冒充实际数据
6. **WebFetch 深入**: 当 WebSearch 返回高价值页面时，应使用 WebFetch 获取完整内容

### 数据优先级 | Data Priority

```
联网搜索实时数据 [C1/C2] > 客户导入资料 > 行业剧本默认值 > 训练数据 [C4]
```

---

## 版本 | Version

- 当前版本 Current: **1.4.0**
- 升级内容 What's New:
  - 🆕 **3个新行业剧本**: 能源与公用事业(`energy-utilities.md`)、交通运输与物流(`transportation-logistics.md`)、房地产与建筑(`real-estate-construction.md`)，行业剧本库从5个扩展至8个
  - 🆕 **3个新行业情报规程** (`intelligence-gathering.md` §8.6-§8.8): 能源/交通物流/房地产建筑各配行业IT系统参考矩阵、招聘关键词库、供应商反向搜索、专属数据源与基准值
  - ✅ 行业剧本库索引更新至 v1.1.0，情报引擎更新至 v1.2
- v1.3.1 内容:
  - 5大行业专属情报规程、跨行业通用系统参考、Q3.1 行业关键词自动切换
- v1.3.0 内容:
  - 联网情报采集协议、企业情报采集引擎、IT系统5阶段搜索、置信度标注体系
- 上一版本 Previous: 1.3.1
- 历史版本:
  - v1.3.1: 5大行业专属情报规程、跨行业通用系统参考、Q3.1行业关键词自动切换
  - v1.3.0: 联网情报采集协议、OSINT引擎、IT系统5阶段搜索、4搜索策略模式、置信度体系
  - v1.2.0: 双语欢迎页面、语言分层、客户名称补全、行业自动识别、CLIMB 模型集成
  - v1.1.0: AI 四维评分、战略假设清单、L1-L2 能力分层、ROI 模板、行业剧本库
- 变更日志 → `CHANGELOG.md`

---

## 许可 | License

MIT License. 详见项目根目录。
