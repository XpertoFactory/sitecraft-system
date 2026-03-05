# Niche AI Sites — Production Book

> Master reference for building sector-specific AI educational platforms.
> Extends the Sitecraft model (`xperto-sitecraft.md`).
> Based on patterns proven in Lawra.org (Law), Ibizai.io (Business), and Insureversia.com (Insurance).

---

## 1. OVERVIEW

Each niche site is an independent educational platform exploring AI's impact on a specific sector. Sites share a common architecture, tech stack, and feature set while being fully customized for their sector's audience, terminology, visual identity, and content.

**Core Thesis Template:**
> "The {sector} professionals most at risk are not those who will be replaced by AI — they are those who refuse to understand it."

**Site Identity:**
Each site has a curator persona (Carlos Miranda Levy) and 3 AI personas representing different viewpoints (balanced/moderate, skeptical/cautious, innovative/pro-AI).

**Network:**
All sites are sister initiatives under CEMI.ai, cross-linked in footers and About sections.

---

## 2. TECH STACK (Standard)

| Technology | Purpose | Version |
|-----------|---------|---------|
| Astro | Static site generator, file-based routing | 5.5+ |
| Svelte | Interactive component islands | 5.0+ |
| Vanilla CSS | Design system (no Tailwind) | — |
| Firebase | Auth, Firestore, AI SDK (Gemini) | 12.9+ |
| Pagefind | Client-side static search | 1.3+ |
| TypeScript | Type safety | 5.7+ |
| GitHub Pages | Hosting + CI/CD | — |
| Google Analytics 4 | Analytics | — |

### package.json (Standard)

```json
{
  "name": "{site-id}-web",
  "type": "module",
  "version": "1.0.0",
  "description": "{Site Name} — {tagline}",
  "scripts": {
    "dev": "astro dev",
    "start": "astro dev",
    "build": "astro build && npx pagefind --site dist",
    "preview": "astro preview",
    "astro": "astro"
  },
  "dependencies": {
    "@astrojs/sitemap": "^3.7.0",
    "@astrojs/svelte": "^7.0.0",
    "astro": "^5.5.0",
    "firebase": "^12.9.0",
    "svelte": "^5.0.0"
  },
  "devDependencies": {
    "pagefind": "^1.3.0",
    "typescript": "^5.7.0"
  }
}
```

### astro.config.mjs (Standard)

```javascript
import { defineConfig } from 'astro/config';
import svelte from '@astrojs/svelte';
import sitemap from '@astrojs/sitemap';

export default defineConfig({
  site: 'https://{domain}',
  integrations: [svelte(), sitemap()],
  i18n: {
    defaultLocale: 'en',
    locales: ['en', 'es', 'fr', 'de', 'it', 'zh', 'ja', 'pt'],
    routing: {
      prefixDefaultLocale: false,
    },
  },
  output: 'static',
});
```

---

## 3. PROJECT STRUCTURE (Standard)

