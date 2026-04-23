# Architecture
<!-- Generated: 2026-04-23 -->

## Overview

Single-file static landing page (`fishexpress-website.html`, 1442 lines, ~437KB). No framework, no build step, no server — pure vanilla HTML/CSS/JS.

## Structure

Three layers colocated in one file:
- **CSS** — `<style>` block (lines 10–806)
- **HTML body** — lines 808–1263
- **JavaScript** — `<script>` block (lines 1265–1440)

## Key Systems

### i18n (Internationalization)
- `const i18n` object (line 1267) — flat key-value maps for `id` and `en` locales
- `applyLang(lang)` — swaps `textContent` on `[data-i18n]` and `innerHTML` on `[data-i18n-html]` elements
- Persisted to `localStorage` key `fe-lang`

### Theme (Light/Dark Mode)
- CSS custom properties in `:root[data-theme="light/dark"]` (lines 11–40)
- `applyTheme(theme)` — sets `data-theme` attribute on `<html>`
- Persisted to `localStorage` key `fe-theme`
- Falls back to `prefers-color-scheme` media query

### Scroll Reveal Animation
- `IntersectionObserver` (line 1424) observes `section.block`, `.delivery-card`, `.contact-card`
- Sets `opacity/translateY` to 0 on init, animates to visible on intersection

## Data Flow

All CTAs → `wa.me/628112210830` with URL-encoded pre-filled messages. No forms, no backend, no API calls at runtime.

All images are base64-encoded JPEGs embedded inline (16 occurrences) — zero external image requests.

## Error Handling

All `localStorage` calls wrapped in `try/catch(e){}` to handle private browsing / storage quota scenarios.

## Entry Points

- Page load → theme + language init → `IntersectionObserver` setup
- User interaction → language toggle, theme toggle, mobile nav hamburger
