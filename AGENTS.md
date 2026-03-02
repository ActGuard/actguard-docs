# Repository Guidelines

## Project Structure & Module Organization
This repository contains documentation content and site configuration.

- `docs/`: Main Markdown documentation pages.
- `docs/python-sdk/`: Python SDK docs (`getting-started.md`, `api-reference.md`, `tool-guards.md`, etc.).
- `assets/`: Static assets used by docs (for example, logos).
- `docs.json`: Documentation site configuration (theme, navigation, branding).

When adding pages, keep related topics grouped under the same folder and update `docs.json` navigation so pages appear in the sidebar.

## Build, Test, and Development Commands
No project-local build scripts are checked in (`package.json`/`Makefile` not present). Typical docs workflow:

- `mintlify dev` (or `npx mintlify dev`): Run local docs preview from repo root.
- `git diff -- docs.json docs/`: Review content and navigation changes before commit.
- `rg "TODO|FIXME" docs`: Catch unfinished text before opening a PR.

If your environment uses different docs tooling, document it in this file when introduced.

## Coding Style & Naming Conventions
- Write docs in Markdown with clear heading hierarchy (`#`, `##`, `###`).
- Use concise, instructional language and runnable examples.
- Prefer kebab-case file names (for example, `getting-started.md`).
- Keep line length readable and avoid excessive inline HTML.
- Use fenced code blocks with language tags (for example, ```python, ```bash).

For site config, keep `docs.json` keys consistent and grouped (`colors`, `logo`, `navigation`, `theme`).

## Testing Guidelines
There is no automated test suite in this repository today. Validate changes by:

- Running local preview and checking page rendering/navigation.
- Verifying internal links and section anchors.
- Copy-running command/code snippets where practical.

Treat broken links, invalid code samples, and missing nav entries as release blockers.

## Commit & Pull Request Guidelines
Recent commits use short, imperative summaries (for example, `Added index`, `Update docs.json with new navigation structure and colors`).

- Commit messages: Start with a verb, keep subject specific, and reference changed area when useful.
- PRs should include: purpose, files changed, navigation impact, and screenshots for visible UI/docs layout changes.
- Link related issues/tasks and note any follow-up documentation work.
