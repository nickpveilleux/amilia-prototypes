# Amilia Prototypes

Rapid HTML prototyping toolkit for Amilia product design. Pure HTML/CSS/JS — no build step.

## Context Loading

**Don't front-load context.** Read what you need, when you need it.

- `design-system/rules.md` — **before building anything** (hard constraints, tech rules, Figma workflow)
- `design-system/tokens.md` — when checking which token to use
- `design-system/patterns/<pattern>.md` — when building that specific pattern
- `design-system/principles.md` — when making judgment calls on layout or interaction
- `design-system/index.md` — for a full overview of what's documented

## Structure

```
components/              # Reusable HTML/CSS components (one file per component)
tokens/
  tokens.css             # CSS custom properties — single source of truth
  reset.css              # Base reset with Amilia typography defaults
templates/
  base.html              # Standard page wrapper (includes tokens + reset)
prototypes/              # One folder per project prototype
  <project-name>/
    index.html
design-system/           # Design system rules, tokens reference, patterns
  rules.md               # Hard rules — read before building
  tokens.md              # Token usage guide
  principles.md          # Design principles
  patterns/              # UI pattern docs (cards, tables, forms, nav, etc.)
index.html               # Gallery page linking to all prototypes
```

## Creating a New Prototype

1. Read `design-system/rules.md`
2. Create `prototypes/<project-name>/index.html` from `templates/base.html`
3. Read relevant pattern docs in `design-system/patterns/`
4. Reuse existing components from `components/`; create new ones if needed
5. Add an entry to root `index.html` gallery

## Cross-Repo Context

Research and task context live in the Emira vault:
- **Path:** `/Users/nicolasveilleux/Library/CloudStorage/Dropbox/Emira`
- **Research:** `areas/amilia/projects/<project>/`
- **Tasks:** `tasks/` or `emira/tasks.md`

When asked to prototype from research, read the relevant Emira files first.

## GitHub Pages

Shareable URLs: `https://nickpveilleux.github.io/amilia-prototypes/prototypes/<project-name>/`
