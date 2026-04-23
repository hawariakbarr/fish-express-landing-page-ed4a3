# Technology Stack

**Analysis Date:** 2026-04-23

## Languages

**Primary:**
- HTML5 - Full page markup and structure (`fishexpress-website.html`)
- CSS3 - All styling including custom properties, grid, flexbox, animations, `color-mix()`, `clamp()`, `backdrop-filter` (`fishexpress-website.html` lines 11–806)
- JavaScript (vanilla ES6+) - All interactivity: i18n, theme toggle, scroll animations, IntersectionObserver (`fishexpress-website.html` lines 1265–1439)

**Secondary:**
- SVG - Inline logo and icon graphics embedded directly in HTML (lines 813–830, 846–848)

## Runtime

**Environment:**
- Browser - Static HTML file served directly; no server runtime required

**Package Manager:**
- None - No package manager, no lockfile; all assets are either inlined or loaded from CDN

## Frameworks

**Core:**
- None - Pure vanilla HTML/CSS/JavaScript; no UI framework or library

**CSS Approach:**
- Custom properties (CSS variables) with dual light/dark themes via `data-theme` attribute on `<html>`
- No CSS preprocessor (no Sass, Less, PostCSS)
- No utility-first framework (no Tailwind, Bootstrap)

**Build/Dev:**
- None - No build step; the file is the final artifact

## Key Dependencies

**Fonts (CDN):**
- Google Fonts — `Fraunces` (serif, used for display headings and logo) — loaded from `https://fonts.googleapis.com`
- Google Fonts — `Plus Jakarta Sans` (sans-serif, body and UI text) — loaded from `https://fonts.googleapis.com`
- Preconnect hints to `fonts.googleapis.com` and `fonts.gstatic.com` (lines 8–10)

**Images:**
- All product and gallery images are embedded as inline Base64-encoded JPEG data URIs — no external image hosting dependency
- Example occurrences at lines: 904, 911, 945, 961, 977, 993, 1009, 1025, 1122, 1126, 1130, 1134, 1138, 1142, 1146, 1150

## Configuration

**Environment:**
- No environment variables — fully self-contained static file
- No server configuration required

**Build:**
- No build config files; the single HTML file is deployed as-is

**Browser Storage:**
- `localStorage` keys used at runtime:
  - `fe-lang` — persists selected language (`id` or `en`)
  - `fe-theme` — persists selected color theme (`light` or `dark`)

## Platform Requirements

**Development:**
- Any text editor; no toolchain setup required
- A browser for preview

**Production:**
- Any static file host (e.g., Nginx, GitHub Pages, Netlify, Vercel, shared hosting)
- No server-side language, database, or build pipeline required
- HTTPS recommended to avoid mixed-content warnings from Google Fonts CDN

---

*Stack analysis: 2026-04-23*
