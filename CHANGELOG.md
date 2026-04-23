# Changelog

All notable changes to 深略 · StratAlign will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/).

---

## [1.4.0] - 2026-04-23

### Added
- **3 New Industry Playbooks**: Energy & Utilities (`energy-utilities.md`), Transportation & Logistics (`transportation-logistics.md`), Real Estate & Construction (`real-estate-construction.md`) — each with full 9-section structure
- **3 New Intelligence Procedures** (§8.6-§8.8): IT system reference matrices, Phase 2/3 search keywords, vendor reverse search templates, industry-specific data sources and benchmarks for each new industry
- Industry playbook library expanded from 5 to 8 industries
- `_index.md` updated to v1.1.0 with all 8 industries registered
- Q0.2 industry mapping table and manual fallback list updated for 8 industries
- Q3.1 industry defaults expanded to cover all 8 industries

### Changed
- Intelligence-gathering engine updated to v1.2 (§8.9 cross-industry renumbered)
- Questionnaire engine Q0.2 manual selection list replaces "Technology & Internet" placeholder with 3 real new industries

---

## [1.3.1] - 2026-04-23

### Added
- **5 Industry-Specific Intelligence Procedures** (§8.1-§8.5): Manufacturing, Retail, Financial Services, Healthcare, Professional Services — each with IT system reference matrix, Phase 2 job posting keywords, Phase 3 vendor reverse search, data sources & benchmarks
- **Cross-Industry Common Systems** (§8.6): BI, CRM, OA, Finance, HR/HCM, Email/Collaboration, Network Security, Database
- Q3.1 now auto-switches search keywords based on detected industry

### Changed
- Intelligence-gathering engine updated to v1.1
- Financial Services §8.3: expanded from 6 to 13 system categories (added Trading System/恒生电子, Insurance Core/Guidewire, Payment/Clearing, Regulatory Reporting, API Gateway)
- Healthcare §8.4: added Scheduling and Medical QMS categories
- Professional Services §8.5: added T&E (Time & Expense) category

---

## [1.3.0] - 2026-04-23

### Added
- **Online Intelligence Gathering Protocol**: Mandatory WebSearch for all pre-filled client data
- **Enterprise Intelligence Gathering Engine** (`intelligence-gathering.md` v1.0): Fuses OSINT structured workflows (adapted from danielmiessler/investigation 279-source catalog + 7 workflows) with web scraping best practices (adapted from mindrally/web-scraping) + China market 7-category intelligence source catalog
- **IT System Inventory 5-Phase Workflow** (§2.2): Annual Report Mining → Job Posting Tech Stack Inference → Vendor Partnership Verification → Tech Leadership & Architecture → Technology Fingerprinting
- **4 Search Strategy Patterns**: Landscape Scan, Recency Pulse, Upstream Tracing, Saturation Stop
- **Confidence Rating System**: [C1] HIGH / [C2] MEDIUM / [C3] LOW / [C4] UNKNOWN with upgrade/downgrade rules
- **Q0.1-Q0.3 Mandatory WebSearch**: Company name, industry, employee count auto-detection all require WebSearch

---

## [1.2.0] - 2026-04-22

### Added
- **CLIMB Digital Growth Ladder Model** (`climb-model-digital-growth-ladder.md`): 5-layer progressive maturity model (Connect → Leverage → Integrate → Model → Breakthrough) with stage assessment rubrics
- **Bilingual Welcome Page**: Redesigned Step 1 with dual-language greeting, capability overview, and getting-started guide
- **Client Name Auto-Complete**: Q0.1 now performs WebSearch to resolve informal names to formal registered names
- **Industry Auto-Detection**: Q0.2 uses WebSearch on confirmed name to map to industry playbook
- **CLIMB Model Integration**: BSC causal chain templates, digital foundation reference architecture, consultant tips enhanced with CLIMB insights across all 5 industry playbooks

### Changed
- Manufacturing playbook: Added sub-sector strategic emphasis (装备制造, 电子高科技, 汽车零部件), 5-platform digital foundation reference architecture, 4 causal chain examples, 3 additional consultant tips from CLIMB model
- All industry playbooks: Enhanced with CLIMB-derived content

---

## [1.1.0] - 2026-04-22

### Added
- **Full Bilingual Support (Chinese/English)**: Language selection prompt at skill activation — user chooses Chinese or English before any other interaction
- **Language Configuration Section in SKILL.md**: Comprehensive language rules table defining behavior for interactions, questionnaires, reports, mini cards, welcome pages, AI scoring, playbook pre-fills, and terminology
- **Deliverable Language Selection**: Before generating each major deliverable, engine prompts user to confirm or override output language
- **Language Switch Commands**: `切换英文`/`switch to English`, `切换中文`/`switch to Chinese`, `用英文生成`/`generate in English`, `用中文生成`/`generate in Chinese`
- **Language Handling Instructions in Reference Files**: All reference files now include HTML comments with explicit instructions on how to extract Chinese-only or English-only content based on user's language preference
- **Language Control Section in Questionnaire Engine**: New command group for language switching during questionnaire flow

### Changed
- Core Workflow updated: Language Selection step added before Module 0
- Interaction Principles: "Language Consistency" added as Principle #1
- Quick Start examples updated with bilingual activation flow
- Report Generation flow updated with language confirmation prompt
- All reference file version numbers bumped to 1.1.0

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

*深略 · StratAlign | sloth-stratalign-eido*