```
{site-id}-web/
├── public/
│   ├── assets/               # Images, logos, fonts, audio
│   │   ├── logos/
│   │   ├── personas/
│   │   ├── heroes/
│   │   └── og/               # Open Graph images
│   ├── CNAME                 # Custom domain
│   ├── robots.txt
│   └── site.webmanifest
├── src/
│   ├── components/           # Astro + Svelte components
│   │   ├── Ask{SiteName}/    # AI chat widget
│   │   │   ├── Ask{SiteName}.astro
│   │   │   └── ChatWidget.svelte
│   │   ├── Navigation.astro
│   │   ├── Footer.astro
│   │   ├── Icon.astro
│   │   ├── ContactModal.astro
│   │   ├── ShareModal.astro
│   │   ├── FlavorSelector.astro
│   │   ├── LanguageSelector.astro
│   │   ├── FunnelCTA.astro
│   │   ├── PersonaTake.astro
│   │   ├── DifficultyBadge.astro
│   │   ├── QuickWinCard.astro
│   │   ├── {Sector}Tag.astro
│   │   ├── AiReadinessAssessment.astro
│   │   ├── AiRoadmapBuilder.astro
│   │   ├── AiHelpCalculator.astro
│   │   ├── PromptBuilder.astro
│   │   ├── EthicsSimulator.astro
│   │   ├── EnrollmentModal.astro
│   │   ├── FlyerSlideshow.svelte
│   │   ├── LikeButton.svelte
│   │   ├── CopyButton.svelte
│   │   ├── CommentSection.svelte
│   │   ├── UserMenu.svelte
│   │   └── AdminComments.svelte
│   ├── content/              # Markdown content collections
│   │   ├── quick-wins/{locale}/
│   │   ├── what-to-do/{locale}/
│   │   ├── what-not-to-do/{locale}/
│   │   ├── faq/{locale}/
│   │   ├── glossary/{locale}/
│   │   ├── success-stories/{locale}/
│   │   ├── case-studies/{locale}/
│   │   └── config.ts
│   ├── i18n/
│   │   ├── index.ts          # t(), getLocalePath(), Locale type
│   │   ├── en.json
│   │   ├── es.json
│   │   ├── fr.json
│   │   ├── de.json
│   │   ├── it.json
│   │   ├── zh.json
│   │   ├── ja.json
│   │   └── pt.json
│   ├── layouts/
│   │   └── BaseLayout.astro  # Master layout (meta, GA4, styles, shared components)
│   ├── lib/
│   │   ├── firebase.ts       # Lazy-init singleton
│   │   ├── auth.ts           # Google + email auth, anonymous upgrade
│   │   ├── tiers.ts          # Rate limiting (localStorage/Firestore)
│   │   ├── chat.ts           # Gemini streaming via firebase/ai
│   │   ├── chat-persona.ts   # Persona definitions + system prompts
│   │   ├── chat-suggestions.ts # Page-specific suggested questions
│   │   ├── conversations.ts  # Conversation CRUD (registered users)
│   │   ├── likes.ts          # Content like system
│   │   ├── submissions.ts    # Contact form submissions
│   │   ├── comments.ts       # Comment CRUD + moderation
│   │   ├── newsletter.ts     # Newsletter subscriptions
│   │   └── admin.ts          # Admin utilities
│   ├── pages/
│   │   ├── index.astro       # Homepage (EN, default locale)
│   │   ├── explore/
│   │   ├── learn/
│   │   ├── practice/
│   │   ├── resources/
│   │   ├── opinion/
│   │   ├── services/
│   │   ├── about/
│   │   ├── contact/
│   │   ├── admin/comments/
│   │   ├── privacy/
│   │   ├── terms/
│   │   └── {locale}/         # Mirror pages for each non-default locale
│   └── styles/
│       ├── variables.css     # Design tokens
│       ├── layout.css        # Grid, containers
│       ├── typography.css    # Font scales
│       ├── components.css    # UI components
│       ├── utilities.css     # Helper classes
│       ├── animations.css    # Transitions, keyframes
│       ├── fonts.css         # @font-face (default flavor)
│       ├── fonts-flavor2.css # Flavor 2 fonts
│       ├── fonts-flavor3.css # Flavor 3 fonts
│       ├── flavor-2.css      # Flavor 2 overrides
│       ├── flavor-3.css      # Flavor 3 overrides
│       ├── dark-mode.css     # Dark theme overrides
│       └── cjk.css           # Chinese/Japanese typography
├── resources/                # Internal docs (not deployed)
│   ├── initial-setup.md
│   ├── site-plan.md
│   ├── interactive-ai-plan.md
│   ├── commercialization-strategy.md
│   ├── business-plan.md
│   ├── investors-pitch.md
│   ├── smoother/             # Smoother methodology files (copied)
│   ├── logo-prompts.md
│   └── personas-image-prompts.md
├── reference/                # Reference code from sister sites (gitignored)
├── firestore.rules
├── firestore.indexes.json
├── firebase.json
├── .env.example
├── .github/workflows/deploy.yml
├── CLAUDE.md
├── CHANGELOG.md
├── README.md
├── tsconfig.json
└── .gitignore
```

