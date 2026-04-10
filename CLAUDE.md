# Amilia Prototypes

Rapid HTML prototyping toolkit for Amilia product design. Pure HTML/CSS/JS — no build step.

## Purpose

Turn research and design explorations into shareable, high-fidelity HTML prototypes fast. Each prototype reuses a growing component library styled to match Amilia's design system.

## Structure

```
components/          # Reusable HTML/CSS components (one file per component)
tokens/              # Design tokens (colors, spacing, typography, shadows)
  tokens.css         # CSS custom properties — single source of truth
  reset.css          # Base reset with Amilia typography defaults
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
3. Link to `../../tokens/tokens.css` and `../../tokens/reset.css` for design tokens
4. Reuse existing components; create new ones in `components/` if needed
5. Add an entry to the root `index.html` gallery

## Cross-Repo Context

Research, briefs, and task context live in the Emira vault:
- **Path:** `/Users/nicolasveilleux/Library/CloudStorage/Dropbox/Emira`
- **Research:** `areas/amilia/projects/<project>/` — look for research syntheses, briefs, context docs
- **Tasks:** `tasks/` or `emira/tasks.md` — may contain prototype requests

When asked to prototype from research, read the relevant Emira files for context before building.

## GitHub Pages

Prototypes are hosted via GitHub Pages from the `main` branch root. Shareable URLs follow:
`https://nickpveilleux.github.io/amilia-prototypes/prototypes/<project-name>/`

---

## Design System Rules

IMPORTANT: Follow these rules for every component and prototype. They encode Amilia's design system and must not be overridden.

### Figma MCP Integration

When implementing from a Figma link or design:

1. **Always** run `get_design_context` first to fetch the structured node data
2. If the response is truncated, run `get_metadata` to get the node map, then re-fetch specific child nodes
3. Run `get_screenshot` for a visual reference
4. Only after you have both context and screenshot, download any assets and start implementation
5. Translate the output (React + Tailwind) into **plain HTML + CSS custom properties** — never use React or Tailwind in this repo
6. Validate against the Figma screenshot for 1:1 visual parity before marking complete

### Colors

IMPORTANT: Never hardcode hex colors. Always use `var(--color-*)` tokens from `tokens/tokens.css`.

| Token | Value | Usage |
|-------|-------|-------|
| `--color-primary` | #186DDC | Primary blue — buttons, links, active states |
| `--color-admin` | #E67300 | Store admin / editing mode |
| `--color-sidebar` | #30383E | Sidebar / navigation background |
| `--color-bg` | #EEF4F6 | Page background |
| `--color-bg-white` | #FFFFFF | Card / content background |
| `--color-header-line` | #C2C2C2 | Header divider lines |
| `--color-content-line` | #CED4DA | Content divider lines |
| `--color-stripes` | #F8F8F8 | Table alternating row stripes |

**Text colors:**

| Token | Value | Usage |
|-------|-------|-------|
| `--color-text-heading` | #0F1111 | Headings, titles, prices, button labels |
| `--color-text-body` | #222626 | Body paragraph text |
| `--color-text-placeholder` | #535353 | Placeholders, tooltips |
| `--color-text-help` | #707070 | Help text, secondary labels |
| `--color-text-inverse` | #FFFFFF | Text on dark backgrounds |

**Status colors:** `--color-success`, `--color-in-progress`, `--color-warning`, `--color-error`, `--color-inactive`, `--color-badge-bg`, `--color-info-tip`

**Tag colors:** `--color-tag-brown`, `--color-tag-turquoise-light`, `--color-tag-turquoise-dark`, `--color-tag-pink-dark`, `--color-tag-purple-light`, `--color-tag-yellow-light`, `--color-tag-purple-dark`, `--color-tag-yellow-dark`, `--color-tag-pink-light`

### Typography

- **Font:** Noto Sans (loaded via Google Fonts in `tokens.css`)
- **Body:** 14px, weight 400, line-height 1.5
- **Body bold:** 14px, weight 700
- **Headings:** all semibold (600), line-height 1.5

| Element | Token | Size |
|---------|-------|------|
| `h1` | `--text-h1` | 35px |
| `h2` | `--text-h2` | 28px |
| `h3` | `--text-h3` | 24.5px |
| `h4` | `--text-h4` | 21px |
| `h5` | `--text-h5` | 17.5px |
| `h6` | `--text-h6` | 14px |
| body | `--text-body` | 14px |

IMPORTANT: Always use `var(--font-family)` — never hardcode font names.

### Spacing

4px base grid. IMPORTANT: Always use `var(--space-*)` tokens, never arbitrary pixel values.

| Token | Value |
|-------|-------|
| `--space-1` | 4px |
| `--space-2` | 8px |
| `--space-3` | 12px |
| `--space-4` | 16px |
| `--space-5` | 20px |
| `--space-6` | 24px |
| `--space-8` | 32px |
| `--space-10` | 40px |
| `--space-12` | 48px |
| `--space-16` | 64px |

### Border Radius

IMPORTANT: Always use `var(--radius)` (4px). There is only one radius value — do not invent others.

### Shadows

- **Cards:** `var(--shadow-card)` → `0 2px 5px 0 #D3D3D3`
- This is the only shadow. Do not invent additional shadow levels.

### Layout

| Token | Value | Usage |
|-------|-------|-------|
| `--padding-screen` | 40px | Page-level padding around content |
| `--padding-card` | 24px | Internal padding for cards |
| `--max-width-content` | 1200px | Maximum content width |
| `--sidebar-width` | 260px | Sidebar navigation width |
| `--header-height` | 56px | Top header bar height |

### Cards

Every card must follow this pattern:
```css
.card {
  background: var(--color-bg-white);
  border-radius: var(--radius);
  box-shadow: var(--shadow-card);
  padding: var(--padding-card);
}
```

### Page Layout

Every prototype page must follow this pattern:
```css
body {
  background: var(--color-bg);
}

.page-content {
  padding: var(--padding-screen);
  max-width: var(--max-width-content);
}
```

### Asset Handling

- IMPORTANT: If the Figma MCP server returns a localhost source for an image or SVG, use that source directly
- IMPORTANT: DO NOT import or add new icon packages — all assets should come from the Figma payload
- IMPORTANT: DO NOT use or create placeholders if a localhost source is provided
- Store downloaded assets in the prototype's folder (e.g., `prototypes/project-name/assets/`)

### Component Rules

- IMPORTANT: Before creating a new component, check `components/` for an existing one
- Components are plain HTML + CSS. No frameworks, no build tools.
- Each component is one file in `components/` with embedded `<style>` tags
- Components must reference `tokens.css` variables — never hardcode values
- Name components in kebab-case: `button.html`, `data-table.html`, `status-badge.html`
- Components should be self-contained and copy-pasteable into any prototype

### Styling Rules

- IMPORTANT: Never use inline styles unless for truly dynamic JS-driven values
- IMPORTANT: Never use Tailwind, Bootstrap, or any CSS framework
- Use CSS custom properties from `tokens/tokens.css` for all design values
- Use semantic class names (`.card`, `.sidebar`, `.status-badge`), not utility classes
- Responsive design via CSS media queries when needed
- Prototype-specific styles go in a `<style>` block in the prototype's HTML
