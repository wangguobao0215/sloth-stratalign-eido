---
name: Sloth-StratAlign-Eido
version: 0.5.0-beta
description: "Enterprise Digital Transformation Strategic Alignment Engine — layer-by-layer strategy decoding with AI-Native Potential Scoring."
description_zh: "企业数字化转型战略对齐引擎：逐层解码战略为可执行的数字化投资组合，含 AI 原生潜力评分。"
author: sloth-lab
tags:
  - digital-transformation
  - strategic-alignment
  - enterprise-architecture
  - ai-native-scoring
  - balanced-scorecard
---

# 同辙 · StratAlign

> 战略不落地，数字化就是空中楼阁。
> Strategy without execution is a castle in the sky.

## 概述 | Overview

同辙 · StratAlign 是一款企业数字化转型战略对齐引擎。它通过结构化对话，将企业战略逐层解码为可执行的数字化投资组合，同时利用 AI 原生潜力评分矩阵识别最高价值的智能化切入点。

StratAlign is an enterprise digital transformation strategic alignment engine. Through structured dialogue it decodes corporate strategy layer-by-layer into an actionable digital investment portfolio, while leveraging an AI-Native Potential Scoring Matrix to identify the highest-value intelligent entry points.

---

## 核心能力 | Core Capabilities

### 1. 战略解码 | Strategic Decoding (Module 1)
- 愿景与使命澄清 | Vision & mission clarification
- 战略主题提取 | Strategic theme extraction
- BSC 四维目标分解 | BSC four-perspective objective decomposition
  - 财务 Financial / 客户 Customer / 内部流程 Internal Process / 学习与成长 Learning & Growth
- **战略质量验证与矛盾检测** | Strategy quality validation with contradiction detection
  - 自动检测战略目标之间的逻辑矛盾 | Auto-detect logical contradictions between strategic objectives
  - 验证因果链完整性 | Verify causal chain completeness
  - 标记缺失维度 | Flag missing perspectives

### 2. 瓶颈扫描 | Bottleneck Scan (Module 2)
- 业务流程痛点识别 | Business process pain point identification
- 能力差距分析 | Capability gap analysis
- 组织与技术债务评估 | Organizational & technical debt assessment
- 痛点优先级排序 | Pain point prioritization

### 2.5 AI 原生潜力分诊 | AI-Native Potential Triage (Module 2.5)

三维评分矩阵 | 3-Dimension Scoring Matrix:

| 维度 Dimension | 含义 Meaning | 评分 Score |
|---|---|---|
| 规则显性度 Rule Explicitness | 业务规则的文档化与标准化程度 | 1-5 |
| 数据模态 Data Modality | 数据的数字化与结构化水平 | 1-5 |
| 决策频率 Decision Frequency | 决策发生的时间频率 | 1-5 |

**评分公式 | Scoring Formula:**

```
AI 潜力原始分 = 规则显性度 × 数据模态 × 决策频率
Raw AI Potential = Rule Explicitness × Data Modality × Decision Frequency

最终得分 = AI 潜力原始分 × 数据基础设施系数
Final Score = AI Potential × Data Infrastructure Coefficient
```

**数据基础设施系数 | Data Infrastructure Coefficient:**

| 数据状态 Data State | 系数 Coefficient |
|---|---|
| 无数据 No data | 0.3 |
| 分散数据 Scattered data | 0.6 |
| 结构化数据 Structured data | 1.0 |

### 3. 覆盖分析 | Coverage Analysis (Module 3)
- 现有 IT 系统全景扫描 | Current IT landscape scanning
- 业务能力 → IT 能力映射 | Business capability → IT capability mapping
- 覆盖率与空白识别 | Coverage rate & gap identification
- 企业架构 (EA) 对齐度评估 | Enterprise Architecture alignment assessment

### 4. 投资组合 | Investment Portfolio (Module 4)
- 项目优先级排序 | Project prioritization
- 投资回报估算 (ROI) | ROI estimation
- 快赢 / 战略 / 基础 三类分组 | Quick-win / Strategic / Foundation grouping
- 实施路线图生成 | Implementation roadmap generation

---

## 对话流程 | Dialogue Flow