---

## 4. i18n SYSTEM

### Languages (8 locales)

| Code | Language | Flag | Native Name |
|------|----------|------|-------------|
| en | English | 🇺🇸 | English |
| es | Spanish | 🇪🇸 | Español |
| fr | French | 🇫🇷 | Français |
| de | German | 🇩🇪 | Deutsch |
| it | Italian | 🇮🇹 | Italiano |
| zh | Chinese | 🇨🇳 | 中文 |
| ja | Japanese | 🇯🇵 | 日本語 |
| pt | Portuguese | 🇧🇷 | Português |

### Implementation

```typescript
// src/i18n/index.ts
export type Locale = 'en' | 'es' | 'fr' | 'de' | 'it' | 'zh' | 'ja' | 'pt';
export const defaultLocale: Locale = 'en';
export const locales: Locale[] = ['en', 'es', 'fr', 'de', 'it', 'zh', 'ja', 'pt'];

export function t(locale: Locale, key: string): string { /* dot-notation lookup with EN fallback */ }
export function tRaw(locale: Locale, key: string): any { /* returns raw value (array/object) */ }
export function getLocalePath(locale: Locale, path: string): string { /* builds locale-prefixed URLs */ }
```

### Routing Convention
- English: `/about/team/` (no prefix)
- Other locales: `/{locale}/about/team/` (prefixed)
- All pages mirror EN structure per locale

### CJK Support
- Dedicated `cjk.css` for `:lang(zh)` and `:lang(ja)` typography overrides
- Adjusted line-height, letter-spacing, font-family fallbacks

---

## 5. DESIGN SYSTEM

### 5.1 Three-Flavor Architecture

Each site defines 3 visual flavors following the Sitecraft model. Each flavor has light and dark variants = 6 total combinations.

**Flavor selection:** `data-flavor` attribute on `<html>` (absent = default flavor).
**Theme selection:** `data-theme="dark"` on `<html>`.

**Per-flavor customization:**
- Color palette (primary, secondary, accent, surfaces)
- Typography (heading font, body font, code font)
- Border radius
- Shadow intensity
- Animation style

**Standard flavor structure:**
| Flavor | Character | Typical Use |
|--------|-----------|-------------|
| Flavor 1 (default) | Professional, authoritative | Corporate, institutional |
| Flavor 2 | Warm, approachable | Community, educational |
| Flavor 3 | Dynamic, innovative | Tech-forward, startup |

### 5.2 CSS Architecture (No Tailwind)

10+ modular CSS files using custom properties:
- BEM-style naming: `.component__element--modifier`
- Design tokens via CSS custom properties
- Dark mode via `[data-theme="dark"]` selector
- Flavor overrides via `[data-flavor="flavor2"]` selector
- CJK overrides via `:lang(zh)`, `:lang(ja)` selectors

### 5.3 Typography Standard

Each flavor defines:
- Heading font (serif or display)
- Body font (sans-serif)
- Code/prompt font (monospace — typically JetBrains Mono)
- Accent font (for quotes, callouts)

### 5.4 Dark Mode

- Toggle stored in `localStorage` key: `{site-id}-theme`
- Anti-flash technique in `<head>` script
- All components must support dark mode
- Minimum contrast ratios: 7:1 body text, 4.5:1 secondary

---

## 6. CONTENT & MENU STRUCTURE

### 6.1 Navigation Menu

**Scroll & Navigation Behavior:**
- Enable `scroll-behavior: smooth` globally; set `scroll-padding-top` to match the fixed nav height
- Implement **scroll-spy** in the Navigation component: use `IntersectionObserver` on section `id` targets to apply an `.active` class to the corresponding nav link as the user scrolls
- On long-form pages (landing pages, single-page layouts), anchor links in the nav must point to in-page `#section-id` targets with scroll-spy active
- Respect `prefers-reduced-motion: reduce` by falling back to `scroll-behavior: auto`

