# Implement Flavor Preview Page

## Prompt

Paste this into Claude Code in any niche site repository:

---

Implement the Flavor Preview page at /about/design-preview/ following the spec in the sitecraft-system production book section 5.7.

This is an internal QA page (add noindex meta tag) that renders all UI components under the active flavor and theme so we can visually verify all 6 combinations (3 flavors x 2 themes).

The page must include:

1. **Sticky controls bar** at the top with:
   - 3 flavor buttons that set `data-flavor` on `<html>` in real time
   - Light/Dark theme toggle
   - Label showing current combination (e.g., "Flavor 2 -- Dark Mode")

2. **Color palette section** -- render all design tokens from variables.css as swatches with hex values and token names. Calculate and display WCAG contrast ratios for key text/background pairs. Flag failing pairs visually.

3. **Typography section** -- h1-h4 samples, body text, code/monospace, accent font. Show font name and weight alongside each.

4. **Component showcase** -- render one live instance of each component that already exists in this project's src/components/: buttons (primary, secondary, outline, disabled), cards (standard, clickable, QuickWinCard if it exists), badges, form inputs, alerts/highlight boxes, accordion, modal trigger, persona takes, and a grid of Lucide icons.

5. **Page pattern samples** -- a sample hero section, 3-column card grid, prose content block (with links, lists, code, blockquotes), and the site footer.

6. **Issue Reporter** -- a Svelte island (DesignIssueReporter.svelte) with fields: Combination (auto-filled), Component (dropdown), Issue type (Color conflict / Contrast failure / Rendering bug / Typography issue / Other), Description (textarea). A "Copy Report" button formats it as markdown and copies to clipboard:

```markdown
## Design Issue: {Component} -- {Flavor} {Theme}
- **Type:** {Issue type}
- **Combination:** {Flavor name} x {Light|Dark}
- **Description:** {Description}
- **Page:** /about/design-preview/
```

Implementation notes:
- Page file: src/pages/about/design-preview/index.astro
- Import and render the ACTUAL site components -- not mockups
- The Issue Reporter is a Svelte island for clipboard interaction
- English-only (internal tool), but components render in the current locale
- Add `<meta name="robots" content="noindex">` in the layout
- Use the site's existing BaseLayout
- Read the actual CSS custom properties via getComputedStyle() for the color palette section

---

## Applicable Repos

All niche sites in the CEMI.ai network:

- ibizai-web
- insureversia-web
- lawra-web
- maimusic-web
- pachamaima-web
- quantum-insureversia
- xperto-taim

And any future niche site built from the production book template.
