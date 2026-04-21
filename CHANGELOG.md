# Changelog

All notable changes to 同辙 · StratAlign will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/).

---

## [1.0.0] - 2026-04-21

### Added
- **Consultant-First Positioning**: Entire skill repositioned as a management consultant efficiency tool
- **4D Weighted AI Scoring Model**: Replaced pure multiplication with weighted additive model (Rule 25%, Data 30%, Frequency 20%, Implementation Complexity 25%), normalized to 0-100 scale
- **Implementation Complexity Dimension**: New 4th scoring dimension measuring how complex AI implementation would be for each scenario
- **Per-Scenario Data Coefficient**: Replaced global data infrastructure coefficient with scenario-level assessment (0.4/0.6/0.8/1.0)
- **Sensitivity Analysis**: Tornado diagram concept, break-even analysis for tier boundaries, single-dimension impact analysis
- **Strategy Hypothesis Register**: If-Then-Because format for all BSC causal links, with validation workflow (Untested → In-Test → Validated/Invalidated → Refined)
- **L1-L2 Capability Decomposition**: Three-level business capability model (L0-L3) with industry-specific templates and capability heat map
- **Application Portfolio Health Quadrant**: Two-axis model (Business Value × Technical Health) with four quadrants (Strategic Assets / Tolerate / Transform / Eliminate)
- **ROI Calculation Template**: Full 5-year TCO model, benefit quantification, NPV calculation, sensitivity analysis, three-scenario analysis (Optimistic/Base/Pessimistic)
- **Industry Playbook Library**: Five industry playbooks (Manufacturing, Retail, Financial Services, Healthcare, Professional Services) with pre-set strategic themes, pain points, IT baselines, L1-L2 capability maps, AI scenario defaults, BSC benchmarks
- **Module 0 Industry Detection**: Pre-screen industry selection with auto-load playbook, company size, consultant mode selection
- **Three Consultant Modes**: Full Discovery (all questions), Accelerated (~50% fewer, pre-filled), Expert (minimal, data import)
- **Questionnaire Pre-fill Defaults**: Industry-specific defaults for 20+ questions across all modules
- **Completeness Validation**: Report Readiness Score (0-100%) with per-module minimum data requirements
- **Executive Summary**: One-page synthesis (Situation → Finding → Recommendation → Impact) added to report template
- **Narrative Report Structure**: "So What" insight paragraphs after every section, consultant guidance notes throughout
- **Risk Scenario Analysis**: Three scenarios (Best/Base/Worst), risk register with probability × impact matrix, early warning indicators
- **Phase-Gate Roadmap**: Four phases (Foundation → Quick Wins → Strategic → Scale) with Go/No-Go decision criteria

### Changed
- AI scoring scale from 0-125 (multiplication) to 0-100 (weighted additive)
- Score tiers recalibrated: ≥75 Immediate / 50-74 Short-term / 25-49 Foundation First / <25 Defer
- Target audience from mixed (CIO/CDO/consultants/planners) to consultant-primary
- Report template from fill-in-blank to narrative structure with consultant notes
- Questionnaire engine from 5 modules (35 questions) to 6 modules (40+ questions with mode tags)
- Enterprise AI Readiness formula updated with new weighted model
- Org Readiness coefficients adjusted: 0.6/0.8/1.0 (was 0.5/0.7/1.0)
- Examples rewritten from consultant perspective with new model calculations

---

## [0.5.0-beta] - 2026-04-17

### Added
- **AI-Native Scoring Matrix**: Three-dimension scoring model (Rule Explicitness, Data Modality, Decision Frequency) with Data Infrastructure Coefficient for quantitative AI potential assessment
- **Questionnaire Engine**: Five-module structured dialogue questionnaire (Strategic Decoding, Bottleneck Scan, AI Triage, Coverage Analysis, Investment Portfolio) with 35+ guided questions
- **Methodology Documentation**: BSC four-perspective indicator system with 20 measurable indicators; Enterprise Architecture (EA) mapping methodology with business-to-IT capability mapping; bidirectional verification method (top-down and bottom-up)
- **Term Simplification Dictionary**: 24-term dictionary mapping technical jargon to plain-language Chinese equivalents across four categories (Strategy, IT, AI, Finance)
- **Mini Diagnostic Card**: 200-word condensed diagnostic format with one-line diagnosis, top bottlenecks, top AI opportunities with scores, and recommended first action
- **Strategy Quality Validation**: Contradiction detection between strategic objectives with causal chain completeness verification
- **Enhanced Report Template**: Added AI scoring results section, contradiction detection results, and ROI estimation summary
- **Worked Examples**: Three fully scored AI scenarios (manufacturing quality inspection, financial reporting, customer service) with detailed rationale
- **Scoring Aggregation**: Multi-scenario ranking with tiered recommendations (Immediate Priority / Short-term / Mid-term / Defer)
- **Enterprise AI Readiness Score**: Composite scoring formula incorporating top scenarios, data infrastructure, and organizational readiness

### Changed
- Report template expanded with AI scoring matrix display and contradiction detection section
- Investment portfolio enhanced with ROI estimates and AI score cross-references
- Dialogue flow extended with deeper questionnaire steps and module control commands
- Examples enhanced with full scoring matrix demonstration, contradiction detection walkthrough, and mini diagnostic card sample

---

## [0.1.0-alpha] - 2026-04-17

### Added
- Initial project skeleton and file structure
- SKILL.md with core concept definition and 5-module framework
- Basic report template with placeholder sections
- Basic examples with enterprise scenario outline
- README (English) and README_zh (Chinese)
- Project metadata and licensing

---

*同辙 · StratAlign | sloth-stratalign-eido*