```
├── Explore
│   ├── New Frontiers
│   ├── AI Impact on {Sector}
│   ├── Challenges and Risks
│   ├── Opportunities
│   ├── Practical Applications
│   └── Personal Guide (Interactive)
├── Learn
│   ├── Intro to AI for {Professionals}
│   ├── What to Do with AI
│   ├── What Not to Do with AI
│   ├── Prompt Engineering (CRAFT Model)
│   ├── AI Readiness Assessment (Interactive)
│   └── Learning Program
│       ├── Program Overview
│       ├── Curriculum
│       └── Case Studies
├── Practice
│   ├── First Steps
│   ├── Quick Wins
│   ├── Prompt Builder (Interactive)
│   ├── Prompt Library
│   ├── AI Adoption Roadmap (Interactive)
│   └── Ethics Simulator (Interactive)
├── Resources
│   ├── FAQ
│   ├── Glossary
│   ├── Success Stories
│   ├── Tools Directory
│   └── Newsletter
├── Opinion
│   └── (Single page — articles by Human and AI experts)
├── Services
│   ├── AI Suite for {Sector}
│   ├── AI Readiness Assessment
│   ├── Consulting Services
│   ├── Digital Twins
│   ├── Personalized Training
│   └── Speaking & Keynotes
└── About Us
    ├── About Us
    ├── Our Team
    ├── Site Guide
    ├── Investors
    ├── Contact Us
    └── Sister Initiatives
```

### 6.2 Content Collections (Standard)

| Collection | Schema Fields | Typical Count |
|-----------|---------------|---------------|
| `quick-wins` | title, description, time, difficulty, sector, aiTool, prompt, tips, cautions, personaTakes, sources, order | 9-12 |
| `what-to-do` | title, number, description, howTo, steps, tools, personaTakes, sources, order | 10 |
| `what-not-to-do` | title, number, description, risk, realExample, mitigation, personaTakes, sources, order | 10 |
| `faq` | title, category, answer, sources, order | 20-30 |
| `glossary` | term, definition, aka, category, relatedTerms, sources, order | 30-100 |
| `success-stories` | title, company, sector, summary, takeaway, personaTakes, sources, order | 5-10 |
| `case-studies` | title, type (real/fictional/absurd), description, subtitle, slug, sector, personaTakes, sources, order | 3 |

### 6.3 Page Count Estimate

Per locale: ~60-70 pages. With 8 locales: ~480-560 pages total.
Plus content collection entries: ~200+ markdown files.

---

## 7. FIREBASE INTEGRATION

### 7.1 Services Used

| Service | Purpose |
|---------|---------|
| Firebase Auth | Anonymous-first, Google OAuth, email/password |
| Firestore | Likes, comments, submissions, users, conversations, newsletter, enrollments |
| Firebase AI SDK | Gemini 2.5 Flash (client-side, no Cloud Functions needed) |
| Analytics (GA4) | Page views, events, conversions |

### 7.2 Firestore Collections

```
{project}/
├── likes/                    # Content likes
│   └── {docId}/users/{uid}
├── comments/                 # Moderated user comments
│   └── {commentId}          → { pageId, userId, text, status, createdAt }
├── submissions/              # Contact form + service inquiries
│   └── {submissionId}       → { type, name, email, message, locale, createdAt }
├── enrollments/              # Learning program signups
│   └── {enrollmentId}       → { name, email, role, company, format, mode, createdAt }
├── users/                    # User profiles + usage tracking
│   └── {uid}                → { email, displayName, usage: { date, messagesUsed } }
├── conversations/            # Chat history (registered users)
│   └── {conversationId}     → { userId, personaId, locale, title, createdAt, updatedAt }
│       └── messages/
│           └── {msgId}      → { role, text, createdAt }
└── newsletter/               # Email subscriptions
    └── {emailHash}          → { email, locale, subscribedAt }
```

### 7.3 Auth Flow

