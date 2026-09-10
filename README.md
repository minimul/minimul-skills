# Skills

A collection of agent skills. Each skill lives in its own directory and is defined by a `SKILL.md` file with a name, description, and usage guidance.

## Skills

- [interactive-explainer](./interactive-explainer) — Builds self-contained, offline HTML pages that explain bugs, fixes, data shapes, or design decisions using real codebase details.

## Usage

Skills are automatically discovered from this directory. Invoke the interactive explainer by asking things like:

- "Make an interactive HTML explaining this bug"
- "Visualize this fix"

Output is written to the project's `tmp/` directory and can be opened directly from `file://`.
