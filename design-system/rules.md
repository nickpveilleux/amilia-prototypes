# Design System Rules

Hard rules that apply to every component and prototype. No exceptions.

## Technology

- **No build tools.** Plain HTML, CSS, vanilla JS only. Must open in a browser with no server.
- **No frameworks.** No React, no Tailwind, no Bootstrap. Semantic HTML + CSS custom properties.
- **No inline styles** unless for truly dynamic JS-driven values.

## Tokens

- IMPORTANT: Never hardcode hex colors. Always use `var(--color-*)` from `tokens/tokens.css`.
- IMPORTANT: Never hardcode font names. Always use `var(--font-family)`.
- IMPORTANT: Never hardcode spacing values. Always use `var(--space-*)` tokens on the 4px grid.
- IMPORTANT: Always use `var(--radius)` (4px) for border radius. There is only one radius value.
- IMPORTANT: Always use `var(--shadow-card)` for card shadows. There is only one shadow.

## Components

- Before creating a new component, check `components/` for an existing one.
- Each component is one file in `components/` with embedded `<style>` tags.
- Components must reference `tokens.css` variables — never hardcode values.
- Name components in kebab-case: `button.html`, `data-table.html`, `status-badge.html`.
- Components should be self-contained and copy-pasteable into any prototype.

## Styling

- Use semantic class names (`.card`, `.sidebar`, `.status-badge`), not utility classes.
- Prototype-specific styles go in a `<style>` block in the prototype's HTML.
- Responsive design via CSS media queries when needed.

## Figma MCP Workflow

When implementing from a Figma link or design:

1. **Always** run `get_design_context` first to fetch the structured node data.
2. If the response is truncated, run `get_metadata` for the node map, then re-fetch specific children.
3. Run `get_screenshot` for visual reference.
4. Translate output (React + Tailwind) into **plain HTML + CSS custom properties**.
5. Validate against the Figma screenshot for 1:1 visual parity.

## Asset Handling

- If the Figma MCP server returns a source URL for an image or SVG, use it directly.
- DO NOT import or add new icon packages — assets come from the Figma payload.
- DO NOT use or create placeholders if a source is provided.
- Store downloaded assets in the prototype's folder: `prototypes/<name>/assets/`.

## Prototypes

- One folder per prototype in `prototypes/`, named after the project.
- Always start from `templates/base.html`.
- Always link to `../../tokens/tokens.css` and `../../tokens/reset.css`.
- Always add an entry to the root `index.html` gallery when creating a new prototype.

## When a Pattern Doesn't Exist

If you need a pattern that isn't documented in `design-system/patterns/`:
- Flag it to the user before inventing a convention.
- Do not guess at layout rules, interaction patterns, or component anatomy.
- Use the closest existing pattern as a starting point and note deviations.
