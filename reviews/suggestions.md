# Protocol Review — Suggestions & Notes

Full review of `protocol/xperto-sitecraft.md` v1.0.0 (4,360 lines).
Review date: 2026-02-17.

---

## Summary

| Priority | Count |
|----------|-------|
| High     | 28    |
| Medium   | 30    |
| Low      | 14    |
| **Total**| **72**|

### Top Systemic Issues

1. **Structural inconsistency in prompt templates** — Many templates (especially content generation, image, video) omit standard sections (CONTEXT, CONSTRAINTS, QUALITY CRITERIA, HANDOFF) despite the meta-template declaring all prompts follow the same structure.
2. **Bolt-on sections invisible to the gated workflow** — Community Engagement, Video Integration, Personalization, and AI-Powered Features are all Design-phase prompts but do not appear in the Design phase exit deliverables or gate criteria. A team could pass all gates without producing any of these.
3. **Missing production templates** — No prompt template for the base Visual Design System or Competitive Analysis, though both are referenced as inputs by multiple downstream templates.
4. **Role naming inconsistency** — "Market Research Specialist" vs. "Market / User Research Specialist" used interchangeably; "UI Expert" vs. "UX Expert" confusion.
5. **Dependency ordering issues** — Voice Guidelines requires outputs (Personas, Website Goals) that appear later in the document; Creative Concepts references Flavors before the Flavor System exists.
6. **Stub sections** — Security Audit, Performance Audit, and Analytics Reporting are `(pending)` placeholders with no content.
7. **Outdated technical standards** — FID replaced by INP as a Core Web Vital; WCAG 2.1 should acknowledge 2.2.

---

## HIGH PRIORITY

> **All 28 high-priority issues resolved in v1.1.0** (2026-02-17). See `CHANGELOG.md` for details.

### H1. Business Strategist / Website Strategy Consultant KPI overlap (lines ~49, ~125)
**Type**: inconsistency — **RESOLVED v1.1.0**
**Description**: Both roles define KPIs independently. Business Strategist "Identifies key performance indicators" and produces "Success Metrics Definition." Website Strategy Consultant "Defines KPIs and success metrics" and produces "KPI Framework." No guidance on how these relate or which takes precedence. Risk of conflicting outputs.

### H2. Content Strategist / UX Expert information architecture dependency undefined (lines ~139, ~196)
**Type**: gap — **RESOLVED v1.1.0**
**Description**: Content Strategist produces "Information Architecture Document" and "Sitemap with Hierarchy." UX Expert produces "Wireframes" and "User Journey Maps" which depend on and feed back into the IA. No collaboration protocol or co-creation relationship defined between these tightly coupled roles.

### H3. Missing Content Writer / Copywriter role (lines ~21-334)
**Type**: gap — **RESOLVED v1.1.0**
**Description**: No role is responsible for actually writing website copy. Content Strategist plans content, Communications Expert defines voice, but nobody is assigned to produce headlines, body copy, CTAs, or microcopy. Phase 4 lists "Content population" as an activity but assigns no owner.

### H4. Market Research Specialist absent from Phase 1 Discovery (lines ~349-353)
**Type**: gap — **RESOLVED v1.1.0**
**Description**: "Market and competitor research" is listed as a Phase 1 Discovery activity, but the Market/User Research Specialist only appears in Phase 2. No one owns market research in the Discovery phase.

### H5. Website Strategy Consultant categorization vs. Phase 2 timing (lines ~115, ~393)
**Type**: inconsistency — **RESOLVED v1.1.0**
**Description**: Categorized under "Design Experts" but produces a key Phase 2 (Conceptualization) deliverable. Either recategorize as Conceptualization Expert or move the deliverable to Phase 3.

### H6. Phase 3 Design lacks internal sequencing (lines ~404-442)
**Type**: suggestion — **RESOLVED v1.1.0**
**Description**: Phase 3 has 9 exit deliverables spanning 6+ expert roles, all treated as a monolithic block. No sub-phasing or sequencing guidance. In practice, Information Architecture must precede Wireframes, which must precede Visual Design System finalization.

