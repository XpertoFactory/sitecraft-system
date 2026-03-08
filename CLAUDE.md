# CLAUDE.md — Xperto SiteCraft System

## Project Overview

This repository contains the **Xperto SiteCraft** protocol — an AI-assisted web design framework. The core document is `protocol/xperto-sitecraft.md` (~4,360 lines). It is not code; it is a structured methodology document with prompt templates, role definitions, and deliverable specifications.

## Key Concepts

- **Expert Roles**: The protocol defines specialized AI roles (Brand Strategist, Creative Designer, Content Strategist, UX Expert, etc.) that collaborate through a phased workflow.
- **Phase Gates**: Work flows through Discovery → Conceptualization → Design → Execution → Optimization → Post-Execution. Each phase has defined deliverables and quality gates.
- **Prompt Templates**: Each task has a structured prompt template with sections: CONTEXT, INPUTS, OBJECTIVE, CONSTRAINTS, OUTPUT SPECIFICATION, QUALITY CRITERIA, HANDOFF.
- **Brand DNA Document**: The foundational deliverable — captures core identity, values, personality archetype, and motivations. Feeds all downstream work.
- **Flavor System**: A unique concept for seasonal/thematic visual variations of a site while maintaining brand consistency.
- **Deliverable Templates**: Appendices contain ready-to-use templates (Brand DNA, Voice Guidelines, Style Guide).

## Working Conventions

### When Reviewing the Protocol
- Look for: inconsistencies between role definitions and their prompt templates, missing deliverables, unclear handoffs between phases, gaps in the workflow.
- The protocol should be internally consistent — if a role is defined, it should have corresponding prompt templates. If an output is referenced as an input, it should be defined somewhere.
- Suggestions go in `reviews/suggestions.md` with section references.

### When Editing the Protocol
- Preserve the existing heading hierarchy and formatting conventions.
- Prompt templates follow the pattern: `## [ROLE]:` / `## [PHASE]:` / `## [TASK]:` followed by subsections (CONTEXT, INPUTS, OBJECTIVE, etc.).
- Keep changes focused — one concern per edit.
- Log all changes in `CHANGELOG.md`.

### Niche AI Sites (Astro implementations)
- The `protocol/niche-sites/` directory contains the template system for sector-specific AI educational platforms built with Astro 5 + Svelte 5.
- `production-book.md` is the authoritative technical reference — covers tech stack, file structure, i18n, content collections, interactive tools, Firebase, search, deployment, and quality checklists.
- Key migration guidance: §6.3 (i18n JSON → Content Collections) and §9.3 (vanilla JS → Svelte 5 islands).
- `reviews/suggestions.md` includes an "Existing Niche Sites" section (S1-S5) with improvement recommendations for deployed sites.

### File Locations
- `protocol/xperto-sitecraft.md` — Core protocol (single source of truth for methodology)
- `protocol/niche-sites/production-book.md` — Technical reference for Astro niche sites
- `protocol/niche-sites/site-plan-template.md` — Per-site implementation plan template
- `protocol/niche-sites/initial-setup-template.md` — Site identity & content kickoff
- `protocol/niche-sites/business-docs-template.md` — Non-public business document templates
- `reviews/suggestions.md` — Protocol review notes + existing sites improvement suggestions
- `CHANGELOG.md` — Version history
- `reference/` — External references, examples, benchmarks
- `resources/` — Supporting materials and tools
