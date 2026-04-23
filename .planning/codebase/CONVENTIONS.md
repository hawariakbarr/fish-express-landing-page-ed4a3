# Conventions
<!-- Generated: 2026-04-23 -->

## General

Single HTML file (`fishexpress-website.html`, 1442 lines) — all HTML, CSS, and JS colocated. No build tools, no preprocessors.

## CSS Conventions

### Naming
- Lowercase kebab-case, BEM-lite: `hero-grid`, `product-card`, `hero-card-overlay`
- Modifier classes appended directly: `featured`, `active`, `hc-1`/`hc-2`/`hc-3`

### Design Tokens
- All colors via CSS custom properties on `:root[data-theme="light/dark"]`
- Tokens: `--teal`, `--ink`, `--paper`, `--yellow`, `--cream`, etc.

### Dark Mode
- `:root[data-theme="dark"] .component` attribute-selector overrides per component
- Applied via `applyTheme(theme)` which sets `data-theme` on `<html>`
- Not consolidated into a single block — overrides are colocated with each component

### Responsive
- Three `max-width` breakpoints: `1024px`, `968px`, `560px`
- All responsive rules in a single RESPONSIVE section at end of `<style>`

### Typography
- Fluid sizing via `clamp()` — e.g. `clamp(48px, 7vw, 92px)` for hero `h1`
- `Fraunces` (serif, display/headings) + `Plus Jakarta Sans` (sans-serif, body/UI)

### Section Delimiters
- `/* ===== SECTION NAME ===== */` used consistently to separate CSS regions

## JavaScript Conventions

### Module Structure
- Single `<script>` block at bottom of `<body>`
- All initialization inside `DOMContentLoaded`
- Sections delimited with `/* ===== SECTION NAME ===== */`

### Naming
- camelCase function names: `applyLang()`, `applyTheme()`
- Flat i18n dictionary with dot-notation keys: `'nav.products': 'Produk'`

### i18n Pattern
- `data-i18n` attribute → sets `textContent`
- `data-i18n-html` attribute → sets `innerHTML`
- Language persisted to `localStorage` key `fe-lang`

### Error Handling
- All `localStorage` calls wrapped in `try/catch(e){}` for private-mode safety
- No other explicit error handling needed (no network requests)

### Animation
- `IntersectionObserver` for scroll-reveal, `threshold: 0.08`
- Unobserves after first trigger (one-shot animation)

## HTML Conventions

- All `<img>` elements have descriptive `alt` text
- `aria-label` on all icon buttons
- `role="group"` and `aria-hidden` used on decorative elements
- 16 base64-encoded JPEG images embedded inline (accounts for ~437KB file size)