1. Anonymous sign-in on first interaction (lazy, on demand)
2. Google OAuth or email/password upgrade available
3. `linkWithPopup()` / `linkWithCredential()` preserves anonymous UID
4. Same-email account merging supported

### 7.4 Security Rules Pattern

- Likes: anyone can read, authenticated can create/update
- Comments: anyone can read approved, authenticated can create (pending moderation)
- Submissions/enrollments: create-only by authenticated
- Users: owner-only CRUD
- Conversations: owner-only, registered-only for create
- Admin: hardcoded UID for comment moderation

---

## 8. AI CHAT SYSTEM (Ask {SiteName})

### 8.1 Architecture

- Svelte 5 component in Astro island (`client:idle`)
- Floating Action Button → expandable panel
- Firebase AI SDK → Gemini 2.5 Flash (client-side, no Cloud Functions)
- Page-context aware suggested questions
- Streaming responses with markdown rendering

### 8.2 Personas (4 standard)

| # | Persona | Voice | Tier | Temperature |
|---|---------|-------|------|-------------|
| 1 | {SiteName} Guide (default) | Balanced, educational | Anonymous | 0.7 |
| 2 | {Name} "The Strategist" | Data-driven, measured | Registered | 0.6 |
| 3 | {Name} "The Guardian" | Cautious, human-centered | Registered | 0.65 |
| 4 | {Name} "The Catalyst" | Bold, innovative | Registered | 0.8 |

Plus Carlos Miranda Levy (curator, registered-only, temp 0.65).

### 8.3 Freemium Tiers

| Feature | Anonymous | Registered (Free) |
|---------|-----------|-------------------|
| Daily messages | 5 | 25 |
| Personas | Default only | All |
| History | sessionStorage | Firestore (persistent) |
| Response length | 512 tokens | 1024 tokens |

Rate limiting:
- Anonymous: `localStorage` key `{site-id}-chat-usage` as `{ date, count }`
- Registered: Firestore `users/{uid}.usage` as `{ date, messagesUsed }`

### 8.4 System Prompt Template

```
IDENTITY
You are {name}, {title}. {personality}.
{Background, experience, philosophy}.

KNOWLEDGE BOUNDARIES
- Expert in {domain areas}
- Do NOT provide specific professional advice for real situations
- When uncertain, say so honestly

SITE CONTEXT
The user is currently viewing: {page title} ({page path}).

INTERACTION STYLE
- Keep responses concise: 150-250 words
- Use markdown formatting: **bold**, bullet points
- {Persona-specific tone guidelines}

GUARDRAILS
- Never fabricate citations, statistics, or case studies
- Never claim to be a licensed professional
- Recommend consulting qualified professionals
- Include educational disclaimers

LANGUAGE
Always respond in {user's locale language}.
```

---

## 9. INTERACTIVE FEATURES

### 9.1 Standard Interactive Tools

| Tool | Type | Description |
|------|------|-------------|
| AI Readiness Assessment | Quiz (12 questions, 4 dimensions) | Evaluates organization's AI readiness |
| Prompt Builder | Wizard (5 steps, CRAFT model) | Builds structured prompts |
| AI Adoption Roadmap | Wizard (5 steps) | Creates personalized adoption plan |
| AI Help Calculator | Decision tree (4 steps) | Determines if AI fits a task |
| Ethics Simulator | Branching scenarios (5 scenarios) | Explores ethical dilemmas |
| Personal Guide | Profile-based routing | Suggests exploration routes based on user profile |

### 9.2 Implementation Pattern

All interactive tools are Astro components with inline `<script>` blocks for client-side interactivity. No framework needed — vanilla JS with `data-*` attributes and CSS class toggling.

Complex interactions (chat, likes, comments, auth) use Svelte 5 components with `client:idle` hydration.

### 9.3 Funnel Strategy

Every page ends with a `FunnelCTA` component driving users toward:
- **Primary CTA:** Learning Program or Our Services
- **Secondary CTAs:** Quick Wins, Prompt Builder, AI Readiness, Prompt Library, AI Adoption Roadmap
- **Motivating language:** "Ready to take the next step?" / "Ready to become AI-ready?"

