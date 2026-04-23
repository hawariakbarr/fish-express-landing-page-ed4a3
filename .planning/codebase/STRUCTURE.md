# Structure
<!-- Generated: 2026-04-23 -->

## File Layout

```
fish-express/
└── fishexpress-website.html   # Entire project — CSS + HTML + JS in one file
```

## HTML Sections (in order)

| Element | Anchor |
|---|---|
| `<nav>` | (top of page) |
| `.hero` | — |
| `.marquee` | — |
| `#produk` | Product categories |
| `#untuk-siapa` | Target audience |
| `#kenapa-kami` | Why choose us |
| `#galeri` | Gallery |
| `.delivery-section` | Delivery info |
| `#kontak` | Contact |
| `<footer>` | — |

## CSS Sections

Delimited by `/* ===== NAME ===== */` comments:

| Section | Approx. line |
|---|---|
| NAV | 58 |
| HERO | 120 |
| MARQUEE | 317 |
| GENERIC SECTIONS | 349 |
| PRODUCT CATEGORIES | 372 |
| AUDIENCE SPLIT | 442 |
| GALLERY | 503 |
| WHY | 557 |
| DELIVERY | 581 |
| CONTACT | 665 |
| FOOTER | 725 |
| RESPONSIVE | 771 |

## JS Sections

Delimited by same `/* ===== NAME ===== */` pattern:

| Section | Approx. line |
|---|---|
| i18n | 1266 |
| Theme | 1382 |
| Init | 1392 |

## Naming Conventions

- BEM-influenced kebab-case class names: `product-card`, `hero-eyebrow`, `audience-b2c`, `why-num`
- Modifier classes appended directly: `featured`, `active`, `hc-1`/`hc-2`/`hc-3`

## Responsive Breakpoints

| Breakpoint | Behavior |
|---|---|
| `max-width: 1024px` | Hide nav links, show hamburger |
| `max-width: 968px` | Stack grids to 1–2 cols |
| `max-width: 560px` | Single column, stack actions |

## Typography

- `Fraunces` — serif, used for headings, prices, decorative numbers
- `Plus Jakarta Sans` — sans-serif, used for body text and UI elements