### H7. Phase 4 has no content production owner (lines ~455-469)
**Type**: gap — **RESOLVED v1.1.0**
**Description**: "Content population" is listed as a Phase 4 activity but no deliverable owner is assigned. No expert writes or populates content. The gate criterion "Content reviewed and approved" does not address who creates the content.

### H8. JS/CSS file lists inconsistent with directory structure (lines ~556-564, ~685-703)
**Type**: inconsistency — **RESOLVED v1.1.0**
**Description**: CSS Architecture lists `animations.css` and `flavors/`; JS Architecture lists 10 files. Directory Structure only shows 6 CSS files and 4 JS files. Six JS modules and several CSS modules are defined in the architecture but absent from the directory.

### H9. Favicon path bug in HTML template (line ~889)
**Type**: inconsistency — **RESOLVED v1.1.0**
**Description**: Template references `/assets/favicon-brand.png` but Asset Types table specifies favicons at `/assets/logos/favicon-brand.png`. Would cause a broken favicon in production.

### H10. Event name mismatch: `language-change` vs `site-language-change` (lines ~663, ~932)
**Type**: inconsistency — **RESOLVED v1.1.0**
**Description**: Two different event names for the same i18n functionality. Would cause a runtime bug — language switching would not work.

### H11. FID is an outdated Core Web Vital (lines ~837, ~2859)
**Type**: enhancement — **RESOLVED v1.1.0**
**Description**: Google replaced First Input Delay (FID) with Interaction to Next Paint (INP) in March 2024. Protocol should target INP (< 200ms) instead.

### H12. Discovery section duplicates Phase 1 with no structural relationship (lines ~349-370, ~961-973)
**Type**: inconsistency — **RESOLVED v1.1.0**
**Description**: Discovery is defined twice: once as Phase 1 in Workflow Architecture and again as the "DISCOVERY: STRATEGIC IDENTIFICATION" section. Different language, no cross-reference, unclear relationship.

### H13. Discovery section has no structured output format (lines ~975-1007)
**Type**: gap — **RESOLVED v1.1.0**
**Description**: Lists questions and topics but defines no deliverable format for capturing answers. Discovery findings are the primary input for all Conceptualization work, yet they have no defined template beyond the Phase 1 exit deliverables table.

### H14. Voice Guidelines dependency ordering problem (lines ~1204-1208)
**Type**: inconsistency — **RESOLVED v1.1.0**
**Description**: Voice Guidelines requires Target Audience Personas and Website Goals as inputs, but both are defined later in the document. Website Goals itself requires Personas. Creates unclear execution order. Either reorder or add an explicit dependency diagram.

### H15. Role naming inconsistency: three names for one role (lines ~98, ~392, ~1206)
**Type**: inconsistency — **RESOLVED v1.1.0**
**Description**: The same role is called "Market / User Research Specialist" (line 98), "Market Research Specialist" (line 392), and referenced without the "/" in various places. Should be standardized throughout.

### H16. Competitor analysis referenced but never produced (lines ~1321, ~1649)
**Type**: gap — **RESOLVED v1.1.0**
**Description**: "Competitor audience analysis" and "Competitive landscape analysis" are listed as inputs in multiple templates but no prompt template assigns any role to produce these artifacts.

### H17. Creative Concepts references Flavors before they exist (line ~1701)
**Type**: gap — **RESOLVED v1.1.0**
**Description**: Creative Concepts output asks "How concept accommodates Flavors" but the Flavor System is developed later. The Creative Designer cannot describe Flavor accommodation when no Flavor System has been defined yet.

### H18. No prompt template for base Visual Design System (line ~1765)
**Type**: gap — **RESOLVED v1.1.0**
**Description**: The Flavor System template requires "Visual Design System (base)" as input. The Visual Design System is listed as a Phase 3 deliverable but has no corresponding production prompt template anywhere in the document.

### H19. Content Architecture placed under EXECUTION header but labeled Design phase (lines ~1925, ~1937)
**Type**: inconsistency — **RESOLVED v1.1.0**
**Description**: Section header reads "## EXECUTION" but the prompt is `[PHASE]: Design`. Phase 3 exit deliverables list Information Architecture as a Design deliverable. The section heading is premature.

