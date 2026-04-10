# Design Tokens Reference

All tokens are defined in `tokens/tokens.css` as CSS custom properties. This doc explains when to use each one.

Source of truth: Figma file `cXUsKsRJfBbIbjXVL7np9A`

## Colors

### Primary

| Token | Value | When to use |
|-------|-------|-------------|
| `--color-primary` | #186DDC | Buttons, links, active states, selected items |
| `--color-admin` | #E67300 | Store admin mode, editing indicators |
| `--color-sidebar` | #30383E | Sidebar / navigation background |

### Backgrounds

| Token | Value | When to use |
|-------|-------|-------------|
| `--color-bg` | #EEF4F6 | Page background — always |
| `--color-bg-white` | #FFFFFF | Card background, content areas, modals |
| `--color-stripes` | #F8F8F8 | Table alternating row stripes |

### Lines / Dividers

| Token | Value | When to use |
|-------|-------|-------------|
| `--color-header-line` | #C2C2C2 | Header divider lines |
| `--color-content-line` | #CED4DA | Content dividers, table borders, form field borders |

### Text

| Token | Value | When to use |
|-------|-------|-------------|
| `--color-text-heading` | #0F1111 | Headings, titles, prices, button labels |
| `--color-text-body` | #222626 | Body paragraph text |
| `--color-text-placeholder` | #535353 | Placeholders, tooltips |
| `--color-text-help` | #707070 | Help text, secondary labels, captions |
| `--color-text-inverse` | #FFFFFF | Text on dark backgrounds (sidebar, buttons) |

### Status

| Token | Value | When to use |
|-------|-------|-------------|
| `--color-success` | #00802F | Success states, confirmations, positive badges |
| `--color-in-progress` | #FEC11B | In-progress indicators, pending states |
| `--color-warning` | #D68100 | Warnings, caution states |
| `--color-error` | #DE1316 | Errors, destructive actions, validation failures |
| `--color-inactive` | #E4E4E4 | Disabled states, inactive items |
| `--color-badge-bg` | #CBE1F3 | Informative badge backgrounds |
| `--color-info-tip` | #183252 | Info tip icons |

### Tags

Used for categorization labels, multi-select tags, color-coded identifiers:

`--color-tag-brown`, `--color-tag-turquoise-light`, `--color-tag-turquoise-dark`, `--color-tag-pink-dark`, `--color-tag-purple-light`, `--color-tag-yellow-light`, `--color-tag-purple-dark`, `--color-tag-yellow-dark`, `--color-tag-pink-light`

## Typography

**Font:** Noto Sans (loaded via Google Fonts in `tokens.css`)

### Headings

All headings: semibold (600), line-height 1.5, color `--color-text-heading`.

| Element | Token | Size |
|---------|-------|------|
| `h1` | `--text-h1` | 35px |
| `h2` | `--text-h2` | 28px |
| `h3` | `--text-h3` | 24.5px |
| `h4` | `--text-h4` | 21px |
| `h5` | `--text-h5` | 17.5px |
| `h6` | `--text-h6` | 14px |

### Body

| Style | Size | Weight | When to use |
|-------|------|--------|-------------|
| Body regular | 14px | 400 | Default paragraph text |
| Body bold | 14px | 700 | Emphasis, labels, table headers |

## Spacing

4px base grid. Always use tokens, never arbitrary values.

| Token | Value | Common usage |
|-------|-------|-------------|
| `--space-1` | 4px | Tight gaps, icon padding |
| `--space-2` | 8px | Between related items, compact lists |
| `--space-3` | 12px | Form field gaps, small section spacing |
| `--space-4` | 16px | Default gap between elements |
| `--space-5` | 20px | Medium section spacing |
| `--space-6` | 24px | Card padding, section gaps |
| `--space-8` | 32px | Large section spacing |
| `--space-10` | 40px | Page padding |
| `--space-12` | 48px | Major section breaks |
| `--space-16` | 64px | Page-level vertical spacing |

## Border Radius

| Token | Value | Usage |
|-------|-------|-------|
| `--radius` | 4px | Everything. Cards, buttons, inputs, badges, modals. |

## Shadows

| Token | Value | Usage |
|-------|-------|-------|
| `--shadow-card` | `0 2px 5px 0 #D3D3D3` | Cards. The only shadow in the system. |

## Layout

| Token | Value | Usage |
|-------|-------|-------|
| `--padding-screen` | 40px | Page-level padding |
| `--padding-card` | 24px | Card internal padding |
| `--max-width-content` | 1200px | Content area max width |
| `--sidebar-width` | 260px | Sidebar navigation width |
| `--header-height` | 56px | Top header bar height |
