# {SITE_NAME} — Site Plan

> Implementation plan for {domain}.
> Reference: Production Book at `sitecraft-system/protocol/niche-sites/production-book.md`

---

## 1. Overview

**{SITE_NAME}** is an independent educational platform exploring AI's impact on {sector}. Part of the CEMI.ai network of sector-specific AI platforms.

**Core Thesis:**
> "{CORE_THESIS}"

**Key Principles:**
1. Evidence-Based — Every claim backed by sources
2. Practitioner-Focused — Built for working {professionals}
3. Ethically Grounded — Addresses bias, fairness, transparency, accountability
4. Accessible — Clear language, structured learning paths
5. Multilingual — 8 languages (EN, ES, FR, DE, IT, ZH, JA, PT)
6. Continuously Updated — Content reflects latest developments

---

## 2. Tech Stack

| Technology | Purpose | Version |
|-----------|---------|---------|
| Astro | Static site generator | 5.5+ |
| Svelte | Interactive components | 5.0+ |
| Vanilla CSS | Design system (3 flavors, dark mode) | — |
| Firebase | Auth, Firestore, AI SDK (Gemini) | 12.9+ |
| Pagefind | Client-side search | 1.3+ |
| TypeScript | Type safety | 5.7+ |
| GitHub Pages | Hosting + CI/CD | — |
| GA4 | Analytics | — |

---

## 3. Design System

### 3.1 Three-Flavor System

| Token | {FLAVOR_1_NAME} (Default) | {FLAVOR_2_NAME} | {FLAVOR_3_NAME} |
|-------|---------------------------|------------------|------------------|
| `--color-primary` | `{HEX}` | `{HEX}` | `{HEX}` |
| `--color-secondary` | `{HEX}` | `{HEX}` | `{HEX}` |
| `--color-accent` | `{HEX}` | `{HEX}` | `{HEX}` |
| `--font-heading` | {FONT} | {FONT} | {FONT} |
| `--font-body` | {FONT} | {FONT} | {FONT} |
| `--radius-md` | {VALUE} | {VALUE} | {VALUE} |

### 3.2 Dark Mode
- Toggle via `data-theme="dark"` on `<html>`
- Stored in localStorage: `{site-id}-theme`
- Anti-flash script in `<head>`

---

## 4. Domain Mapping

### {Sector} Sub-Sectors
{TABLE_OF_SUB_SECTORS_WITH_DESCRIPTIONS}

### Domain Terminology
| Generic | {Site} Term |
|---------|------------|
| practiceArea | {sectorTerm} |
| sitesTake | {siteName}sTake |
| professionals | {professional term} |
| regulatory bodies | {relevant bodies} |

---

## 5. Site Architecture

### 5.1 Page Inventory

**Per locale: ~{N} pages. With 8 locales: ~{N×8} total.**

```
/                                    Homepage
/explore/
  /explore/new-frontiers/            How AI is changing {sector}
  /explore/ai-impact/               AI impact across sub-sectors
  /explore/challenges/              Challenges and risks
  /explore/opportunities/           Opportunities in AI + {sector}
  /explore/applications/            Practical applications
  /explore/personal-guide/          Interactive exploration route

/learn/
  /learn/intro/                     Intro to AI for {professionals}
  /learn/what-to-do/                Best practices (collection-based)
  /learn/what-not-to-do/            Dangers (collection-based)
  /learn/prompt-engineering/        CRAFT framework + techniques
  /learn/ai-readiness/              Interactive assessment
  /learn/program/                   Learning Program overview
  /learn/program/curriculum/        Program curriculum details
  /learn/program/case-studies/      3 immersive case studies

/practice/
  /practice/first-steps/            Getting started with AI
  /practice/quick-wins/             Filterable quick-win cards
  /practice/prompt-builder/         Interactive CRAFT builder
  /practice/prompt-library/         Searchable prompt collection
  /practice/ai-roadmap/             Interactive adoption roadmap
  /practice/ethics-simulator/       Ethics scenario simulator

/resources/
  /resources/faq/                   FAQ collection
  /resources/glossary/              {Sector} + AI terms
  /resources/success-stories/       AI adoption case studies
  /resources/tool-directory/        AI tools for {sector}
  /resources/newsletter/            Newsletter signup

/opinion/                           Expert opinion articles

/services/
  /services/                        Our Services overview
  /services/ai-suite/               AI Suite for {Sector}
  /services/assessment/             AI Readiness Assessment
  /services/consulting/             Consulting Services
  /services/digital-twins/          Digital Twins
  /services/training/               Personalized Training
  /services/speaking/               Speaking & Keynotes

/about/
  /about/                           About hub
  /about/{site-id}/                 Identity, mission, principles
  /about/team/                      CEMI.ai, personas, curator
  /about/guide/                     Guided tour + sitemap modal
  /about/investors/                 Investment opportunity
  /about/contact/                   Contact form
  /about/sister-sites/              Sister initiatives

/admin/comments/                    Comment moderation (noindex)
/privacy/                           Privacy policy
/terms/                             Terms of service
```

### 5.2 Locale Mirror
- EN: `/path/` (no prefix)
- Other: `/{locale}/path/`
- All 8 locales mirror EN structure

---

## 6. Content Collections

