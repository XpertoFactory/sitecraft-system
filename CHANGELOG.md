# Changelog

All notable changes to the Xperto SiteCraft protocol are documented here.

## [Unreleased]

## [1.1.0] — 2026-02-17

### Added
- **Content Writer / Copywriter role** (H3) — new Execution Phase Expert responsible for producing all website copy
- **Visual Design System prompt template** (H18) — full template bridging Creative Direction to implementation-ready design tokens, components, and patterns
- **Web Framework Decision section** (NEW) — decision matrix, criteria, workflow integration table, and full prompt template for selecting web architecture
- **UI Framework Decision section** (NEW) — decision matrix for CSS/component approach, integration with Visual Design System and Flavor System, full prompt template
- **Security Audit prompt template** (H24) — replaced `(pending)` stub with full template covering transport security, HTTP headers, input handling, dependency scanning, information disclosure
- **Performance Audit prompt template** (H25) — replaced `(pending)` stub with full template covering Core Web Vitals, page weight, runtime performance, asset optimization, third-party impact, caching
- **Discovery Brief output format** (H13) — structured table defining the format for Phase 1's primary handoff deliverable
- **Phase 3 internal sequencing guidance** (H6) — recommended ordering of Design phase deliverables with dependency notes and parallelization guidance
- **IA collaboration protocol** (H2) — defined Content Strategist / UX Expert co-ownership of Information Architecture with feedback loop and conflict resolution
- **Phase 1 key roles** (H4) — Market / User Research Specialist added to Discovery phase activities
- **Cross-phase note** (H5) — Website Strategy Consultant noted as bridging Conceptualization and Design
- **Content Production Package** (H7) — added to Phase 4 exit deliverables with Content Writer / Copywriter as owner
- **Pre-Launch Checklist expanded** (H28) — added Security, Performance, Analytics, Legal/Compliance, Internationalization, Backup/Recovery, and Brand Consistency categories
- **QA Framework automated testing guidance** (H26) — added regression, smoke, visual regression, load testing, and test environment guidance
- **Iconography Standards** — SVG icons (Lucide or custom) required; emojis prohibited unless client-requested
- **Dependency note** (H14) — Voice Guidelines prompt now documents parallel execution approach for its dependencies

### Changed
- **KPI scope differentiated** (H1) — Business Strategist: business-level KPIs; Website Strategy Consultant: website-specific KPIs
- **Favicon path fixed** (H9) — HTML template corrected from `/assets/favicon-brand.png` to `/assets/logos/favicon-brand.png`
- **Event name standardized** (H10) — `language-change` → `site-language-change` throughout
- **FID replaced with INP** (H11) — Core Web Vitals updated: First Input Delay → Interaction to Next Paint (< 200ms)
- **Role name standardized** (H15) — "Market Research Specialist" → "Market / User Research Specialist" in all references
- **Competitive analysis input standardized** (H16) — references now consistently use "Competitive Analysis Summary (from Business Strategist)"
- **Flavor reference in Creative Concepts** (H17) — changed to "thematic variations (to be reconciled with Flavor System)" acknowledging sequencing
- **EXECUTION header renamed** (H19) — section now titled "CONTENT PRODUCTION" with phase-clarification note
- **Regional Flavors disclaimer** (H20) — added customization-required note framing entries as starting-point examples, not library items
- **Discovery cross-reference** (H12) — added note linking Discovery section to Phase 1 definition in Workflow Architecture
- **Directory Structure expanded** (H8) — added `animations.css`, `flavors/` directory, and 6 missing JS modules to match CSS/JS Architecture tables
- **Image generation prompts expanded** (H21) — Hero Image and Section Image prompts upgraded to full template structure with PHASE, CONTEXT, CONSTRAINTS, QUALITY CRITERIA, HANDOFF
- **Video sub-type prompts expanded** (H22) — Testimonial, Explainer, and Promotional video prompts upgraded to full template structure with role assignments, inputs, constraints, and quality criteria
- **Text content prompts connected** (H23) — all 5 text content generation prompts now include Content Architecture Document and Page-Level Content Brief as inputs
- **QA Framework CONSTRAINTS added** (H26) — added CONSTRAINTS and QUALITY CRITERIA sections to QA prompt
- **Cultural Context Analysis completed** (H27) — added INPUTS, CONSTRAINTS, QUALITY CRITERIA, and HANDOFF sections

## [1.0.0] — 2026-02-17

### Added
- Initial protocol: `protocol/xperto-sitecraft.md`
- Full expert role definitions (Conceptualization, Design, Execution phases)
- Workflow architecture with phase gates
- Website structure and technical standards
- Prompt templates for all roles and tasks
- Deliverable templates (Brand DNA, Voice Guidelines, Style Guide)
- Checklists (Pre-Launch)
- Community Engagement Architecture
- Personalization and Cultural Context frameworks
- AI-Powered Features strategy
- Client Collaboration Protocol
- Video Integration Protocol (Xperto Media)
