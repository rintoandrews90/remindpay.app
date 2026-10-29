# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

Static marketing site for **RemindPay** (iOS bill & warranty tracker), live at https://remindpay.app. There is **no build step** — plain HTML files are deployed directly.

App Store: https://apps.apple.com/us/app/remindpay-bills-warranty/id1609633170

## Version control

This **is** a git repo, on `main`, with remote `origin` → `git@github.com:rintoandrews90/remindpay.app.git`. Recent history is descriptive (e.g. "Add 9 individual tutorial detail pages"); older commits are all "Updated".

## Deploy

```bash
npx wrangler deploy
```

Run from the project root. `wrangler.jsonc` serves the current directory (`assets.directory: "."`) as static assets to the Cloudflare Worker `remindpayapp`. Custom domain via `CNAME`.

**Caveat:** there is **no `package.json`** in this directory, so `npm` walks up to the home directory (`~/package.json` — this is where an earlier Playwright install landed). If you need project-local npm packages, run `npm init` here first.

## Architecture

### Pages

Root:
- `index.html` — single-page landing site (hero, stats, bento feature grid, testimonials marquee, CTA, footer)
- `PrivacyPolicy.html`, `TermsOfUse.html` — legal pages (both linked from the footer)

`pages/`:
- `faq.html` — FAQ page
- `changelog.html` — "What's New" release-notes timeline. **Its content is generated from the iOS repo**, not written by hand — see below.
- `tutorial.html` — tutorials index; links to all nine `tut-*.html` pages. Linked from the index nav and footer.
- `tut-getting-started.html`, `tut-reminders.html`, `tut-warranty.html`, `tut-widgets.html`, `tut-reports.html`, `tut-apple-watch.html`, `tut-apple-pay.html`, `tut-siri.html`, `tut-recurring-bills.html` — tutorial detail pages

`images/` holds all screenshots and icons, plus `images/faq/` (FAQ/tutorial step art, including `step1–4.svg`).

### Stack (all via CDN — nothing to install to edit)

Every page loads:
- **Tailwind CSS** from CDN (`https://cdn.tailwindcss.com`) with a custom config block inline in that page's `<head>`
- **Inter** from Google Fonts; **Material Symbols Rounded** for icons

`index.html` only:
- **Motion** (`motion@12.42.2` from jsDelivr) for scroll-reveal animations

### Tailwind config is duplicated per page

Each HTML file carries its own inline `theme.extend` — there is no shared config file. Tokens defined: `primary` (with `dark`/`light`), `brandtext`, `brandmuted`, `brandborder`, `brandbg`, `surface`, `success`, plus custom shadow keys and breakpoints `xs520: 520px` / `md880: 880px`.

**`index.html` has drifted from every other page and from `DESIGN.md`** across the whole palette, not just the primary:

| Token | `DESIGN.md` + all other pages | `index.html` (drifted) |
|---|---|---|
| `primary` | `#2E6FA8` | `#396FC0` |
| `primary.dark` | `#1F5683` | `#2B589C` |
| `primary.light` | `#DCE8F2` | `#D8E3F3` |
| `brandtext` | `#1A1A2E` | `#1B2027` |
| `brandmuted` | `#6B7280` | `#5C6678` |
| `brandborder` | `#E5E7EB` | `#D2D6DB` |
| `brandbg` | `#F9FAFB` | `#F6F7F8` |
| `surface` | `#F7F7F8` | `#F6F7F8` |
| `success` | `#34C759` | `#479A9A` |

`<meta name="theme-color">` follows the same split (`#396FC0` on index, `#2E6FA8` elsewhere). New code should follow `DESIGN.md`. Changing `index.html` back is a deliberate visual change — confirm before doing it.

### Scroll-reveal animation (`index.html` only)

Elements with `data-animate` start invisible (via the `.js [data-animate]` CSS rule) and are animated in by Motion's `inView()` when scrolled into view. `data-delay="0.06"` etc. staggers sibling cards. The `.no-motion` class disables this if Motion fails to load within 1.5s; `prefers-reduced-motion` is also respected. No other page uses Motion or `data-animate`.