### H20. Regional Flavors use culturally reductive stereotypes (lines ~1869-1878)
**Type**: inconsistency — **RESOLVED v1.1.0**
**Description**: Pre-defined flavors like "Asian Harmony" for an entire continent and "European Minimal" risk inappropriate generalizations. Should be framed as starting-point examples requiring per-project customization, not pre-built library items.

### H21. Image generation prompts structurally incomplete (lines ~2159-2203)
**Type**: inconsistency — **RESOLVED v1.1.0**
**Description**: Hero Image and Section Image prompts are the thinnest in the document. Missing: PHASE, CONTEXT, CONSTRAINTS, QUALITY CRITERIA, HANDOFF. No guidance on brand consistency, style vs. photography distinction, or AI generation vs. stock decision criteria.

### H22. Video sub-type prompts are not real templates (lines ~2242-2273)
**Type**: inconsistency — **RESOLVED v1.1.0**
**Description**: The three video sub-type prompts (Testimonial, Explainer, Sales) are simple bullet lists with no role assignment, inputs, constraints, or quality criteria. Structurally incomplete compared to every other prompt in the document.

### H23. Text content prompts disconnected from Content Architecture (lines ~2275-2390)
**Type**: gap — **RESOLVED v1.1.0**
**Description**: None of the five text content generation prompts include Content Architecture Document or Page-Level Content Briefs as inputs, despite those documents defining per-page specifications including primary message, CTAs, SEO specs, and accessibility requirements.

### H24. Security Audit is an empty stub (line ~2995)
**Type**: gap — **RESOLVED v1.1.0**
**Description**: The entire Security Audit section is `(pending)`. No website should pass through a comprehensive QA process without security validation. Even static sites need HTTPS, CSP headers, and dependency scanning.

### H25. Performance Audit is an empty stub (line ~2999)
**Type**: gap — **RESOLVED v1.1.0**
**Description**: Like Security, Performance Audit is just `(pending)`. Performance metrics are only superficially covered in the QA Framework (5 metrics with targets). No standalone audit for server-side performance, bundle budgets, third-party impact, or caching strategy.

### H26. QA Framework missing quality criteria for itself and automated testing (lines ~2811-2895)
**Type**: gap — **RESOLVED v1.1.0**
**Description**: The QA prompt lacks both QUALITY CRITERIA and CONSTRAINTS sections. Also covers only manual testing — no mention of automated testing, regression testing, test environments, load testing, or test data management.

### H27. Cultural Context Analysis prompt missing standard template elements (lines ~3450-3503)
**Type**: gap — **RESOLVED v1.1.0**
**Description**: The only full prompt that omits all four of: INPUTS, CONSTRAINTS, QUALITY CRITERIA, and HANDOFF.

### H28. Pre-Launch Checklist missing major categories (lines ~3958-4007)
**Type**: gap — **RESOLVED v1.1.0**
**Description**: Missing items for: Flavor System verification, multilingual/i18n testing, AI-powered features, community features, personalization, specific Core Web Vitals targets, legal/GDPR compliance, cookie consent, DNS/domain, and content backup/recovery.

---

## MEDIUM PRIORITY

### M1. Grammar issue in AI Philosophy statement (line ~17)
**Type**: inconsistency
**Description**: "AI does not replace our teams or merely automates simple tasks" — broken grammar. Should be "nor merely automate."

### M2. Inconsistent expert category naming (lines ~23, ~115, ~244)
**Type**: inconsistency
**Description**: "Conceptualization Experts," "Design Experts," but "Execution Phase Experts." The third adds "Phase" breaking parallel structure.

### M3. Creative Designer / Visual Design Expert boundary unclear (lines ~154-188)
**Type**: suggestion
**Description**: Distinction is "what/why" vs. "how" but the boundary is blurry. No arbitration mechanism when mood boards conflict with design system constraints.

### M4. Strategic Foundation Package undefined (line ~394)
**Type**: gap
**Description**: Listed as Phase 2 exit deliverable owned by Project Manager with vague "Comprehensive review" validation. Never defined elsewhere. Contents unknown.

