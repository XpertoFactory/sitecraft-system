# Xperto SiteCraft System

A comprehensive AI-assisted web design framework that defines the soul of a website before touching its skin.

## What Is This?

Xperto SiteCraft is a structured methodology for crafting websites using a team of specialized AI expert roles. It covers the full lifecycle — from discovery and brand strategy through design, execution, optimization, and post-launch support.

The protocol defines:
- **Expert roles** (Brand Strategist, Creative Designer, UX Expert, Content Strategist, etc.)
- **Phased workflow** with gate reviews and deliverables
- **Prompt templates** for each role and task
- **Deliverable templates** (Brand DNA Document, Voice Guidelines, Style Guide, etc.)
- **Technical standards** for site architecture, performance, accessibility, and SEO

## Repository Structure

```
sitecraft-system/
├── protocol/                         # Protocol documents
│   ├── xperto-sitecraft.md           # Core protocol (~4,360 lines)
│   └── niche-sites/                  # Niche AI site templates
│       ├── production-book.md        # Full technical reference (Astro, Svelte, Pagefind, Firebase)
│       ├── site-plan-template.md     # Per-site implementation plan template
│       ├── initial-setup-template.md # Site identity & content kickoff template
│       └── business-docs-template.md # Non-public business document templates
├── niche-sites/                      # Working notes & fix scripts for live sites
├── reference/                        # Reference materials, examples, benchmarks
├── resources/                        # Supporting assets and tools
├── reviews/                          # Protocol review notes and suggestions
│   └── suggestions.md                # Running log of improvement ideas
├── CHANGELOG.md                      # Version history of protocol changes
├── CLAUDE.md                         # Project context for Claude Code
├── INSTALL.md                        # Setup and usage guide
└── README.md                         # This file
```

## Protocol Sections

| Section | Coverage |
|---------|----------|
| **Overview** | Philosophy, AI integration approach |
| **Expert Team** | Roles across Conceptualization, Design, and Execution |
| **Workflow Architecture** | Phase gates, deliverables, iteration protocols |
| **Website Structure** | Site architecture, CSS/JS modules, file conventions |
| **Discovery** | Strategic identification of project, brand, audience |
| **Conceptualization** | Brand DNA, Voice Guidelines, Personas, Goals |
| **Design** | Creative concepts, Flavor System, content architecture |
| **Execution** | Content generation, image/video prompts, interactive tools |
| **Optimization** | SEO, analytics, A/B testing, QA, accessibility |
| **Post-Execution** | Maintenance plans, analytics reporting |
| **Community** | Engagement architecture |
| **Personalization** | Adaptive content, cultural context |
| **AI Features** | AI-powered site capabilities |
| **Client Collaboration** | Touchpoints, communication templates |
| **Appendices** | Brand DNA template, Voice Guidelines template, Style Guide template, checklists |

## Influences and Acknowledgments

Several SiteCraft features were inspired by reviewing external AI design skill projects. The concepts were adapted to fit SiteCraft's methodology-first, framework-agnostic architecture.

### From [taste-skill](https://github.com/Leonxlnx/taste-skill) (Design Taste / Anti-Slop Frontend)

Taste-skill is a single-file AI instruction system that overrides default LLM biases when generating frontend code — banning generic patterns and enforcing premium alternatives. Its core thesis is that LLMs suffer from "probability collapse," gravitating toward the statistical mean of their training data.

| Concept Adopted | How It Appears in SiteCraft |
|----------------|----------------------------|
| **Explicit anti-pattern lists with alternatives** | **AI Output Anti-Pattern Catalog** — concrete banned-patterns tables for Visual/CSS, Typography, Layout, Content/Copywriting, and Component/Interaction categories, each explaining *why* a pattern is generic and what to do instead |
| **Parameterized design dials (1–10 scales)** | **Design Calibration Dials** — three scales (Design Variance, Motion Intensity, Visual Density) in the Creative Direction Document that carry forward as binding constraints to the Visual Design System |
| **Detailed motion/animation architecture with performance constraints** | **Motion System expansion** — duration tokens, easing tokens, 5 animation categories with purpose rules, scroll animation guidelines, micro-interaction specs, compositor-only performance constraints, and reduced-motion requirements |
| **AI copywriting cliché bans** | **AI-Generated Content Guardrails** — banned filler words/phrases table, placeholder data policy, and 3-question Authenticity Test (Specificity, Evidence, Voice match) in the Voice Guidelines |
| **Pre-flight self-audit checklist** | **AI Self-Audit Protocol** — 7-item pre-delivery checklist in the meta-template that every expert/agent runs before delivering any output |

