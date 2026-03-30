# Changelog

All notable changes to the Xperto SiteCraft protocol are documented here.

## [Unreleased]

### Added
- **Social Sharing Architecture** — three-level sharing system (site, page, item) with in-page modal, SVG icons, Web Share API fallback, share data model, platform configuration, accessibility and i18n requirements
- **`share.js` module** — added to Directory Structure, JS Architecture table, and HTML template
- **Share Trigger and Share Modal component patterns** — added to Style Guide template
- **Character & People Imagery Standards** — all character imagery must feature Hispanic/Mediterranean/Latino characters with dark hair in warm-weather appropriate clothing; wardrobe table, prompt enforcement note, and cross-references added to Hero Image, Section Image, all 3 video prompts, and Visual Design System imagery guidelines
- **Light/Dark Theme System** — full architecture section under Website Structure defining toggle UI, persistence strategy (`localStorage` + `prefers-color-scheme`), anti-flash inline script, four-layer CSS token cascade, image/media handling, and accessibility requirements
- **`theme.js` and `theme.css` modules** — added to Directory Structure, CSS/JS Architecture tables, and HTML template
- **Theme Toggle component pattern** — added to Style Guide template with CSS icon-swap, focus states, and reduced-motion support
- **`<meta name="color-scheme">` and `data-theme` attribute** — added to HTML template with anti-flash inline script in `<head>`
- **PWA/mobile meta tags** — added `<meta name="mobile-web-app-capable">` and `<meta name="theme-color">` to HTML template with deprecation warning against the old `apple-mobile-web-app-capable` tag
- **Site Search Implementation guidance** — library comparison table (Pagefind, Lunr, Fuse.js, Algolia), build pipeline requirements, and common 404 troubleshooting note
- **Pre-Launch Checklist additions** — deprecated meta tag check and search index build verification
- **OG Image Specifications** — dimension, format, file size, and safe-zone requirements with per-platform table (Facebook, X, LinkedIn, WhatsApp, Pinterest, Discord/Slack/Telegram)
- **Article/Blog Post meta tag variant** — `og:type=article` with `article:published_time`, `article:modified_time`, `article:author`, `article:section`, `article:tag`
- **Social Meta Tag Fallback Behavior table** — documents which Twitter tags fall back to OG and which must be explicit
- **AI Output Anti-Pattern Catalog** — (inspired by [taste-skill](https://github.com/Leonxlnx/taste-skill)) concrete banned-patterns lists for Visual/CSS, Typography, Layout, Content/Copywriting, and Component/Interaction categories, each with "why it's generic" explanation and recommended alternative; cross-referenced from Creative Direction and Visual Design System prompts
- **Design Calibration Dials** — three parameterized scales (Design Variance, Motion Intensity, Visual Density) added to Creative Direction Document output specification; each dial maps 1–10 to specific design implications; values carry forward as binding constraints to Visual Design System
- **Motion System expansion** — expanded from 4 bullet points to full architecture: duration scale tokens, easing function tokens, 5 animation categories with purpose/performance rules, scroll animation guidelines, micro-interaction specifications per element, performance constraints (compositor-only animation, 60fps target), and comprehensive reduced-motion requirements
- **AI-Generated Content Guardrails** — new section in Voice Guidelines output: banned filler words/phrases table, placeholder/fake data policy, 3-question Authenticity Test (Specificity, Evidence, Voice match); shared content quality constraint note added above all Text Content Generation Prompts
- **AI Self-Audit Protocol** — pre-delivery checklist added to the meta-template: anti-pattern check, Brand DNA alignment, calibration dial compliance, authenticity test, placeholder scan, accessibility verification, distinctiveness check; runs before every deliverable
- **Landing Page Pattern Library** — (inspired by [ui-ux-pro-max-skill](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill)) 12 named page patterns (Hero-Centric, Storytelling Scroll, Feature Showcase, Social Proof-Led, Funnel, Editorial, Portfolio Gallery, Comparison, FAQ/Resource Hub, Waitlist, Dashboard Landing, Local/Service Area) with section flows, best-for guidance, and conversion strategies; cross-referenced from Creative Direction Document
- **UI Style Vocabulary** — 10 named contemporary UI styles (Minimalism, Glassmorphism, Neumorphism, Brutalism, Editorial/Print, Bento Grid, Organic/Liquid, Corporate/Enterprise, High Contrast/Bold, Retro/Nostalgic) with CSS signatures, best-for/caution guidance; Creative Direction must reference by name
- **Data Visualization Guidelines** — chart type selection table (10 data relationships), visualization accessibility rules, chart design token system with dark mode guidance, library recommendations (Chart.js, D3.js, Recharts, Apache ECharts)
- **Typography Pairing Principles** — 5 pairing principles (Contrast, Mood alignment, Hierarchy service, Weight range, Metric compatibility) and 6 archetypal mood-based pairing references added to Visual Design System Typography System section
- **Industry Context and Conventions** — new section (6) in Creative Direction Document output: industry visual profile questionnaire, common visual expectations table for 8 industries (Healthcare, Finance, Luxury, Tech/SaaS, Education, Food & Beverage, Legal/Government, Creative/Agency)
- **Implementation Detail Rules** — added to Style Guide template: cursor rules table, z-index scale system (7 layers), text contrast minimums by text role, spacing consistency rules with touch target sizes, border and divider rules per theme
- **Smooth Scroll & Scroll-Spy** — new guideline section in Visual Design System (Motion & Animation): `scroll-behavior: smooth` with `scroll-padding-top` for fixed nav offset, `IntersectionObserver`-based scroll-spy specification for active nav-link highlighting, `prefers-reduced-motion` fallback; `.active` class added to Navigation CSS pattern; `nav.js` module description updated; HTML template sections given `id` attributes for anchor targets; Content Architecture output now includes in-page anchor navigation with scroll-spy; niche-sites production book Navigation section updated with scroll & navigation behavior requirements
- **Search Stop-Word Filtering** — comprehensive stop-word filtering specification covering all 8 site languages (EN, ES, FR, DE, IT, PT, ZH, JA) with dual integration paths for both PagefindUI (`processTerm`) and Pagefind JS API (pre-filtered query); shared `filterStopWords` utility with `Set`-based lookup; CJK particle handling note; code examples for both API styles in niche-sites production book; Intelligent Search Specification in main protocol updated with multi-language and dual-API requirements; quality checklists in production book and site-plan template updated
- **Niche AI Sites Template System** — four reusable templates for building sector-specific AI educational platforms: `production-book.md` (full technical reference covering Astro + Svelte + Pagefind + Firebase stack, i18n, personas, deployment, quality checklists), `site-plan-template.md` (per-site implementation plan with architecture, collections, phases, verification), `initial-setup-template.md` (site identity, content sections, personas, visual identity kickoff), `business-docs-template.md` (commercialization strategy, business plan, investor pitch templates)
- **Svelte Island Migration Path** (production book §9.3) — criteria for when to upgrade interactive tools from vanilla JS Astro components to Svelte 5 islands, 8-step migration process, i18n prop pattern for Svelte components, rule-of-thumb thresholds
- **Content Collections Migration Path** (production book §6.3) — criteria for when to migrate from i18n JSON to Astro Content Collections, step-by-step extraction process with schema examples, migration priority order (glossary → faq → quick-wins → success-stories → case-studies)
- **§10.7 Evaluations** (production book) — per-module and program-wide evaluations, personalized by participant role/profile
- **Fast Initial Assessment** in Learning Program navigation (production book §6.1) — added as sub-page under Learning Program, after Case Studies
- **Target participant roles** in Learning Program core components (production book §10.1) — roles identified for curriculum, case study, and assessment customization
- **Existing Sites Suggestions** (reviews/suggestions.md) — 5 new improvement recommendations for deployed niche sites: S1 (Svelte island migration), S2 (Content Collections migration), S3 (Pagefind stop-word standardization), S4 (First Steps page), S5 (mobile/desktop nav parity)
- **INSTALL.md** — setup and usage guide covering repository layout, core protocol usage, niche site creation workflow, and Claude Code integration
- **README.md** — updated repository structure to include `protocol/niche-sites/`, `niche-sites/`, and `INSTALL.md`; added Niche AI Sites section describing the shared architecture and template system
- **Card Icon-Title Layout Anti-Pattern** — stacked icon-over-title added to Component & Interaction Anti-Patterns with inline-left alternative; `.card-header` CSS pattern added to Style Guide Cards section enforcing `display: flex; align-items: center; gap` for icon + title pairing
- **Card Icon Layout Runbook** (`reviews/fix-card-icon-layout.md`) — reusable prompt for fixing stacked icon-over-title cards across existing sites; includes priority repo list and per-repo CLAUDE.md update instructions
- **README Runbooks section** — new section documenting reusable fix prompts in `reviews/`
- **YouTube Privacy-Enhanced Embeds** — new Video Embedding Standards section in Video-Web Integration Protocol requiring `youtube-nocookie.com` for all YouTube embeds with `loading="lazy"`, accessible `title`, and responsive container; `video-player.js` description updated; production book §5.5 added
- **Iconography Standards strengthened** — emoji ban made absolute (no context exceptions without explicit client request); Lucide established as primary SVG icon library; inline icon-title placement rule added with cross-reference to Anti-Pattern Catalog; Style Guide template Icon Type changed from `[SVG / Emoji / Icon font]` to `SVG only (Lucide preferred)`; Icon Placement for cards changed from "Above title, centered" to inline-left; production book §5.4 added with same rules

### Changed
- **Production Workflow Phases 3-5** (production book §18) — Phase 3 now includes Content Collections migration, Phase 4 includes Svelte island migration, Phase 5 emphasizes completing collection migration before 3rd+ locale
- **§10.6 Personalization** (production book) — clarified dual name: Fast Initial Assessment / Pre-Evaluación Diagnóstica
- **Visual Design System prompt** — dark mode changed from optional to mandatory first-class deliverable
- **Flavor System prompt** — light/dark theme variants now required for every Flavor
- **Style Guide Color Palette** — restructured with Light/Dark columns for all color tokens
- **Design Tokens methodology** — Theme dimension added alongside Flavor as orthogonal override axis
- **Flavor System Integration CSS** — rewritten with four-layer cascade (Base Light → Dark → Flavor → Flavor+Dark)
- **Pre-Launch Checklist** — added Light/Dark Theme verification section (8 items)
- **`variables.css` description** — updated to reference light/dark token sets
- **Open Graph meta tags** — expanded from 6 to 12 tags: added `og:locale`, `og:locale:alternate`, `og:image:width`, `og:image:height`, `og:image:type`, `og:image:alt`; fixed `og:image` to use absolute URL; removed brand name from `og:title` (redundant with `og:site_name`)
- **Twitter/X Card meta tags** — expanded from 4 to 7 tags: added `twitter:site`, `twitter:creator`, `twitter:image:alt`; fixed `twitter:image` to use absolute URL; added note that `twitter:` prefix remains standard despite X rebrand
- **Share Data Model** — added absolute URL requirement note and OG Image Specifications cross-reference
- **Creative Direction Document** — Recommended Concept section now references UI Style Vocabulary, Landing Page Pattern Library, and Typography Pairing Principles; Industry Context added as section 6; Concept Adaptation Notes renumbered to section 8; new quality criteria for industry context documentation

## [1.2.0] — 2026-02-17

Resolves 39 of the remaining 44 medium/low/additional-observation items from the v1.0.0 review. 5 items (M17, M18, M22, M23, M26) were already resolved in v1.1.0; L2 and AO3 are acceptable as-is.

### Added
- **Phase 5: Post-Execution definition** (AO4) — duration, activities, exit deliverables, and gate criteria added to Workflow Architecture
- **Strategic Foundation Package definition** (M4) — contents, validation method, and consistency-check process documented
- **Collaborative Task Protocol** (M16) — lead role, review role, conflict escalation, and joint attribution guidelines for multi-role prompts
- **Iteration conflict resolution protocol** (M10) — evidence-based resolution process, escalation chain, and iteration cycle limits
- **Retrospective output artifact** (M11) — Phase Retrospective Summary template with owner, format, and feed-forward requirement
- **HANDOFF sections for text content prompts** (M24) — all 5 text generation prompts now specify downstream consumers
- **TBT and TTI metrics** (M27) — added to QA Performance Audit section
- **Community Engagement and Video Integration in Phase 3** (M28+M29) — added as conditional exit deliverables and gate criteria
- **Client Collaboration expansions** (M30) — Scope Change Protocol, Conflict Resolution Framework, and Formal Sign-Off Template
- **CSS custom property mapping and media queries** (L3) — mobile-first breakpoint patterns for all 6 breakpoints
- **Footer accessibility requirements** (L4) — landmark, ARIA labels, legal links, contrast requirements
- **OG and Twitter Card meta tags** (M8) — `og:type`, `og:site_name`, and full Twitter Card markup in HTML template
- **Analytics clarification comment** (M7) — inline GA4 vs. `analytics.js` relationship documented in HTML template
- **i18n requirements per page element** (M12) — table format with translation/localization needs per element
- **WCAG 2.2 acknowledgment** (M9) — note added at first WCAG reference pointing to 2.2 additional criteria
- **Site Persona accessibility expansion** (L9) — screen reader, keyboard, chatbot a11y, and non-visual fallback requirements
- **Brand Essence field** (L13) — one-liner field added to Brand DNA template Differentiators section
- **Error Messages and Empty States in Voice Guidelines** (L14/AO11) — prompt output now requests these explicitly
- **Design Tokens section** (AO5) — token methodology, naming conventions, and platform-agnostic format in Style Guide template
- **Flavor System Integration section** (AO6) — token override mapping, CSS custom property pattern, variant documentation in Style Guide template
- **Missing component patterns** (AO7) — Navigation, Modal, Toast, Dropdown, Tabs, Accordion, Table, Pagination, Breadcrumbs, Loading States added to Style Guide template
- **Discovery Brief template** (AO9a) — full template in Appendix D
- **Target Audience Persona template** (AO9b) — full template in Appendix E
- **QA Report template** (AO9c) — full template in Appendix F
- **Creative Designer ↔ Visual Design Expert boundary** (M3) — conflict resolution protocol between the two roles
- **Contextual Flavor Library workflow note** (M20) — producer, validator, and connection to Flavor System prompt
- **Brand DNA precedence note** (M15) — clarifies Brand DNA as canonical reference when business objectives overlap
- **Directory Structure ↔ Site Map reconciliation** (M5) — `/about/` expanded, `/resources/` added, relationship note added

### Changed
- **Grammar fix** (M1) — "or merely automates" → "nor merely automate"
- **Expert category naming** (M2) — "Execution Phase Experts" → "Execution Experts" for parallel structure
- **Duplicate metaphor removed** (L1) — "soul/skin" phrasing deduplicated from line 5
- **Meta-template INPUTS** (L5) — "(from previous steps)" parenthetical removed to match actual templates
- **Voice Guidelines bold marker** (L6) — unclosed `**` removed from heading
- **Role name "UI Expert"** (L11) — corrected to "User Interface Expert" in User Journey Validation handoff
- **Heading typo** (L12) — "LAYERs" → "LAYERS"
- **Semantic HTML** (M6) — `<div id="site-nav">` → `<nav>`, `<div id="site-footer">` → `<footer>` in HTML template
- **SEO keyword density** (L10) — replaced deprecated "keyword density" with "semantic coverage and topic authority assessment"
- **Web Management Plan phase** (AO10) — `[PHASE]: Execution` → `[PHASE]: Post-Execution`
- **ASSUME removed from meta-template** (M14) — unused constraint type removed for consistency
- **Duplicate Cultural Context heading** (AO2) — merged into single section with transition sentence
- **Flavor System HANDOFF** (M19) — UX Expert and Accessibility Expert added as recipients
- **Flavor System QUALITY CRITERIA** (M21) — WCAG contrast, reduced-motion, font accessibility, and focus state requirements added
- **Market research input** (L7) — vague "available" clause replaced with traceable source reference
- **Website Goals HANDOFF** (L8) — Analytics Architect removed (not an immediate consumer)
- **Other Content stubs** (M25) — marked as "(pending — to be developed per project needs)"
- **Style Guide code fencing** (AO1) — outer fence upgraded to 5 backticks; inner CSS block properly nested
- **Responsive breakpoints** (AO8) — expanded from single 768px breakpoint to all 6 breakpoints with media query examples
- **Discovery Brief input** (M13) — added to Project Identity Card INPUTS

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