### M5. Directory Structure vs. Site Map mismatch (lines ~529-599)
**Type**: inconsistency
**Description**: Directory Structure shows `/about/index.html` as a single page; Site Map Template shows `/about/` with three sub-pages. `resources/` directory present in Site Map but absent from Directory Structure.

### M6. HTML template semantic HTML violations (lines ~903, ~917)
**Type**: inconsistency
**Description**: Code Style Guidelines mandate semantic HTML5, but template uses `<div id="site-nav">` and `<div id="site-footer">` instead of `<nav>` and `<footer>`.

### M7. Analytics double-loading concern (lines ~867-874, ~697)
**Type**: inconsistency
**Description**: Template includes inline Google Analytics in `<head>` AND JS Architecture defines `analytics.js` module. Relationship unclear — risks double-tracking.

### M8. Missing Open Graph and Twitter Card tags (lines ~882-886)
**Type**: enhancement
**Description**: OG tags missing required `og:type` and `og:site_name`. No Twitter Card markup at all. Expected for a protocol with an SEO Specialist role.

### M9. WCAG version should acknowledge 2.2 (lines ~322, ~475, ~2916)
**Type**: enhancement
**Description**: Protocol targets WCAG 2.1 AA throughout. WCAG 2.2 was published October 2023 with additional success criteria. Should at minimum acknowledge 2.2.

### M10. Iteration protocols lack conflict resolution (lines ~481-519)
**Type**: gap
**Description**: Only 3 adjacency pairs defined for 15+ roles. No protocol for disagreements between adjacent experts. No escalation mechanism or iteration cycle limits.

### M11. Retrospective protocol has no output artifact (lines ~512-519)
**Type**: gap
**Description**: Asks four questions but defines no output document, no owner, and no mechanism for feeding learnings forward.

### M12. Page elements lack i18n mapping (lines ~844-857)
**Type**: gap
**Description**: Page Elements list makes no reference to internationalization requirements per element, despite extensive multilingual support section.

### M13. Project Identity Card should consume Discovery Brief (lines ~1059-1095)
**Type**: gap
**Description**: First Conceptualization task but does not list the Discovery Brief as input, despite it being a Phase 1 exit deliverable referenced by later templates.

### M14. ASSUME constraint type missing from all templates (lines ~1033, ~1059+)
**Type**: gap
**Description**: Meta-template defines `ASSUME: [Safe assumptions]` as a standard constraint sub-type, but no actual template includes it.

### M15. Website Goals input overlap with Brand DNA (lines ~1424-1428)
**Type**: gap
**Description**: "Business objectives from stakeholder interviews" overlaps with information already synthesized in the Brand DNA Document. No guidance on precedence.

### M16. Collaborative task structure undefined (lines ~1517, ~2052, ~3106)
**Type**: enhancement
**Description**: Multiple templates assign two roles (e.g., "Brand Strategist + Communications Expert") but no guidance on who leads, how conflicts are resolved, or how output is attributed.

### M17. Site Persona multilingual constraint unconditional (line ~1537)
**Type**: gap
**Description**: "DO: Define how the persona adapts across languages and cultures" presupposes multilingual scope. Should be conditional.

### M18. Creative Direction Document not linked to Flavor System (lines ~1711-1716, ~1763)
**Type**: inconsistency
**Description**: Creative Concepts handoff does not mention Flavor System development. Flavor System inputs do not include Creative Direction Document. The two should be explicitly linked.

### M19. Flavor System HANDOFF missing UX and Accessibility experts (lines ~1858-1863)
**Type**: gap
**Description**: Flavors affect visual presentation, interaction patterns, and user experience, but UX Expert and Accessibility Expert are not listed as handoff recipients.

### M20. Contextual Flavor Library has no workflow integration (lines ~1865-1924)
**Type**: gap
**Description**: Sits outside any prompt template. No guidance on who produces these, how they are validated, or how they connect to the Flavor System prompt.

### M21. Flavor System quality criteria lack accessibility specifics (lines ~1852-1857)
**Type**: gap
**Description**: "Accessibility verified for each Flavor" is generic. Should reference WCAG contrast ratios for each variant, reduced motion considerations, and font accessibility.