| Collection | Count (per locale) | Schema |
|-----------|-------------------|--------|
| quick-wins | 9-12 | title, description, time, difficulty, sector, aiTool, prompt, tips, cautions, personaTakes, sources, order |
| what-to-do | 10 | title, number, description, howTo, steps, tools, personaTakes, sources, order |
| what-not-to-do | 10 | title, number, description, risk, realExample, mitigation, personaTakes, sources, order |
| faq | 20-30 | title, category, answer, sources, order |
| glossary | 30-100 | term, definition, aka, category, relatedTerms, sources, order |
| success-stories | 5-10 | title, company, sector, summary, takeaway, personaTakes, sources, order |
| case-studies | 3 | title, type, description, subtitle, slug, sector, personaTakes, sources, order |

---

## 7. AI Chat System (Ask {SiteName})

### Personas

| Persona | Voice | Tier | Temp | Color |
|---------|-------|------|------|-------|
| {SiteName} Guide | Balanced, educational | Anonymous | 0.7 | {HEX} |
| {Name} "The Strategist" | Data-driven, measured | Registered | 0.6 | {HEX} |
| {Name} "The Guardian" | Cautious, human-centered | Registered | 0.65 | {HEX} |
| {Name} "The Catalyst" | Bold, innovative | Registered | 0.8 | {HEX} |
| Carlos Miranda Levy | Experienced, strategic | Registered | 0.65 | — |

### Tiers
- Anonymous: 5 msgs/day, default persona only, sessionStorage
- Registered: 25 msgs/day, all personas, Firestore history

---

## 8. Learning Program

### Core Curriculum (6 Modules)

| # | Module | Topics |
|---|--------|--------|
| 1 | {MODULE_1_TITLE} | {TOPICS} |
| 2 | {MODULE_2_TITLE} | {TOPICS} |
| 3 | {MODULE_3_TITLE} | {TOPICS} |
| 4 | {MODULE_4_TITLE} | {TOPICS} |
| 5 | {MODULE_5_TITLE} | {TOPICS} |
| 6 | {MODULE_6_TITLE} | {TOPICS} |

### Specialization Tracks (6)

| Track | Target Audience |
|-------|----------------|
| {TRACK_1} | {AUDIENCE} |
| {TRACK_2} | {AUDIENCE} |
| {TRACK_3} | {AUDIENCE} |
| {TRACK_4} | {AUDIENCE} |
| {TRACK_5} | {AUDIENCE} |
| {TRACK_6} | {AUDIENCE} |

### Case Studies

1. **Real:** {TITLE} — {DESCRIPTION}
2. **Fictional:** {TITLE} — {DESCRIPTION}
3. **Absurd:** {TITLE} — {DESCRIPTION}

### Formats
- Express (1h), Intensive (4h), Professional (8h), Masterful (24h)

### Methodology
- Smoother Methodology (see `/resources/smoother/`)
- Activities: Quiz, Case Study, Role Simulation, Discussion, Project, Reflection

---

## 9. Funnel Strategy

| Page Type | Primary CTA | Secondary CTAs |
|-----------|------------|----------------|
| Explore pages | Learning Program | Quick Wins, AI Readiness |
| Learn pages | Learning Program | Prompt Builder, Ethics Simulator |
| Practice pages | Our Services | Learning Program, AI Roadmap |
| Resources | Learning Program | Prompt Library, Tools Directory |
| Services | Contact Us | Assessment, Training |

---

## 10. Implementation Phases

### Phase 1: Foundation (~1 week)
- [ ] Astro project init with standard config
- [ ] CSS design system (3 flavors × light/dark)
- [ ] i18n system (EN + ES first)
- [ ] Firebase project setup
- [ ] Core components (Navigation, Footer, BaseLayout, Icon)
- [ ] GitHub Pages deployment

### Phase 2: Core Content (~2 weeks)
- [ ] Homepage
- [ ] About section (6 pages)
- [ ] Explore section (6 pages)
- [ ] Learn section (7 pages)
- [ ] Services section (7 pages)

### Phase 3: Practice & Resources (~2 weeks)
- [ ] Practice section (6 pages + interactive tools)
- [ ] Resources section (5 pages)
- [ ] Opinion section (1 page)
- [ ] Content collections (quick-wins, what-to-do, what-not-to-do, faq, glossary)

### Phase 4: Interactive Features (~1 week)
- [ ] Ask {SiteName} chat (Phase 1: UI + Gemini)
- [ ] Ask {SiteName} chat (Phase 2: Auth + Personas + History)
- [ ] Like/Share/Comment system
- [ ] Admin panel

### Phase 5: Expansion (~2 weeks)
- [ ] Expand i18n to all 8 languages
- [ ] Learning Program curriculum
- [ ] Case Studies with Role Simulation
- [ ] Success Stories, Tools Directory content

### Phase 6: Business (~1 week)
- [ ] Commercialization strategy
- [ ] Business plan
- [ ] Investors pitch
- [ ] Investors page

---

## 11. Verification Checklist

- [ ] Build passes with 0 errors
- [ ] All 6 flavor/theme combinations render correctly
- [ ] Language switching for all active locales
- [ ] Search returns relevant results (stop-word filtering active for all site languages — prepositions/articles stripped via `processTerm` or pre-filtered query)
- [ ] All interactive tools complete full flow
- [ ] All CTAs link correctly
- [ ] Dark mode: all elements readable
- [ ] Mobile: fully responsive
- [ ] Firebase: auth, likes, chat functional
- [ ] Lighthouse: Performance > 90, Accessibility > 90

---

## 12. File Inventory (Expected at Full Build)

| Category | Count |
|----------|-------|
| Page routes (per locale) | ~65 |
| Total pages (8 locales) | ~520 |
| Components (Astro + Svelte) | ~30 |
| Library services | ~12 |
| CSS files | ~12 |
| Content collection entries | ~200+ |
| i18n translation files | 8 |