```
[启动 Start]
    │
    ▼
[Module 1] 战略解码 Strategic Decoding
    │  ├─ 愿景/使命/价值观澄清
    │  ├─ 战略主题提取 (3-5 themes)
    │  ├─ BSC 四维目标展开
    │  └─ ⚠️ 矛盾检测 Contradiction Detection
    │
    ▼
[Module 2] 瓶颈扫描 Bottleneck Scan
    │  ├─ 业务流程痛点 (按部门)
    │  ├─ 能力差距热力图
    │  └─ 技术/组织债务评估
    │
    ▼
[Module 2.5] AI 原生潜力分诊 AI-Native Triage
    │  ├─ 三维评分 (规则×数据×频率)
    │  ├─ 数据基础设施系数修正
    │  └─ 场景排序 & Top-N 推荐
    │
    ▼
[Module 3] 覆盖分析 Coverage Analysis
    │  ├─ IT 系统现状盘点
    │  ├─ 业务能力 ↔ IT 能力映射
    │  └─ 覆盖率计算 & 空白标记
    │
    ▼
[Module 4] 投资组合 Investment Portfolio
    │  ├─ 项目分组 (快赢/战略/基础)
    │  ├─ ROI 估算 & 风险评级
    │  └─ 路线图 (6/12/18 月)
    │
    ▼
[输出 Output]
    ├─ 完整诊断报告 Full Diagnostic Report
    └─ 迷你诊断卡 Mini Diagnostic Card
```

### 双向验证 | Bidirectional Verification

- **自顶向下** Top-Down: 战略 → 目标 → AI场景 → IT覆盖 → 投资 (1→2→2.5→3→4)
- **自底向上** Bottom-Up: 投资 → IT覆盖 → 目标 → 战略 (4→3→2→1)

---

## 术语简化 | Term Simplification

本技能使用通俗语言替代专业术语，降低沟通门槛。
This skill uses plain language to replace jargon, lowering communication barriers.

完整词典见 → `references/term-dictionary.md`

| 专业术语 | 通俗表达 | English |
|---|---|---|
| 企业架构 | 企业能力地图 | Enterprise Architecture |
| 平衡计分卡 | 四维战略仪表盘 | Balanced Scorecard |
| 数字孪生 | 数字影子 | Digital Twin |

---

## 引用文件 | Referenced Files

| 文件 File | 说明 Description |
|---|---|
| `references/methodology.md` | BSC 四维指标体系 & EA 映射方法论 |
| `references/questionnaire-engine.md` | 五模块结构化问卷引擎 |
| `references/ai-native-scoring.md` | AI 原生潜力评分详细标准 |
| `references/term-dictionary.md` | 24 术语简化词典 |
| `references/report-template.md` | 完整诊断报告模板 |
| `references/report-template-mini.md` | 迷你诊断卡模板 (200 词) |
| `references/examples.md` | 示例与演示 |

---

## 使用方式 | How to Use

### 快速启动 | Quick Start

```
用户: 我们公司想做数字化转型，不知道从哪里开始。
User: Our company wants to do digital transformation but doesn't know where to start.
```

技能将自动进入 Module 1 战略解码对话。
The skill will automatically enter Module 1 Strategic Decoding dialogue.

### 指定模块 | Specify Module

```
用户: 直接做 AI 场景评估
User: Jump to AI scenario assessment
```

技能将进入 Module 2.5 AI 原生潜力分诊。

### 生成报告 | Generate Report

```
用户: 生成诊断报告
User: Generate diagnostic report
```

完成所有模块后，可生成完整报告或迷你诊断卡。

---

## 适用对象 | Target Audience

- CIO / CTO / CDO（首席数字官）
- 战略规划部门 | Strategic Planning Department
- 数字化转型办公室 | Digital Transformation Office
- IT 规划团队 | IT Planning Team
- 管理咨询顾问 | Management Consultants

---

## 方法论基础 | Methodology Foundation

- **平衡计分卡 (BSC)** — Kaplan & Norton
- **企业架构 (EA)** — TOGAF / Zachman
- **AI 就绪度评估** — 自研三维评分模型
- **投资组合管理** — MoSCoW + RICE 混合框架

详细方法论 → `references/methodology.md`

---

## 版本 | Version

- 当前版本 Current: **0.5.0-beta**
- 阶段 Phase: Phase 1 — 核心引擎 Core Engine
- 变更日志 → `CHANGELOG.md`

---

## 许可 | License

MIT License. 详见项目根目录。
