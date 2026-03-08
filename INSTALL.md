# Installation & Setup

Xperto SiteCraft is a methodology document, not installable software. There is no build step, no dependencies, and no runtime. This guide explains how to set up your working environment and use the protocol.

## Prerequisites

- Git
- A markdown editor or viewer (VS Code recommended)
- [Claude Code](https://claude.com/claude-code) (recommended for AI-assisted protocol use)

## Clone the Repository

```bash
git clone https://github.com/XpertoFactory/sitecraft-system.git
cd sitecraft-system
```

## Repository Layout

```
sitecraft-system/
├── protocol/                     # Protocol documents
│   ├── xperto-sitecraft.md       # Core protocol (~4,360 lines)
│   └── niche-sites/              # Niche AI site templates
│       ├── production-book.md    # Full technical reference for building a site
│       ├── site-plan-template.md # Per-site implementation plan template
│       ├── initial-setup-template.md  # Site identity & content kickoff template
│       └── business-docs-template.md  # Non-public business document templates
├── niche-sites/                  # Working notes & fix scripts for live sites
├── reference/                    # External references, examples, benchmarks
├── resources/                    # Supporting materials and tools
├── reviews/                      # Protocol review notes
│   └── suggestions.md
├── CHANGELOG.md
├── CLAUDE.md                     # Project context for Claude Code
├── INSTALL.md                    # This file
└── README.md
```

## Usage

### Using the Core Protocol

1. Read `protocol/xperto-sitecraft.md` — the single source of truth for the SiteCraft methodology.
2. Follow the phased workflow: Discovery → Conceptualization → Design → Execution → Optimization → Post-Execution.
3. Use the prompt templates with an AI assistant (Claude, etc.) to generate deliverables for each phase.

### Creating a New Niche AI Site

1. Copy `protocol/niche-sites/initial-setup-template.md` into your new site's repository and fill in all `{PLACEHOLDERS}`.
2. Copy `protocol/niche-sites/site-plan-template.md` and customize it with your site's architecture, content collections, and design tokens.
3. Use `protocol/niche-sites/production-book.md` as the authoritative technical reference during development — it covers the tech stack (Astro + Svelte + Pagefind + Firebase), file structure, i18n, search, deployment, and quality checklists.
4. Use `protocol/niche-sites/business-docs-template.md` to generate non-public business documents (commercialization strategy, business plan, investor pitch).

### Working with Claude Code

The repository includes a `CLAUDE.md` file that provides project context to Claude Code. When you open this repo in Claude Code, it will automatically understand the project structure, conventions, and editing guidelines.

## Contributing

- Log improvement suggestions in `reviews/suggestions.md` with section references.
- All protocol changes must be reflected in `CHANGELOG.md`.
- Keep edits focused — one concern per change.
- Preserve the existing heading hierarchy and formatting conventions.
