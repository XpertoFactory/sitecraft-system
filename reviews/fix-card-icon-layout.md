# Fix Card Icon Layout: Inline Icon-Title Instead of Stacked

## Prompt

Paste this into Claude Code in any repository that uses cards with icons:

---

Scan this repository for the "stacked icon-over-title" anti-pattern in cards: anywhere an SVG icon or `<Icon>` component is placed on its own line above a card title (h2/h3), instead of inline to the left. The icon is typically inside its own `<div>` wrapper with `margin-bottom`, followed by the heading on the next line.

Fix every instance by making the icon sit inline to the left of the title:
1. Wrap the icon + heading together in a flex container: `<div style="display: flex; align-items: center; gap: 0.75rem;">`
2. Remove any block-level wrapper around the icon that causes it to be on its own line (e.g., `<div style="margin-bottom: ...">` around the icon).
3. Keep the icon size and color as-is.
4. If the icon was inside a centered/block div, remove the centering.

After fixing the HTML, update this repo's CLAUDE.md (create one if it doesn't exist) to include this design rule:

### Card Icon Layout
- Never stack an icon above a card title on separate lines
- Always place the icon inline to the left of the title using `display: flex; align-items: center; gap: 0.75rem`
- This applies to all card components, feature grids, and any icon+heading pairing

Then commit with message: "Fix card icon layout: inline icon-title instead of stacked"

---

## Priority Repos (confirmed anti-pattern)

1. **ibizai-web** — sector cards, prompt library categories
2. **insureversia-web** — sector cards, learning program pillars, delivery modes, applications
3. **lawra-web** — training tiers, speaking formats, multiple template pages
4. **quantum-insureversia** — contact cards, onboarding features

## Also Worth Running On

- quantum-media
- thesocialentrepreneur-web
- uaf2026
- maimusic-web
- pachamaima-web
- xpertomedia-web
- xperto-concilia

## Likely Clean (minimal or no card content)

- mipais
- xpertalks
- xolutiva-web
- xaid
- xperto-group-web
- xpertorutas
- xpertosolutions-web
- xperto-taim