### CSS classes to know

`index.html` (the only page with a substantial `<style>` block):
- `.pcard` — the standard white card (border, 24px radius, lift-on-hover)
- `.shine-card` — adds a shine sweep `::after` on hover
- `.hero-mesh` — radial gradient background on the hero section
- `.cta-noise` — adds SVG noise texture overlay `::after` on the CTA band
- `.marquee-track` / `.marquee-group` — infinite-scroll testimonial row; pause on hover
- `.edge-fade` — mask-image fade at left/right edges of the marquee
- `.animate-float` — floating keyframe on the hero phone image
- `.badge-shimmer` — shimmer animation on the hero rating badge
- `.grad-avatar` — blue gradient fill for testimonial initials avatars
- `.icon-glow-blue`, `.stat-num` — icon glow and gradient stat numerals

Other pages style almost entirely with Tailwind utilities and define only what they need: `.tcard` / `.tcard-thumb` (`pages/tutorial.html`), `.rcard` (tutorial detail pages and `changelog.html`), `.rail` / `.rel-dot` (`changelog.html`'s timeline). `faq.html` and the legal pages define only base `body`/`html` rules. `.pcard` and friends are **not** available outside `index.html` — copy the utilities instead of reaching for the class.

## Updating the changelog page

`pages/changelog.html` mirrors the App Store release notes, which live in the **iOS repo** at `~/Documents/Apps/RemindPay` (`Bills Keeper.xcodeproj`). That repo is tagged per version, and each tag holds that release's notes:

```bash
cd ~/Documents/Apps/RemindPay
git tag | sort -V                                     # version-ordered release list
git log -1 --format=%ad --date=short <tag>            # release date
git show "<tag>:fastlane/whats_new/en-US.txt"         # that version's notes
```

Note the quotes/braces — in zsh, an unquoted `$t:fastlane` is parsed as a history modifier and silently returns nothing.

Conventions the page follows:
- Only versions with real notes are listed. `fastlane/whats_new/en-US.txt` first appears at tag `3.3.46`; everything older has none, so the page starts there and points at the App Store for earlier history.
- Not every tag shipped. Tags whose notes duplicate a neighbour (resubmissions) are omitted, and runs of identical boilerplate are collapsed into one dated range entry (e.g. `3.4.0 – 3.4.3`).
- Notes are used close to verbatim — this is shipped App Store copy, British spellings included.
- `fastlane/changelog.txt` is **not** per-version; it has been the same text at every tag. Don't source from it.

When a new version ships: add an entry at the top of the timeline, move the `rel-dot--latest` class and the `Latest` badge to it, and update the version/date in the hero chip, the CTA copy, and `sitemap.xml`.

## Design

**Before writing or changing any UI, read `DESIGN.md`** and follow its tokens (colors, typography, radii, shadows, components).

Key constraints from `DESIGN.md`:
- **Primary blue:** `#2E6FA8` (canonical — see the drift table above).
- **Type:** Inter only, display weights 800–900 with negative letter-spacing. Body copy is always muted (`#6B7280`), never pure black.
- **Buttons:** always pill-shaped (`border-radius: 9999px`); primary CTA is always a blue gradient pill with blue-alpha shadow.
- **Section headers:** always preceded by an uppercase badge (`badge-section` component).
- **Cards at rest** are flat with a 1px border; elevation (shadow + translateY) appears only on hover.
- **Feature icon colors** are accent-coded: blue, green, orange, rose, violet, gold. Don't mix accents within a single feature card.

## SEO

`robots.txt` allows everything and points at `sitemap.xml`. `index.html` carries a `WebSite` JSON-LD block (`name: "RemindPay"`) so Google shows "RemindPay" rather than the bare domain.

`sitemap.xml` lists all 15 pages. Add new pages here when you create them.

## Notes

- `HANDOFF.md` is stale (last updated 2026-07-06) — it predates the git repo, `TermsOfUse.html`, and the tutorial pages. Trust this file over it.
- `.impeccable/` is config for the `impeccable` design skill, not site content.
- Owner/support email: rintoandrews90@gmail.com.