### M22. Content Architecture handoff missing Content Strategist (lines ~2022-2028)
**Type**: inconsistency
**Description**: Lists five downstream consumers but omits Content Strategist, despite the document being an input to nearly every text content generation prompt.

### M23. Learning Path Architecture phase/location ambiguity (lines ~2031, ~2052)
**Type**: inconsistency
**Description**: Labeled `[PHASE]: Design` but positioned after Content Architecture under the EXECUTION section. Should be moved or relabeled.

### M24. Text content prompts missing HANDOFF sections (lines ~2275-2390)
**Type**: inconsistency
**Description**: None of the five text content generation prompts include a HANDOFF section. Every other major prompt template specifies downstream consumers.

### M25. "Other Content to Generate" is a stub (lines ~2392-2395)
**Type**: gap
**Description**: "News and Updates" and "Guidelines and Tutorials" listed with no prompt templates. Should have minimal templates or be marked `(pending)`.

### M26. A/B Testing Framework duplicated and incomplete (lines ~2665-2669, ~2696-2748)
**Type**: inconsistency
**Description**: Covered within Analytics Framework AND as a standalone section. Standalone version missing QUALITY CRITERIA and CONSTRAINTS sections.

### M27. QA Performance metrics reference outdated FID (line ~2859)
**Type**: suggestion
**Description**: Should also include TTI and TBT, which are commonly used in Lighthouse audits.

### M28. Community Engagement not in Design phase deliverables table (lines ~3075, ~419-431)
**Type**: suggestion
**Description**: Prompt uses `[PHASE]: Design` but Design phase exit deliverables and gate criteria don't mention it. Invisible to the gated workflow.

### M29. Video Integration not in deliverables or Client Touchpoint Map (lines ~3209, ~3652)
**Type**: suggestion
**Description**: Same issue as Community Engagement — a Design-phase bolt-on invisible to gates and client touchpoints.

### M30. Client Collaboration Protocol severely underdeveloped (lines ~3650-3699)
**Type**: gap
**Description**: Only outline-level templates (5-7 bullets each). No prompts, no conflict resolution guidance, no scope creep handling, no formal sign-off document template — despite the workflow requiring client sign-off at multiple gates.

---

## LOW PRIORITY

### L1. Repeated "soul/skin" metaphor (lines ~5, ~11)
**Type**: inconsistency
**Description**: Same metaphor stated nearly verbatim within six lines. Reads as accidental duplication.

### L2. Analytics Architect placement under Design Experts (lines ~228-242)
**Type**: suggestion
**Description**: Designs measurement frameworks and event tracking — more technical/execution-oriented. No corresponding Execution-phase expert implements what the Analytics Architect designs.

### L3. Responsive breakpoints lack CSS mapping (lines ~820-827)
**Type**: gap
**Description**: Six breakpoints defined but no guidance on CSS custom property mapping or media query patterns. Mobile-first approach implied but both min-width and max-width columns shown.

### L4. Footer structure incomplete (lines ~940-959)
**Type**: gap
**Description**: Minimal ASCII layout omits social links, contact info, legal links, and site navigation. No accessibility requirements for footer landmark.

### L5. Meta-template INPUTS parenthetical inconsistency (line ~1023)
**Type**: inconsistency
**Description**: Meta-template says `INPUTS (from previous steps)` but every actual template uses bare `INPUTS`.

### L6. Voice Guidelines formatting error (line ~1224)
**Type**: inconsistency
**Description**: `#### 1. **Brand Voice Characteristics` — bold marker opened but never closed.

### L7. Vague "available market research" input (line ~1320)
**Type**: gap
**Description**: Unlike other inputs that reference specific documents from specific roles, this is an open-ended "whatever is available" clause that undermines traceability.

### L8. Website Goals handoff lists non-immediate consumer (line ~1492)
**Type**: inconsistency
**Description**: Lists Analytics Architect as handoff recipient, but that role acts much later. Other handoffs list only immediate downstream consumers.

### L9. Site Persona accessibility bullet insufficient (line ~1572)
**Type**: enhancement
**Description**: Single bullet for screen reader accessibility is insufficient for what is a complex design challenge, especially for chatbot persona interactions.

