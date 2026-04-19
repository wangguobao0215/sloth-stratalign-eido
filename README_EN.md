# Sloth-StratAlign-Eido

![Version](https://img.shields.io/badge/version-0.5.0--beta-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Phase](https://img.shields.io/badge/phase-1%20Core-orange)

**StratAlign** — Enterprise Digital Transformation Strategic Alignment Engine

> Phase 1 (v0.5.0-beta): Core Engine with AI Scoring, Questionnaire Engine, and Methodology

---

## What is StratAlign?

StratAlign is an AI-powered skill that guides enterprises through digital transformation strategic planning. Through structured dialogue, it decodes corporate strategy layer-by-layer into an actionable digital investment portfolio, identifying the highest-value AI opportunities along the way.

## Key Features (Phase 1)

### Core Modules
1. **Strategic Decoding** — Vision/mission clarification, strategic theme extraction, BSC four-perspective objective decomposition
2. **Bottleneck Scan** — Process pain points, capability gaps, technical & organizational debt assessment
3. **AI-Native Potential Triage** — 3-dimension scoring matrix (Rule Explicitness x Data Modality x Decision Frequency) with Data Infrastructure Coefficient
4. **Coverage Analysis** — IT landscape scanning, business-to-IT capability mapping, gap identification
5. **Investment Portfolio** — Project prioritization with ROI estimates, quick-win/strategic/foundation grouping, roadmap generation

### New in Phase 1
- **AI Scoring Matrix**: Quantitative 3-dimension model scoring business scenarios for AI potential (max score: 125)
- **Strategy Contradiction Detection**: Auto-detect logical conflicts between strategic objectives
- **Questionnaire Engine**: 35+ structured questions across 5 modules with progressive dialogue flow
- **Methodology Reference**: BSC indicators (20 measurable KPIs) and EA mapping methodology
- **Term Simplification Dictionary**: 24 technical terms mapped to plain-language equivalents
- **Mini Diagnostic Card**: 200-word condensed diagnostic for quick executive briefing
- **Bidirectional Verification**: Top-down (Strategy to Investment) and Bottom-up (Investment to Strategy) alignment checks

## AI Scoring Formula

```
Final Score = (Rule Explicitness x Data Modality x Decision Frequency) x Data Infrastructure Coefficient

Dimensions (1-5 each):
  - Rule Explicitness: How well-documented are business rules?
  - Data Modality: How digitized and structured is the data?
  - Decision Frequency: How often do decisions occur?

Data Infrastructure Coefficient:
  - 0.3 = No data foundation
  - 0.6 = Scattered data
  - 1.0 = Structured, unified data platform
```

## File Structure

```
phase-1-core/
  SKILL.md                  # Skill definition (main entry point)
  methodology.md            # BSC indicators & EA mapping methodology
  questionnaire-engine.md   # 5-module structured questionnaire
  ai-native-scoring.md      # AI scoring criteria & rubric
  term-dictionary.md        # 24-term simplification dictionary
  report-template.md        # Full diagnostic report template
  report-template-mini.md   # Mini diagnostic card (200 words)
  examples.md               # Worked examples & demonstrations
  README.md                 # Chinese README
  README_EN.md              # This file (English)
  CHANGELOG.md              # Version history
```

## Quick Start

Invoke the skill and describe your company's situation:

```
> Our company wants to do digital transformation but doesn't know where to start.
```

The engine will guide you through each module with structured questions.

To jump to a specific module:
```
> Jump to AI scenario assessment
```

To generate output:
```
> Generate diagnostic report
> Generate mini diagnostic card
```

## Target Audience

- CIO / CTO / CDO (Chief Digital Officer)
- Strategic Planning departments
- Digital Transformation offices
- IT Planning teams
- Management Consultants

## Methodology Foundation

- **Balanced Scorecard (BSC)** — Kaplan & Norton (1992)
- **Enterprise Architecture (EA)** — TOGAF / Zachman
- **AI Readiness Assessment** — Proprietary 3-dimension scoring model
- **Portfolio Management** — MoSCoW + RICE hybrid framework

## Version

- Current: **0.5.0-beta** (Phase 1 — Core Engine)
- See [CHANGELOG.md](CHANGELOG.md) for full version history

## License

MIT License