The funnel should feel helpful, not pushy — always include relevant secondary links alongside the primary CTA.

---

## 10. LEARNING PROGRAM

### 10.1 Structure

Based on the **Smoother Methodology** (see `/resources/smoother/`).

**Core components:**
- Hero with CTA + Flyer Slideshow
- Problem statement (why this matters)
- Three Pillars: Hyper-Personalized, Hands-On Practical, Smoother Methodology
- Core Curriculum (6 modules, expandable accordions)
- Specialization Tracks (6 tracks in card grid)
- Capstone Project
- Smoother Activity Types (quiz, case study, role simulation, discussion, project, reflection)
- Duration formats, learning modalities, delivery modes
- Enrollment form

### 10.2 Duration Formats

| Format | Duration | Target |
|--------|----------|--------|
| Express | 1 hour | Quick orientation, awareness |
| Intensive | 4 hours | Practical skills, hands-on |
| Professional | 8 hours | Comprehensive, with case studies |
| Masterful | 24 hours | Deep expertise, capstone project |

### 10.3 Delivery Modes

- Self-learning (asynchronous, on-demand)
- Coached-learning (guidance, feedback, async)
- In-person tutoring (real-time, virtual or physical)

### 10.4 18 Learning Modalities

Talks, Short Courses, Workshops, Diplomas, Challenges, Onboarding, Change Readiness, Makeovers, Hackathons, Bootcamps, Labs, Masterclass, Conversations/Panels, Micro-learning, Coaching, Training Sessions, Progressive Professional Development.

### 10.5 Case Studies (3 per site)

| Type | Purpose | Characteristics |
|------|---------|----------------|
| Real | Credibility, sourced references | Actual events, quotable sources |
| Fictional | Controlled learning experience | Explore specific aspects in depth |
| Absurd | Creative thinking, break assumptions | Extreme scenarios (zombie apocalypse, AI takeover, etc.) |

Each case study includes role simulation exercises per the Smoother methodology.

### 10.6 Personalization

1. Fast initial assessment (or detailed if desired)
2. Evaluates: learning style, speed, skill level, competencies
3. Generates personalized: learning path, activities, content, tools, environment
4. Includes customized case studies, role simulations, scenarios

---

## 11. ENGAGEMENT FEATURES

### 11.1 Like System
- Per-item likes (content cards, articles)
- Page-level "Was this useful?" bar
- Firestore backend with user tracking

### 11.2 Share System
- Share modal: X, Facebook, LinkedIn, WhatsApp, Email
- OG images per page
- Twitter Card meta tags

### 11.3 Comments
- Moderated comments (pending → approved/rejected)
- Admin panel at `/admin/comments/`
- Admin UID enforcement via Firestore rules

### 11.4 Newsletter
- Email signup in footer and dedicated page
- SHA-256 email dedup to Firestore
- Per-locale subscription tracking

### 11.5 Contact Form
- Modal with type selector (Consulting, Info, Program, Case, Idea, Services)
- Saved to Firestore `submissions/` collection

---

## 12. SEO & ANALYTICS

### 12.1 Meta Tags (BaseLayout)
- `<title>`, `<meta description>`, `<meta keywords>`
- Canonical URL
- `<link rel="alternate" hreflang>` for all 8 locales
- Open Graph: `og:title`, `og:description`, `og:image`, `og:type`, `og:locale`
- Twitter Card: `twitter:card`, `twitter:title`, `twitter:description`, `twitter:image`
- PWA: `mobile-web-app-capable`, `theme-color`

### 12.2 Google Analytics 4
- GA4 tag in `<head>` of BaseLayout
- Page view tracking
- Event tracking for interactive tools, CTA clicks, enrollments

### 12.3 Sitemap
- Auto-generated by `@astrojs/sitemap` on build
- All locales included

### 12.4 Search
- Pagefind runs post-build (`npx pagefind --site dist`)
- Client-side search UI in navigation
- Works offline (static index)

---