### From [ui-ux-pro-max-skill](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill) (UI UX Pro Max)

UI UX Pro Max is a data-driven design intelligence engine with searchable CSV databases, a BM25 search algorithm, and 100 industry-specific reasoning rules. It provides implementation-ready specifications (color palettes, font pairings, chart types, landing page patterns) across 13 technology stacks.

| Concept Adopted | How It Appears in SiteCraft |
|----------------|----------------------------|
| **Named landing page patterns with section flows and conversion strategies** | **Landing Page Pattern Library** — 12 named patterns (Hero-Centric, Storytelling Scroll, Feature Showcase, Social Proof-Led, Funnel, Editorial, Portfolio Gallery, Comparison, FAQ/Resource Hub, Waitlist, Dashboard Landing, Local/Service Area) |
| **Named UI style catalog with CSS signatures and compatibility guidance** | **UI Style Vocabulary** — 10 contemporary styles (Minimalism, Glassmorphism, Neumorphism, Brutalism, Editorial/Print, Bento Grid, Organic/Liquid, Corporate/Enterprise, High Contrast/Bold, Retro/Nostalgic) with best-for and caution notes |
| **Chart type recommendations with library and accessibility guidance** | **Data Visualization Guidelines** — chart type selection table, visualization accessibility rules, chart design tokens with dark mode, and library recommendations |
| **Curated font pairings with mood and industry matching** | **Typography Pairing Principles** — 5 pairing principles and 6 archetypal mood-based pairing references in the Visual Design System |
| **Industry-specific reasoning rules and anti-patterns** | **Industry Context and Conventions** — industry visual profile questionnaire and 8-industry reference table in the Creative Direction Document |
| **Practical CSS/UX implementation rules (cursor, z-index, contrast minimums)** | **Implementation Detail Rules** — cursor rules, z-index scale, text contrast minimums, spacing consistency rules, and border/divider rules in the Style Guide template |

### What Was Not Adopted (and Why)

Both projects contain elements that are valuable in their context but don't fit SiteCraft's role as a framework-agnostic methodology document:

- **BM25 search engine, CSV databases, CLI installer** (ui-ux-pro-max) — SiteCraft is a protocol document, not software; these are architectural choices for a tool
- **React/Next.js/Tailwind-specific rules** (both projects) — SiteCraft is intentionally framework-agnostic; the Web Framework Decision section handles technology selection
- **Specific font bans (Inter, Roboto)** (taste-skill) — too opinionated for a methodology; instead, SiteCraft requires *justification* for any font choice
- **13 technology stack guideline files** (ui-ux-pro-max) — per-framework implementation details are out of scope; SiteCraft provides the design system and lets the chosen framework determine implementation patterns
- **100 product type → style mappings** (ui-ux-pro-max) — too granular for a methodology document; instead, SiteCraft provides the Industry Context framework for creative directors to make informed decisions

## Niche AI Sites

The `protocol/niche-sites/` directory contains a complete template system for building sector-specific AI educational platforms (e.g., AI in Law, AI in Insurance, AI in Business). Each site in the network shares:

- **Astro + Svelte + Vanilla CSS** static site architecture
- **8-language i18n** (EN, ES, FR, DE, IT, PT, ZH, JA)
- **3-flavor design system** with light/dark mode
- **Pagefind search** with multi-language stop-word filtering
- **Firebase** for auth, chat (AI personas via Gemini), likes, and comments
- **AI Learning Program** based on the Smoother methodology

See [INSTALL.md](INSTALL.md) for step-by-step setup instructions.

## Working With This Repo

- **Review the protocol**: Read `protocol/xperto-sitecraft.md` and log observations in `reviews/suggestions.md`
- **Create a niche site**: Start with the templates in `protocol/niche-sites/` (see [INSTALL.md](INSTALL.md))
- **Track changes**: All protocol modifications should be reflected in `CHANGELOG.md`
- **Reference materials**: Drop examples, competitor analyses, or benchmarks into `reference/`
- **Resources**: Store templates, tools, or assets in `resources/`
