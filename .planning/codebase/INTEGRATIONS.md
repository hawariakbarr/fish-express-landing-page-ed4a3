# External Integrations

**Analysis Date:** 2026-04-23

## APIs & External Services

**Messaging / Order Channel:**
- WhatsApp (wa.me deep-link) — primary ordering and customer contact channel
  - Used in: nav CTA (line 851), hero CTA (line 877), B2C audience card (line 1060), B2B audience card (line 1075), footer (line 1254), contact section (line 1205)
  - Phone number: `628112210830`
  - Pre-filled message text varies by context (B2C vs B2B vs generic inquiry)
  - No SDK; plain `<a href="https://wa.me/...">` links with URL-encoded `text` query param

## Data Storage

**Databases:**
- None — no backend or database

**File Storage:**
- All images inlined as Base64 data URIs directly in the HTML file
- No external image CDN or object storage (no Cloudinary, S3, Imgix, etc.)

**Caching:**
- Browser `localStorage` only (two keys: `fe-lang`, `fe-theme`)
- No service worker, no server-side caching layer

## Authentication & Identity

**Auth Provider:**
- Not applicable — fully public static page; no login, user accounts, or authentication

## Fonts (CDN)

**Google Fonts:**
- Provider: `https://fonts.googleapis.com` / `https://fonts.gstatic.com`
- Families loaded:
  - `Fraunces` — weights 400, 600, 800, 900 (normal + italic variants), optical size range 9–144
  - `Plus Jakarta Sans` — weights 400, 500, 600, 700, 800
- Loading strategy: `display=swap` (render-blocking avoided)
- Preconnect hints present for both domains (lines 8–9)
- File: `fishexpress-website.html` line 10

## Social Media & Profile Links

**Instagram:**
- Profile: `https://instagram.com/fishexpress_id`
- Appears in: gallery section CTA (line 1156), contact section (line 1210), footer (line 1255)
- Not embedded via Instagram API — static links only; gallery images are inlined JPEGs

**Linktree:**
- Profile: `https://linktr.ee/fishexpressbdg`
- Appears in: contact section (line 1215), footer (line 1256)
- Static link only; no SDK or embed

## Monitoring & Observability

**Error Tracking:**
- None — no Sentry, LogRocket, or equivalent

**Analytics:**
- None — no Google Analytics (`gtag`), Google Tag Manager, Meta Pixel (`fbq`), or any tracking script detected

**Logs:**
- None — no logging integration; vanilla `console` not used in production JS

## Payments

**Payment Processing:**
- None — no payment gateway (no Midtrans, Stripe, PayPal, GoPay, OVO, etc.)
- Orders are initiated via WhatsApp deep-link; payment presumably handled offline or via chat

## CI/CD & Deployment

**Hosting:**
- Not determined from source — file is deployment-ready as a single static HTML artifact
- Compatible with any static host (GitHub Pages, Netlify, Vercel, shared hosting, CDN)

**CI Pipeline:**
- None detected

## Webhooks & Callbacks

**Incoming:**
- None

**Outgoing:**
- None

## Environment Configuration

**Required env vars:**
- None — fully self-contained; no secrets or environment-specific configuration

**Secrets location:**
- Not applicable; the only external identifier is the public WhatsApp phone number embedded in HTML

---

*Integration audit: 2026-04-23*
