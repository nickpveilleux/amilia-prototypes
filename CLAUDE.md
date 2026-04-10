# Amilia Prototypes

Rapid HTML prototyping toolkit for Amilia product design. Pure HTML/CSS/JS — no build step.

## Purpose

Turn research and design explorations into shareable, high-fidelity HTML prototypes fast. Each prototype reuses a growing component library styled to match Amilia's design system.

## Structure

```
components/          # Reusable HTML/CSS components (one file per component)
tokens/              # Design tokens (colors, spacing, typography, shadows)
  tokens.css         # CSS custom properties
templates/           # Page shells and layouts
  base.html          # Standard page wrapper (includes tokens + reset)
prototypes/          # One folder per project prototype
  <project-name>/
    index.html       # Entry point
    ...
index.html           # Gallery page linking to all prototypes
```

## Conventions

- **No build tools.** Plain HTML, CSS, vanilla JS only. Must open in a browser with no server.
- **Components** are standalone HTML files with embedded `<style>` tags. Import via copy or `<link>` to extracted CSS.
- **tokens/tokens.css** is the single source of truth for design tokens. Every component and prototype references these variables.
- **File paths are relative.** Prototypes link to `../../tokens/tokens.css` and `../../components/` so they work from the file system.
- **One folder per prototype.** Named after the project (e.g., `smart-search`, `people-profile`). Each has its own `index.html`.
- **index.html at root** is the gallery — update it when adding a new prototype.

## Creating a New Prototype

1. Create `prototypes/<project-name>/index.html`
2. Use `templates/base.html` as the starting point
3. Link to `../../tokens/tokens.css` for design tokens
4. Reuse existing components; create new ones in `components/` if needed
5. Add an entry to the root `index.html` gallery

## Cross-Repo Context

Research, briefs, and task context live in the Emira vault:
- **Path:** `/Users/nicolasveilleux/Library/CloudStorage/Dropbox/Emira`
- **Research:** `areas/amilia/projects/<project>/` — look for research syntheses, briefs, context docs
- **Tasks:** `tasks/` or `emira/tasks.md` — may contain prototype requests

When asked to prototype from research, read the relevant Emira files for context before building.

## Design Tokens

Tokens will be populated from Amilia's Figma design system. Until then, use sensible defaults in `tokens/tokens.css` and flag them as placeholders.

## GitHub Pages

Prototypes are hosted via GitHub Pages from the `main` branch root. Shareable URLs follow:
`https://nickpveilleux.github.io/amilia-prototypes/prototypes/<project-name>/`
