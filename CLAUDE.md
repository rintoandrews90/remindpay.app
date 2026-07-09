# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

Static marketing site for **RemindPay** (iOS bill & warranty tracker), live at https://remindpay.app. There is **no build step** — plain HTML files are deployed directly.

## Deploy

```bash
npx wrangler deploy
```

Run from the project root. `wrangler.jsonc` serves the current directory as static assets to Cloudflare.

**Important caveats:**
- There is **no `package.json`** in this directory. `npm` walks up to the home directory. If you need to install npm packages (e.g. for scripts), run `npm init` here first.
- There is **no git repo** in this folder — no version history. Be careful with destructive edits.

## Architecture

### Pages
- `index.html` — single-page landing site (hero, stats, bento feature grid, testimonials marquee, CTA, footer)
- `pages/faq.html` — FAQ page (same stack, same design)
- `PrivacyPolicy.html` — privacy policy

### Stack (all via CDN — nothing to install to edit)
- **Tailwind CSS** loaded from CDN (`https://cdn.tailwindcss.com`) with a custom config block inline in each page's `<head>`
- **Inter** from Google Fonts; **Material Symbols Rounded** for icons
- **Motion** (`motion@12.42.2` from jsDelivr) for scroll-reveal animations

### Tailwind config
The Tailwind `theme.extend` is defined inline in each HTML file's `<script>` block — not in a shared file. Custom tokens defined there map to `DESIGN.md` values: `primary`, `brandtext`, `brandmuted`, `brandborder`, `brandbg`, `surface`, `success`, and custom shadow + breakpoint keys (`xs520`, `md880`).

### Scroll-reveal animation
Elements with `data-animate` start invisible (via `.js [data-animate]` CSS rule) and are animated in by Motion's `inView()` when scrolled into view. `data-delay="0.06"` etc. staggers sibling cards. The `.no-motion` class disables this if Motion fails to load within 1.5s.

### CSS classes to know
- `.pcard` — the standard white card (border, 24px radius, lift-on-hover)
- `.shine-card` — adds a shine sweep `::after` on hover
- `.hero-mesh` — radial gradient background on the hero section
- `.cta-noise` — adds SVG noise texture overlay `::after` on the CTA band
- `.marquee-track` / `.marquee-group` — infinite-scroll testimonial row; pause on hover
- `.animate-float` — floating keyframe on the hero phone image
- `.badge-shimmer` — shimmer animation on the hero rating badge
- `.grad-avatar` — blue gradient fill for testimonial initials avatars
- `.edge-fade` — mask-image fade at left/right edges of the marquee

## Design

**Before writing or changing any UI, read `DESIGN.md`** and follow its tokens (colors, typography, radii, shadows, components).

Key constraints from `DESIGN.md`:
- **Primary blue:** `#2E6FA8` (DESIGN.md canonical). Note: `index.html` currently uses `#396FC0` — a slight drift. New code should follow `DESIGN.md`.
- **Type:** Inter only, display weights 800–900 with negative letter-spacing. Body copy is always muted (`#6B7280`), never pure black.
- **Buttons:** always pill-shaped (`border-radius: 9999px`), primary CTA is always a blue gradient pill with blue-alpha shadow.
- **Section headers:** always preceded by an uppercase badge (`badge-section` component).
- **Cards at rest** are flat with a 1px border; elevation (shadow + translateY) appears only on hover.
- **Feature icon colors** are accent-coded: blue, teal/success, orange, red/danger, gold. Don't mix accents within a single feature card.

## Pending items (from HANDOFF.md)

- Footer "Terms of Use" link points to `#` — needs a real page or removal.
- After deploying, use Google Search Console → URL Inspection → Request Indexing for `https://remindpay.app/` to speed up site-name update.