## 13. DEPLOYMENT

### 13.1 GitHub Pages
- Auto-deploy on push to `main`
- GitHub Actions workflow at `.github/workflows/deploy.yml`
- CNAME file in `public/` for custom domain

### 13.2 Build Verification
- `npm run build` must pass with 0 errors
- Expected page count verified in CI
- Sitemap auto-generated

### 13.3 Environment
- Firebase client config in `.env` (public by design, secured via Firestore rules)
- `.env.example` provided for setup reference
- `reference/` directory gitignored

---

## 14. PERSONA SYSTEM

### 14.1 Per-Site Personas

Each site defines 3 fictional AI personas + the curator:

| Role | Archetype | Voice | Purpose |
|------|-----------|-------|---------|
| The Moderate | Balanced analyst | Data-driven, measured, inclusive | Default viewpoint |
| The Skeptic | Critical guardian | Cautious, risk-aware, human-centered | Counterbalance |
| The Enthusiast | Innovation catalyst | Bold, forward-looking, optimistic | Inspiration |
| The Curator | Carlos Miranda Levy | Experienced, strategic, educational | Human anchor |

Each persona appears in:
- `PersonaTake` components on content pages (3 viewpoints per topic)
- AI chat system (selectable persona)
- Opinion articles (bylines)

### 14.2 Persona Design Requirements

For each persona, define:
- Full name (multicultural, reflecting global audience)
- Title / role description
- Background story (2-3 sentences)
- Voice characteristics (3-4 adjectives)
- Expertise areas
- Color association (maps to brand palette)
- Avatar image (AI-generated, professional portrait)
- System prompt for chat

---

## 15. SERVICES SECTION

### Standard Service Pages

| Service | Description |
|---------|-------------|
| AI Suite for {Sector} | SaaS platform with sector-specific AI tools |
| AI Readiness Assessment | Diagnostic + benchmarking engagement |
| Consulting Services | Tiered: Quick Wins ($3-15K), Full Transformation ($15-150K), Strategic Retainer ($3-20K/mo) |
| Digital Twins | Bespoke AI twin of professional ($5-37.5K build + maintenance) |
| Personalized Training | Standard ($49-499/seat) + Custom ($800-75K) |
| Speaking & Keynotes | Keynotes, events, lectures, webinars ($500-7,500) |

---

## 16. NON-PUBLIC BUSINESS DOCUMENTS

These are generated in `/resources/` and never deployed as web pages.

### 16.1 Commercialization Strategy (`commercialization-strategy.md`)

Standard structure:
- Operating Model (hybrid: proprietary tools + integrations)
- 7 Revenue Lines (AI Suite, Assessment, Consulting, Case Implementation, Digital Twin, Training, Speaking)
- Detailed pricing per line (developing vs developed world tiers)
- Go-to-market strategy
- The Flywheel: Free content → Authority → Assessment → Action → Recurring → Premium → Feedback

### 16.2 Business Plan (`business-plan.md`)

Standard sections:
- Executive Summary
- Value Proposition
- Problem-Solution Fit
- Market Dynamics and Disruptive Opportunity
- Business Model and Revenue Lines
- Financial Plan (3-year projections)
- Competitive Landscape
- Team
- Roadmap
- Projections & Exit Strategy
- Risk Analysis
- Why Now

**Standard expense structure:**
| Category | Amount |
|----------|--------|
| **Initial:** Legal & Incorporation | $1,000 |
| **Monthly:** Tech Tools & Licenses | $750 |
| **Monthly:** Accounting Services | $100 |
| **Monthly:** Office (Space, Electricity, Internet) | $1,000 |
| **Monthly:** Chief Innovation Officer | $5,000 |
| **Monthly:** Additional Staff | $2,500 |
| **Total Monthly Operating** | $9,350 |
| **Total Annual Operating** | $113,200 |

### 16.3 Investors Pitch (`investors-pitch.md`)