### L10. Keyword density is a deprecated SEO concept (line ~2573)
**Type**: suggestion
**Description**: "Keyword density recommendations" is outdated. Modern SEO uses semantic coverage. The protocol itself warns against keyword stuffing but then recommends density targets.

### L11. User Journey Validation references "UI Expert" (line ~2805)
**Type**: inconsistency
**Description**: Handoff mentions "UI Expert" but the protocol defines "UX Expert." Either a different role or a naming error.

### L12. "LAYERs" heading typo (line ~3298)
**Type**: inconsistency
**Description**: "PERSONALIZATION AND CONTEXTUALIZATION LAYERs" — inconsistent lowercase "s".

### L13. Brand DNA template minor field mismatch (line ~3700)
**Type**: suggestion
**Description**: Prompt specifies "Brand Essence (One-Liner)" under Differentiators; template has "Unique Positioning" / "Competitive Advantage" but no explicit one-liner field.

### L14. Voice Guidelines template includes items not in the prompt (lines ~3936, ~3939)
**Type**: suggestion
**Description**: Template includes "Error Messages" and "Empty States" under Example Phrases — excellent additions but not requested by the prompt that generates this document.

---

## ADDITIONAL OBSERVATIONS

### Style Guide template has broken Markdown fencing (line ~4064)
**Type**: inconsistency  **Priority**: high
**Description**: Code fence closes after Gradients & Effects, splitting the template. Everything from "Border Styling" onward renders as document content rather than template content.

### Duplicate "Discovery Additions for Cultural Context" heading (lines ~3400, ~3448)
**Type**: inconsistency  **Priority**: medium
**Description**: Same heading appears twice — first introduces narrative bullets, second introduces the prompt. Content is nearly duplicated.

### Cultural Context prompt phase mismatch (line ~3452)
**Type**: inconsistency  **Priority**: medium
**Description**: Labeled `[PHASE]: Discovery` but nested under Personalization section between Design-phase sections. Should be near the Discovery section if it belongs to Discovery.

### Post-Execution phase not formally defined in Workflow Architecture (line ~3003)
**Type**: gap  **Priority**: medium
**Description**: Workflow Architecture defines 4 phases. Post-Execution exists as a section but has no phase definition, no gate criteria, no duration estimate.

### Style Guide template missing Design Tokens section (line ~4009)
**Type**: gap  **Priority**: medium
**Description**: Visual Design Expert outputs include "Design Tokens Documentation" but the Style Guide template only uses CSS custom properties with no platform-agnostic token format.

### Style Guide template missing Flavor System integration (line ~4009)
**Type**: gap  **Priority**: medium
**Description**: No section showing how Flavor overrides map to base design tokens, despite the Visual Design Expert owning both documents.

### Style Guide component patterns incomplete (line ~4104)
**Type**: gap  **Priority**: medium
**Description**: Only covers Cards, Badges, Highlight Boxes, CTA Buttons, and Form Elements. Missing ~10 common patterns (navigation, modal, tooltip, tabs, tables, alerts, pagination, breadcrumbs, loading states).

### Style Guide single responsive breakpoint (line ~4295)
**Type**: gap  **Priority**: medium
**Description**: Only defines 768px breakpoint despite the document's own Responsive Breakpoints section defining 6 breakpoints.

### Missing appendix templates (document-wide)
**Type**: gap  **Priority**: medium
**Description**: Templates exist only for Brand DNA, Voice Guidelines, Pre-Launch Checklist, and Style Guide. Missing: Target Audience Persona (most referenced input), Content Architecture, Creative Direction, Discovery Brief/Project Charter, QA Report, Website Goals.

### Web Management Plan phase mislabeled (line ~3016)
**Type**: inconsistency  **Priority**: low
**Description**: Labeled `[PHASE]: Execution` but lives under "POST-EXECUTION AND SUPPORT." Should be Post-Execution.

### Voice Guidelines template additions (lines ~3936, ~3939)
**Type**: enhancement  **Priority**: low
**Description**: Template includes "Error Messages" and "Empty States" examples — good for web design. Prompt should be updated to request these.
