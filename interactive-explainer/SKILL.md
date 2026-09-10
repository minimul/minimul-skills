---
name: interactive-explainer
description: This skill should be used when the user asks to "make an interactive HTML", "build an interactive explainer", "visualize this bug/fix", or wants a self-contained HTML page that explains a bug, fix, data shape, or design decision in the codebase.
user-invocable: true
---

# Interactive HTML Explainer Skill

## Non-negotiables

1. **Self-contained & offline.** One `.html` file, inline `<style>`/`<script>`, zero network deps (no CDN, no Mermaid, no web fonts). Must render from `file://`.
2. **Ground every claim in the real codebase.** Explore first; use actual schema columns, real `file:line`, real counts, real code. Never invent row shapes or numbers — read them. If a value can't be verified, say so on the page.
3. **Portability.** No emoji or unicode arrows inside labels (use `&rarr;` or words). Dark theme, system font.

## Build steps

1. Identify what to explain (bug / fix / data / decision) and its real source.
2. Pull concrete details with Read/Grep/Bash — column types, line numbers, exact counts, before/after code — and cite them.
3. Pick interactive devices that fit (compose, don't use all):
   - **Before/After toggle** — buggy vs fixed (flow, rows, or rendered UI).
   - **Tab nav** — one section per concern (bug / data / fix / tests).
   - **Path simulator** — a button per scenario showing the resulting state.
   - **Clickable data bars** — each metric explains itself on click.
   - **Real-UI mock / DB-row tables** — render literal rows through the real view logic; highlight the broken cells.
4. Write to the project's `tmp/` directory as `tmp/*-<topic>.html` (for a Rails app that's `Rails.root/tmp`; scratch, already git-ignored — never the repo root). State the `file://` path to open it.

## Anti-patterns

- CDN-loaded libraries (breaks offline).
- Invented data instead of the real values.
- No toggles/tabs/simulator — that's a doc, not this skill.
- Committing as documentation without asking.