Standard structure:
- Investment terms (raise amount, valuation, equity, instrument)
- Use of funds allocation
- Return scenarios (conservative, mid, optimistic, pessimistic)
- Market opportunity
- Competitive advantages
- Team & track record

---

## 17. SISTER SITES NETWORK

Current network (all linked in footers and About sections):
- **Lawra.org** — AI in Law
- **Ibizai.io** — AI in Business
- **Insureversia.com** — AI in Insurance
- **AiLearning.global** — AI in Learning
- **AiVideo.rocks** — AI in Video Production
- **MaiMusic.org** — AI in Music
- **100+ AI** — AI directory

---

## 18. PRODUCTION WORKFLOW

### Phase 1: Foundation
1. Initialize Astro project with standard config
2. Set up CSS design system (3 flavors × light/dark)
3. Implement i18n system (start with EN+ES, expand to 8)
4. Configure Firebase project (Auth, Firestore, AI SDK)
5. Build core components (Navigation, Footer, BaseLayout, Icon, FlavorSelector)
6. Deploy to GitHub Pages

### Phase 2: Core Content
1. Homepage
2. About section (5-6 pages)
3. Explore section (5-6 pages)
4. Learn section (6-8 pages including Program)
5. Practice section (7-9 pages including interactive tools)

### Phase 3: Extended Content
1. Resources section (FAQ, Glossary, Success Stories, Tools Directory, Newsletter)
2. Opinion section
3. Services section (6 pages)
4. Content collections (quick-wins, what-to-do, what-not-to-do, faq, glossary, success-stories)

### Phase 4: Interactive Features
1. AI Chat system (Ask {SiteName}) — Phase 1: Chat UI + Gemini
2. AI Chat — Phase 2: Auth + Multi-Persona + History
3. Like/Share/Comment system
4. Admin panel

### Phase 5: Expansion
1. Expand i18n to all 8 languages
2. Learning Program curriculum (modules, exercises)
3. Case Studies with Role Simulation
4. Additional content (sector-specific deep dives)

### Phase 6: Business
1. Generate business documents (commercialization, business plan, investors pitch)
2. Investors page
3. Contact/Services forms

---

## 19. QUALITY CHECKLIST

Before each deployment:
- [ ] `npm run build` passes with 0 errors
- [ ] All flavors render correctly (3 × 2 = 6 combinations)
- [ ] Language switching works for all locales
- [ ] Search returns relevant results
- [ ] Interactive tools complete full flow
- [ ] CTAs link to correct destinations
- [ ] Dark mode: all elements readable
- [ ] Mobile: fully responsive
- [ ] CJK: Chinese/Japanese text renders properly
- [ ] Meta tags: OG images, Twitter cards, hreflang
- [ ] Firebase: auth, likes, submissions functional
- [ ] Chat: personas respond in correct language
- [ ] Comments: moderation flow works
- [ ] Lighthouse: Performance > 90, Accessibility > 90

---

## 20. NAMING CONVENTIONS

### localStorage Keys
- `{site-id}-theme` — dark/light mode
- `{site-id}-flavor` — selected flavor
- `{site-id}-chat-usage` — anonymous chat rate limiting
- `{site-id}-uid` — anonymous UID cache

### sessionStorage Keys
- `{site-id}-chat-messages-{personaId}` — chat session

### CSS Custom Properties
- `--color-primary`, `--color-secondary`, `--color-accent`
- `--surface-*` for backgrounds
- `--font-heading`, `--font-body`, `--font-code`
- `--radius-*` for border radii
- `--shadow-*` for box shadows

### Domain-Specific Terminology
Each site must define its domain mappings (replacing generic terms):

| Generic | Example (Law) | Example (Insurance) | Example (Business) |
|---------|--------------|--------------------|--------------------|
| practiceArea | practiceArea | insuranceSector | businessSector |
| sitesTake | lawrasTake | insureversiasTake | ibizaisTake |
| professionals | lawyers | insurance professionals | business leaders |
| regulatory bodies | bar associations | NAIC, state DOIs | regulators |

---

*This production book is a living document. Update it as patterns evolve across sites.*
