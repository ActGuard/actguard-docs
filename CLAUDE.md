# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

Documentation site for **ActGuard** — a runtime governance layer for AI agents (budget enforcement, tool guards, chain-of-custody). Built on Mintlify.

## CLI commands

```bash
npm i -g mint      # Install Mintlify CLI (one-time)
mint dev           # Local preview at localhost:3000
mint validate      # Validate build
mint broken-links  # Check internal links
mint a11y          # Accessibility check
mint rename        # Rename/move files and update references
```

Mintlify deploys automatically on push to the connected Git branch.

## Site structure

- `docs.json` — site configuration (navigation, theme, colors, logo). **Never use `mint.json`** — it's deprecated.
- `index.mdx` — root landing page
- `python-sdk/` — SDK documentation pages
- `python-sdk/integrations/` — provider-specific pages (openai, anthropic, google)
- `assets/` — static assets (logo, images)

Navigation has two tabs: **Docs** (Getting Started, Concepts, API) and **Integrations** (Providers).

## Content rules

Every `.mdx` file requires `title` in frontmatter (add `description` for SEO). Always specify language tags on code blocks. Use root-relative paths without file extensions for internal links (e.g. `/python-sdk/getting-started`). When creating a new page, add it to `docs.json` navigation or it won't appear in the sidebar.

## Mintlify skill

A Mintlify skill is installed at `.agents/skills/mintlify/SKILL.md`. It contains detailed component references, navigation patterns, writing standards, and workflow checklists. Consult it (or https://mintlify.com/docs) for component selection, `docs.json` config options, and content conventions.

Key writing standards from the skill:
- Sentence case for headings
- No marketing language ("powerful", "seamless", "robust")
- No filler phrases ("it's important to note", "in order to")
- Second-person voice, active voice
