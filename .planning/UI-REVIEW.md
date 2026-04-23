# UI Review — Fish Express Landing Page

**Audited:** 2026-04-23
**Baseline:** Abstract 6-pillar standards (no UI-SPEC.md)
**Screenshots:** Not captured — no dev server detected on ports 3000, 5173, 8080

---

## Overall Score: 17/24

| Pillar | Score | Grade |
|---|---|---|
| Copywriting | 4/4 | Excellent |
| Visuals | 3/4 | Good |
| Color | 3/4 | Good |
| Typography | 2/4 | Needs Work |
| Spacing | 3/4 | Good |
| Experience Design | 2/4 | Needs Work |

---

## Top Priority Fixes

1. **Mobile nav has no hamburger button in HTML and no JS handler** — Mobile users (below 1024px) see the nav links hidden via CSS and no mechanism to access them, making all navigation unreachable — Add a `<button class="menu-toggle" aria-label="Open navigation" aria-expanded="false">` element inside `<nav>`, add a `.nav-links.open { display: flex; }` CSS rule, and wire a click handler in the `DOMContentLoaded` block that toggles `aria-expanded` and the `.open` class.

2. **25 distinct font-size values with no coherent type scale** — The CSS defines sizes from 11px to 280px with no repeating pattern or scale step (e.g., 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 22, 26, 28, 34, 36, 38, 42, 44, 48, 60, 72, 280px) — consolidate to a 7-step scale: `--text-xs: 12px`, `--text-sm: 14px`, `--text-base: 16px`, `--text-md: 18px`, `--text-lg: 22px`, `--text-xl: 28px`, `--text-2xl: clamp(38px, 5vw, 64px)` and apply these tokens throughout.

3. **Scroll-reveal JS sets `opacity: 0` with no `prefers-reduced-motion` guard** — Users who have requested reduced motion in their OS settings will see content invisible until it intersects, and the animation itself fires anyway — Wrap the `IntersectionObserver` setup in `if (!window.matchMedia('(prefers-reduced-motion: reduce)').matches)` and skip setting `opacity: 0` / `transform` when the user has opted out.

---

## Copywriting — 4/4

### Strengths
- Hero headline is specific and benefit-driven: "Filet ikan premium untuk keluarga sehat & bisnis kuliner" — no generic taglines.
- CTAs are action-specific with destination context: "Pesan Sekarang", "Lihat Produk", "Order untuk rumah →", "Daftar reseller →". The arrow character reinforces forward motion without generic "Click Here" patterns.
- Pre-filled WhatsApp message URLs (lines 1060, 1075) are contextual — the B2C link pre-populates "saya mau pesan untuk kebutuhan rumah" and the B2B link uses "saya tertarik dengan program reseller/wholesale". This is excellent microcopy that reduces friction.
- Bilingual i18n dictionary (ID and EN) is complete and consistent. No missing keys were found for any element. EN translations are natural, not machine-like.
- Social proof stats are specific (years, follower count, post count, delivery days) rather than vague ("thousands of happy customers").
- The gallery section sub-heading "Update menu, promo, dan bazar kami secara real-time di Instagram @fishexpress_id" sets accurate user expectations.
- Product descriptions lead with differentiators: "tanpa duri", "tanpa pengawet", "tanpa MSG" — negative claims that build trust for the target audience (parents, health-conscious buyers).

### Issues
- None identified. No generic "Submit", "Click Here", or "Learn More" labels present. No empty or error states apply to this static page.

---

## Visuals — 3/4

### Strengths
- Hero uses a layered card collage (`.hc-1`, `.hc-2`, `.hc-3`) with deliberate rotation angles (−4°, +5°, −2°) and `z-index` stacking, creating depth without a full-bleed image.
- The marquee strip (line 928, `aria-hidden="true"`) adds kinetic texture between the hero and product sections without distracting from content.
- Audience cards use strong background color differentiation (yellow gradient for B2C, teal-to-deep-teal for B2B) with decorative oversized text ("B2C"/"B2B" at `font-size: 280px`, `opacity: 0.1`) as a visual anchor.
- The `why-num` numerals (72px Fraunces italic, `opacity: 0.3`) establish visual rhythm in the four-column "why" grid.
- Gallery uses square aspect-ratio cards in a 4-column grid with hover scale + overlay — consistent with Instagram content display patterns.
- All 16 images have meaningful `alt` attributes (e.g., "Fish Express catfish fillet vacuum packs", "Homemade Fish Nugget Alphabet").

