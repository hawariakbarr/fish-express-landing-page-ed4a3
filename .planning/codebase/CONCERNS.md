# Concerns
<!-- Generated: 2026-04-23 -->

## Tech Debt

| Severity | Item |
|---|---|
| High | **Monolithic single-file architecture** — all HTML/CSS/JS/images in one 437 KB file; impossible to cache assets independently or parallelize loading |
| High | **16 inline base64 JPEG images** (lines 904–1150) — no browser caching, forces full re-download on every page visit |
| Medium | **WhatsApp phone number hardcoded in 5 places** — changing the number requires finding all instances manually |
| Low | **Duplicated SVG logo** — same SVG appears in nav and footer; no shared symbol |
| Low | **i18n key duplication** — no completeness check; missing keys fail silently (render empty string) |

## Known Bugs

| Severity | Item |
|---|---|
| High | **Mobile hamburger menu has no JS handler** — button is rendered but clicking it does nothing; mobile users cannot navigate |
| Medium | **`applyLang()` uses `textContent` on strings with HTML entities** — strings containing `&amp;`, `<`, `>` will render as literal text rather than markup |
| Medium | **Scroll reveal sets `opacity: 0` inline on init** — if JS fails or is disabled, page content is invisible |

## Security

| Severity | Item |
|---|---|
| Low | **External links missing `rel="noreferrer"`** — allows referrer leakage to third-party sites |
| Low | **No Content Security Policy** — no CSP header or meta tag |

## Performance

| Severity | Item |
|---|---|
| High | **437 KB HTML payload** — almost entirely caused by base64-encoded images; should be external files |
| High | **No `loading="lazy"` on any image** — all 16 images load on page init regardless of viewport |
| Medium | **Google Fonts without preload** — no `<link rel="preload">` for font files; fonts block render |
| Low | **`color-mix()` without fallback** — 9 occurrences; colors invisible on Chrome <111, Firefox <113, Safari <16.2 |

## Accessibility

| Severity | Item |
|---|---|
| High | **Mobile nav completely inaccessible** — no ARIA states, no keyboard handler, no open/close JS logic |
| High | **No `<main>` landmark** — screen readers cannot skip to main content |
| Medium | **Gallery images missing `alt` attributes** — visual content not described for screen readers |
| Medium | **Hero `h1` hidden by animation with no `prefers-reduced-motion` fallback** — content invisible to users with motion sensitivity |
| Low | **Contact emoji icons not hidden from screen readers** — decorative emojis read aloud |

## Maintainability

| Item |
|---|
| No OG/social meta tags (Open Graph, Twitter Card) — poor link preview when shared |
| No favicon |
| No structured data (JSON-LD) for SEO |
| Hardcoded business stats (numbers, years) — no CMS or data layer |
| Zero automated tests — all changes require full manual QA |