### Issues
- The `.menu-toggle` button is defined in CSS (`display: block` at ≤1024px) but **the HTML element does not exist in the `<nav>` body** — there is no `<button class="menu-toggle">` in the markup. Mobile users see neither nav links nor a toggle button.
- The `float-fish` emoji elements (`.f1`, `.f2` at `opacity: 0.12`) are decorative fish characters that float in the hero background. They are not hidden from screen readers — should have `aria-hidden="true"`.
- Gallery images on lines 1122–1150 (the 8 gallery grid items) have no `alt` attributes at all, confirmed by the grep results. Product card images (lines 945–1009) have appropriate alts; gallery images do not.
- No favicon referenced in `<head>`, reducing brand recognition in browser tabs and bookmarks.

---

## Color — 3/4

### Strengths
- A well-structured dual-theme system using CSS custom properties with `:root[data-theme="light"]` and `:root[data-theme="dark"]` — color changes are centralized in the token layer, not scattered.
- 60/30/10 ratio is broadly respected: `--paper` / `--cream` dominates backgrounds (60%), `--ink` / `--teal` frame structural elements (30%), `--yellow` / `--coral` are accent-only (10%).
- Accent color `--teal` is consistently used for interactive states: nav link underline, btn-primary background, product card hover border, stat numbers, section eyebrows. No random accent usage.
- Dark mode inverts the color relationships intelligently — the footer swaps from `--ink` background to `--cream` background, maintaining contrast without a pure-black/pure-white scheme.
- Text selection color (line 54: `::selection { background: var(--yellow); color: #1A1B1F; }`) is a polished detail.

### Issues
- `color-mix(in srgb, ...)` is used in 9 places (lines 62, 131, 138, 213, 219, 391, 605, 618, 701) with no fallback values. Chrome <111, Firefox <113, and Safari <16.2 will render these colors as invisible (transparent). Affected elements include the nav blur background, hero blob backgrounds, button shadow, product card hover shadow, and contact card hover shadow. Fix: precede each `color-mix()` value with a plain `rgba()` fallback.
- Product badge colors are applied as inline styles (`style="background: var(--teal); color: white;"` on lines 961, 978 etc.) rather than modifier classes. This is inconsistently applied — "Best Seller" badge uses `.featured` class (line 949) but subsequent badges use inline styles. Should be standardized to a class-based modifier system (`.product-image-badge--teal`, etc.).
- External links (`rel="noopener"` only, lines 1121–1155, 1210, 1215) are missing `noreferrer`, which allows referrer leakage to Instagram and Linktree. Change to `rel="noopener noreferrer"`.

---

## Typography — 2/4

### Strengths
- The two-font pairing (Fraunces serif for display/headings, Plus Jakarta Sans sans-serif for body) is a strong contrast: expressive editorial vs. legible UI.
- `clamp()` is used correctly for fluid typography on the three primary headings (hero h1, section h2, contact h2), preventing fixed-size overflow on narrow viewports.
- The use of Fraunces italic (`font-style: italic`) on `em` elements within headings creates visual emphasis without relying solely on weight or color.
- Base body line-height of 1.6 (line 50) is appropriate for reading comfort.

### Issues
- **25 distinct font-size values** are defined in CSS (see full list below), far exceeding a manageable type scale. There is no underlying scale relationship (no consistent ratio like 1.25x or 1.333x between steps).
  - Body-range sizes: 11px, 12px, 13px, 14px, 15px, 16px, 17px, 18px, 19px, 20px
  - Mid-range: 22px, 26px, 28px
  - Display-range: 34px, 36px, 38px, 42px, 44px, 48px, 60px, 72px
  - Decorative: 280px (audience background text)
  - Fluid: `clamp(48px, 7vw, 92px)`, `clamp(48px, 7vw, 84px)`, `clamp(38px, 5vw, 64px)`
- Five font-weight values are used: 500, 600, 700, 800, 900 — the 900-weight (`audience-bg-decor`) and 800-weight (`hero-title`) are valid for display use, but 500/600/700 all appear on body text without a clear role distinction, making the weight system ambiguous.
- The `stat-num` font-size is 38px (a one-off value) — it sits between the `section-title` clamp range and body sizes without a clear scale position.
- `font-size: 34px` is only used inside the SVG logo's `<text>` element — not part of the CSS type scale but visually prominent.

---

## Spacing — 3/4

### Strengths
- Section-level vertical rhythm is disciplined: `section.block` uses `padding: 120px 32px` universally, the hero uses `padding: 140px 32px 80px`, the delivery section uses `padding: 100px 32px`, and the contact section uses `padding: 120px 32px`. All use the same 32px horizontal gutter, establishing consistent lateral boundaries.
- Responsive breakpoints correctly reduce section padding: at ≤968px sections shift to `padding: 80px 24px`, and at ≤560px the nav shifts to `padding: 14px 20px` — a coherent step-down.
- Gap values in grid layouts are consistent at the component level: `gap: 24px` for product grid, `gap: 28px` for audience grid, `gap: 32px` for why grid — a 4px increment pattern.
- The hero stats use `margin-top: 60px` and `padding-top: 32px` with a 1px border separator — a clean visual break within the hero content column.

### Issues
- Section-level vertical padding values (100px, 120px, 140px) use raw pixel values rather than a CSS custom property token. If the design rhythm needs adjustment, all three must be found and changed manually. Define `--section-pad-v: 120px` and use it consistently.
- Component-level padding shows no underlying scale: card bodies use `padding: 28px 28px 32px` (asymmetric vertical), audience cards use `padding: 56px 48px`, delivery card uses `padding: 72px 64px`. These values are ad-hoc rather than derived from a base unit. An 8px base unit grid would produce cleaner values (48, 56, 64, 72 are 8px-aligned, but 28px and 32px in the same shorthand breaks it).
- One inline style contains a raw pixel value: `style="font-size: 20px;"` on `.hc-3 .hc-title` (line 920) — this bypasses the type scale entirely.

---

## Experience Design — 2/4

### Strengths
- Theme persistence via `localStorage` with a `try/catch` guard (lines 1394–1396) is correctly implemented. Falls back to `prefers-color-scheme` media query on first visit.
- Language persistence via `localStorage` with `try/catch` is similarly robust.
- Smooth anchor scroll is implemented for all `a[href^="#"]` elements with `behavior: 'smooth'`.
- Scroll-reveal `IntersectionObserver` uses `threshold: 0.08` (triggers at 8% visibility) and correctly calls `io.unobserve()` after animation — prevents re-firing.
- All nav control buttons have `aria-label` attributes (lines 843–845): language buttons identify the locale, theme button says "Toggle dark mode".
- WhatsApp CTAs use pre-filled message text appropriate to context (B2C vs. B2B), reducing user effort.
- `rel="noopener"` is consistently applied to all `target="_blank"` links, preventing tab-napping.

### Issues

**Critical:**
- **Mobile hamburger button does not exist in HTML** — `.menu-toggle` has CSS rules (lines 115–118, 774) showing it at `display: block` on ≤1024px, but no `<button class="menu-toggle">` element appears anywhere in the HTML body. Mobile users cannot access any navigation links.
- **No `<main>` landmark** — The page has `<nav>` and `<footer>` semantic elements but all content sections sit as direct children of `<body>` without a `<main>` wrapper. Screen reader users cannot use "skip to main content" or navigate by landmark.
- **Scroll-reveal sets `opacity: 0` via JavaScript on init with no `prefers-reduced-motion` guard** — If the user has `prefers-reduced-motion: reduce` set, the IntersectionObserver still hides and animates all sections. Additionally, if JS fails to load, all `section.block`, `.delivery-card`, and `.contact-card` elements remain invisible permanently.

**Serious:**
- **Gallery images have no `alt` attributes** — 8 `<img>` elements in the gallery grid (lines 1122–1150) were confirmed to have no `alt` text. They do have surrounding `.gallery-caption` text, but that only appears on hover and is not exposed to screen readers as image description.
- **Decorative emoji in partner pills and contact cards are not hidden from screen readers** — `<span class="partner-pill">🛵 Gosend</span>` (line 1183) and contact icons like `<div class="contact-icon">💬</div>` (line 1207) will be read aloud as "motor scooter Gosend" and "speech bubble" by screen readers. These should use `aria-hidden="true"` on the emoji character or be replaced with `role="img" aria-label="..."` patterns.
- **External links missing `noreferrer`** — Instagram and Linktree links use `rel="noopener"` but not `rel="noreferrer"`. The referrer header leaks the Fish Express URL to those third-party domains. Change all instances to `rel="noopener noreferrer"`.

**Minor:**
- No `<meta name="og:image">`, `<meta name="og:title">`, or Twitter Card tags — link previews on WhatsApp (the primary conversion channel) and social media will show no image or meaningful description. This is a significant miss given the product's social-first marketing.
- No `loading="lazy"` on the 14 below-fold product and gallery images. Only 2 images use `loading="eager"` (lines 904, 911 — hero images). The remaining 14 base64 images load eagerly on page init regardless of viewport position, contributing to the 437 KB payload cost.

---

## Files Audited

- `/home/hawariakbar/Project/landing page /fish-express/fishexpress-website.html` (1442 lines — full HTML/CSS/JS source)
- `/home/hawariakbar/Project/landing page /fish-express/.planning/codebase/STACK.md`
- `/home/hawariakbar/Project/landing page /fish-express/.planning/codebase/ARCHITECTURE.md`
- `/home/hawariakbar/Project/landing page /fish-express/.planning/codebase/CONCERNS.md`
