---
version: 1.0
name: RemindPay-design-system
description: A crisp, friendly App-Store-marketing interface for RemindPay, a bill & warranty tracker for Apple devices. The system anchors on a white canvas with soft blue-tinted gradient bands, a confident steel-blue primary (#2E6FA8), and Inter at heavy weights (800–900) for display type. Brand voltage comes from blue gradient text treatments and pill-shaped gradient CTAs with soft colored shadows. Accent tints (orange, green, rose, violet) color-code feature categories. Dark ink-navy (#1A1A2E) closes the page as the footer.
colors:
  primary: "#2E6FA8"
  primary-dark: "#1F5683"
  primary-light: "#DCE8F2"
  primary-gradient-end: "#4789BC"
  ink: "#1A1A2E"
  muted: "#6B7280"
  border: "#E5E7EB"
  bg-soft: "#F9FAFB"
  canvas: "#ffffff"
  hero-tint: "#EEF5FB"
  blue-tint: "#E6F1F9"
  on-primary: "#ffffff"
  accent-orange: "#FF9500"
  accent-orange-light: "#FFB84D"
  accent-green: "#16A34A"
  accent-green-tint: "#F0FDF4"
  accent-rose: "#E11D48"
  accent-rose-tint: "#FFF1F2"
  accent-violet: "#8B5CF6"
  accent-violet-tint: "#F5F3FF"
  accent-orange-tint: "#FFF7ED"
  star-gold: "#FFC107"
  success: "#34C759"

typography:
  display-xl:
    fontFamily: "Inter, -apple-system, sans-serif"
    fontSize: clamp(40px, 5.2vw, 68px)
    fontWeight: 900
    lineHeight: 1.15
    letterSpacing: -2px
  display-lg:
    fontFamily: "Inter, -apple-system, sans-serif"
    fontSize: clamp(28px, 4vw, 44px)
    fontWeight: 800
    lineHeight: 1.15
    letterSpacing: -1px
  display-md:
    fontFamily: "Inter, -apple-system, sans-serif"
    fontSize: clamp(24px, 3vw, 36px)
    fontWeight: 800
    lineHeight: 1.2
    letterSpacing: -0.8px
  stat-number:
    fontFamily: "Inter, -apple-system, sans-serif"
    fontSize: clamp(32px, 4vw, 48px)
    fontWeight: 900
    lineHeight: 1
  title-md:
    fontFamily: "Inter, -apple-system, sans-serif"
    fontSize: 18px
    fontWeight: 700
    lineHeight: 1.4
  body-lg:
    fontFamily: "Inter, -apple-system, sans-serif"
    fontSize: 17px
    fontWeight: 400
    lineHeight: 1.6
  body-md:
    fontFamily: "Inter, -apple-system, sans-serif"
    fontSize: 16px
    fontWeight: 400
    lineHeight: 1.7
  body-sm:
    fontFamily: "Inter, -apple-system, sans-serif"
    fontSize: 14px
    fontWeight: 400
    lineHeight: 1.7
  list-item:
    fontFamily: "Inter, -apple-system, sans-serif"
    fontSize: 15px
    fontWeight: 500
    lineHeight: 1.5
  caption:
    fontFamily: "Inter, -apple-system, sans-serif"
    fontSize: 13px
    fontWeight: 600
    lineHeight: 1.4
  badge-uppercase:
    fontFamily: "Inter, -apple-system, sans-serif"
    fontSize: 12px
    fontWeight: 700
    lineHeight: 1.4
    letterSpacing: 1.5px
  button:
    fontFamily: "Inter, -apple-system, sans-serif"
    fontSize: 16px
    fontWeight: 700
    lineHeight: 1

rounded:
  md: 12px
  card: 20px
  pill: 9999px
  full: 9999px

spacing:
  xs: 8px
  sm: 12px
  md: 16px
  lg: 24px
  xl: 32px
  xxl: 48px
  section: 100px

shadows:
  primary-md: "0 8px 24px rgba(46,111,168,0.35)"
  primary-lg: "0 12px 32px rgba(46,111,168,0.45)"
  primary-soft: "0 12px 40px rgba(46,111,168,0.15)"
  card-hover: "0 16px 48px rgba(46,111,168,0.12)"
  testimonial-hover: "0 8px 32px rgba(46,111,168,0.1)"
  btn-white: "0 8px 30px rgba(0,0,0,0.2)"

components:
  top-nav:
    backgroundColor: "rgba(255,255,255,0.9) + backdrop-blur"
    textColor: "{colors.ink}"
    height: 68px
    position: sticky
  button-primary:
    background: "linear-gradient(135deg, {colors.primary}, {colors.primary-dark})"
    textColor: "{colors.on-primary}"
    typography: "{typography.button}"
    rounded: "{rounded.pill}"
    padding: 16px 32px
    shadow: "{shadows.primary-md}"
    hover: "translateY(-2px) + {shadows.primary-lg}"
  button-secondary:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink}"
    border: "1.5px solid {colors.border}"
    rounded: "{rounded.pill}"
    padding: 15px 28px
    hover: "border-color {colors.primary} + translateY(-2px)"
  button-white-on-gradient:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.primary}"
    rounded: "{rounded.pill}"
    padding: 16px 36px
    shadow: "{shadows.btn-white}"
    hover: "translateY(-2px)"
  badge-section:
    backgroundColor: "{colors.primary-light}"
    textColor: "{colors.primary}"
    typography: "{typography.badge-uppercase}"
    border: "1px solid {colors.primary} at 30% alpha"
    rounded: "{rounded.pill}"
    padding: 5px 12px
  badge-rating:
    backgroundColor: "{colors.primary-light}"
    textColor: "{colors.primary}"
    typography: "{typography.caption}"
    border: "1px solid {colors.primary} at 30% alpha"
    rounded: "{rounded.pill}"
    padding: 6px 14px
  feature-pillar-card:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink}"
    border: "1px solid {colors.border}"
    rounded: "{rounded.card}"
    padding: 32px 28px
    hover: "translateY(-4px) + {shadows.card-hover}"
  feature-icon-circle:
    size: 52px
    rounded: "{rounded.full}"
    backgroundColor: "accent tint (e.g. {colors.blue-tint}, {colors.accent-green-tint})"
    border: "1px solid matching accent at 40% alpha"
    iconColor: "matching accent"
  feature-image-panel:
    background: "soft two-stop gradient of an accent tint (e.g. {colors.hero-tint} → {colors.blue-tint})"
    rounded: "{rounded.card}"
    height: "280px mobile / 500px desktop"
    content: "app screenshot at 120% height with large colored drop-shadow"
  numbered-list-chip:
    size: 22px
    backgroundColor: "{colors.primary-light}"
    textColor: "{colors.primary}"
    typography: "12px / 700"
    rounded: "{rounded.full}"
  testimonial-card:
    backgroundColor: "{colors.canvas}"
    border: "1px solid {colors.border}"
    rounded: "{rounded.card}"
    padding: 28px
    hover: "{shadows.testimonial-hover}"
    stars: "{colors.star-gold}"
  avatar-circle:
    size: 36px
    backgroundColor: "{colors.primary}"
    textColor: "{colors.on-primary}"
    rounded: "{rounded.full}"
  cta-band:
    background: "linear-gradient(135deg, {colors.primary}, {colors.primary-gradient-end})"
    textColor: "{colors.on-primary}"
    typography: "{typography.display-lg}"
    padding: 100px 5%
  footer:
    backgroundColor: "{colors.ink}"
    textColor: "rgba(255,255,255,0.7)"
    linkColor: "rgba(255,255,255,0.6) → white on hover"
    padding: "60px 5% 40px"
---

## Overview

RemindPay's marketing site is a bright, friendly, consumer-app landing page in the Apple-ecosystem tradition. The base is a **white canvas** with a soft blue-tinted gradient hero (`{colors.hero-tint}` → white). All type is **Inter** — heavy weights (800–900) with tight negative tracking for display, regular weight for body. There is no serif anywhere; the voice is modern-product, not editorial.

Brand voltage comes from three treatments:
1. **Blue gradient text** — headlines and stat numbers use a `{colors.primary}` → `{colors.primary-gradient-end}` gradient clipped to text. The hero also highlights single words in an orange gradient (`{colors.accent-orange}` → `{colors.accent-orange-light}`).
2. **Pill-shaped gradient CTAs** — the primary button is a blue gradient pill with a soft blue shadow that lifts on hover.
3. **Color-coded feature tints** — each feature gets its own pastel tint + accent pair (blue, green, orange, rose, violet), used for icon circles and screenshot panel gradients.

The page closes with a full-bleed blue gradient CTA band and a dark ink-navy (`{colors.ink}`) footer.

## Colors

### Brand
- **Primary** (`{colors.primary}` — #2E6FA8): Steel blue. Buttons, links, badges, avatar fills, gradient starts.
- **Primary Dark** (`{colors.primary-dark}` — #1F5683): Gradient end for buttons, hover emphasis.
- **Primary Light** (`{colors.primary-light}` — #DCE8F2): Badge and chip backgrounds.
- **Gradient End** (`{colors.primary-gradient-end}` — #4789BC): Lighter blue used as the second stop in headline/stat/CTA-band gradients.

### Accents (feature color-coding)
Each feature category pairs a saturated accent with a pastel tint background:
- Blue: `{colors.primary}` on `{colors.blue-tint}` / `{colors.hero-tint}`
- Green: `{colors.accent-green}` (#16A34A) on `{colors.accent-green-tint}` (#F0FDF4)
- Orange: `{colors.accent-orange}` (#FF9500 / #EA580C) on `{colors.accent-orange-tint}` (#FFF7ED)
- Rose: `{colors.accent-rose}` (#E11D48) on `{colors.accent-rose-tint}` (#FFF1F2)
- Violet: `{colors.accent-violet}` (#8B5CF6) on `{colors.accent-violet-tint}` (#F5F3FF)
- **Star Gold** (`{colors.star-gold}` — #FFC107): Testimonial star ratings. The hero rating star uses `{colors.accent-orange}`.

### Neutrals
- **Ink** (`{colors.ink}` — #1A1A2E): Headlines, primary text, footer background. Navy-tinted near-black.
- **Muted** (`{colors.muted}` — #6B7280): Sub-headlines, descriptions, captions.
- **Border** (`{colors.border}` — #E5E7EB): 1px card and button outlines.
- **BG Soft** (`{colors.bg-soft}` — #F9FAFB): Alternate section band background (feature rows).
- **Canvas** (#ffffff): Default page floor.

## Typography

**Inter only**, loaded at 400–900. Fallback stack: `Inter, -apple-system, BlinkMacSystemFont, sans-serif`. Icons are **Material Symbols Rounded**.

| Token | Size | Weight | Tracking | Use |
|---|---|---|---|---|
| `{typography.display-xl}` | clamp(40–68px) | 900 | -2px | Hero h1, often with gradient-clipped words |
| `{typography.display-lg}` | clamp(28–44px) | 800 | -1px | Section h2, usually gradient-clipped |
| `{typography.display-md}` | clamp(24–36px) | 800 | -0.8px | Feature-row h2 (solid ink, no gradient) |
| `{typography.stat-number}` | clamp(32–48px) | 900 | — | Stats, gradient-clipped |
| `{typography.title-md}` | 18px | 700 | — | Card titles |
| `{typography.body-lg}` | 17px | 400 | — | Section intro paragraphs (muted) |
| `{typography.body-md}` | 16px | 400 | — | Feature descriptions (muted) |
| `{typography.list-item}` | 15px | 500 | — | Numbered checklist items (ink) |
| `{typography.body-sm}` | 14px | 400 | — | Card body, footer text |
| `{typography.caption}` | 13px | 600 | — | Rating badge, fine print |
| `{typography.badge-uppercase}` | 12px | 700 | +1.5px | Section badges ("FEATURES", "REVIEWS") |
| `{typography.button}` | 15–16px | 600–700 | — | Buttons |

### Principles
- Display type is **very heavy** (800–900) with negative tracking — the opposite of a light editorial voice. Never use weight 400 for headlines.
- Major section h2s get the blue gradient text treatment; feature-row h2s inside tinted bands stay solid ink.
- Body copy is muted gray (`{colors.muted}`), never pure black, with generous 1.6–1.7 line-height.

## Layout

- **Max content width:** 1200px (hero), 1100px (sections), 900px (stats).
- **Section padding:** ~100px vertical, 5% horizontal.
- **Hero:** 2-column grid (1.05fr / 1fr), copy left, phone screenshot right; stacks below 880px.
- **Feature pillars:** auto-fit grid, min 260px columns (3-up desktop → 1-up mobile), 24px gap.
- **Feature rows:** 2-column 50/50 grids alternating image side (image right on even rows via order swap), 60px gap, 80px between rows.
- **Testimonials:** auto-fit grid, min 280px columns, 20px gap.
- **Custom breakpoints:** 520px (`xs520`) and 880px (`md880`) in addition to Tailwind defaults.

## Elevation & Depth

Shadows are **soft, large-radius, and brand-tinted** — blue-alpha shadows under blue elements:

| Treatment | Use |
|---|---|
| `{shadows.primary-md}` → `{shadows.primary-lg}` on hover | Primary gradient buttons |
| `{shadows.card-hover}` + translateY(-4px) | Feature pillar cards on hover |
| `{shadows.testimonial-hover}` | Testimonial cards on hover |
| Large colored drop-shadows (e.g. `0 45px 90px rgba(46,111,168,0.55)`) | App screenshots inside feature panels, tinted to match the panel's accent |
| `{shadows.btn-white}` | White button on the gradient CTA band |

Cards at rest are flat with a 1px `{colors.border}` outline; elevation appears on hover (lift + shadow). Motion is consistent: `transition 200ms`, `translateY(-2px)` for buttons, `translateY(-4px)` for cards.

## Shapes

| Token | Value | Use |
|---|---|---|
| `{rounded.card}` | 20px | All cards and image panels |
| `{rounded.pill}` | 9999px | Every button and badge — buttons are always pills, never rectangles |
| `{rounded.full}` | 50% | Icon circles (52px), numbered chips (22px), avatars (36px) |

## Components

- **`top-nav`** — Sticky, 68px, white at 90% opacity with backdrop blur, no border. App icon (38px) + bold wordmark left.
- **`button-primary`** — Blue gradient pill (`{colors.primary}` → `{colors.primary-dark}`), white bold text, blue-tinted shadow, lifts on hover. Often carries an Apple logo SVG.
- **`button-secondary`** — White pill, 1.5px gray border, border turns primary-blue on hover.
- **`badge-section`** — Uppercase tracking badge above every section h2. Primary-light fill, primary text, 30%-alpha primary border.
- **`feature-pillar-card`** — White card, gray hairline, 20px radius, 52px tinted icon circle (Material Symbols Rounded icon in the accent color), 18px bold title, 14px muted body.
- **`feature-image-panel`** — Pastel gradient panel (20px radius) holding an oversized app screenshot with a large accent-tinted drop shadow. Each feature row uses a different accent tint.
- **`numbered-list-chip`** — 22px primary-light circle with a primary-blue number; used for feature checklists.
- **`testimonial-card`** — White card, gold ★★★★★ row, italic 15px quote, 36px primary-blue initial avatar + "App Store Review" caption.
- **`cta-band`** — Full-bleed blue gradient band (not a contained card), 900-weight white headline, white pill button with primary-blue text.
- **`footer`** — `{colors.ink}` background, white/70 text, 4-column link grid (2fr 1fr 1fr 1fr), white/10 top-border bar with copyright.

## Do's and Don'ts

### Do
- Keep the canvas white with soft blue-tinted gradient bands (`{colors.hero-tint}` → white) for the hero; use `{colors.bg-soft}` for alternate section bands.
- Use Inter 800–900 with negative tracking for all display type, and the blue gradient text-clip on major section headlines and stats.
- Keep every button and badge pill-shaped.
- Color-code features with the accent tint pairs (blue / green / orange / rose / violet) — icon circle, panel gradient, and screenshot shadow should all share one accent.
- Use blue-alpha shadows under blue elements; shadows should be large-radius and soft, appearing on hover with a small upward translate.
- Precede every section h2 with an uppercase `{component.badge-section}`.

### Don't
- Don't use serif fonts anywhere — this is a product brand, not an editorial one.
- Don't use flat solid-color primary buttons; the primary CTA is always the blue gradient pill with shadow.
- Don't use rectangular or lightly-rounded buttons — pills only. Cards stay at 20px.
- Don't mix accent colors within a single feature (e.g. green icon in a rose panel).
- Don't put gradient text inside the tinted feature-row bands — solid ink there; gradient headlines live on white sections only.
- Don't use pure black text; ink is #1A1A2E and body copy is muted #6B7280.

## Responsive Behavior

| Width | Key changes |
|---|---|
| < 520px | Stats stack 1-up; footer 1 column |
| 520–880px | Stats 2-up (last spans 2); hero stacks, text centers; feature rows stack image-first |
| > 880px | Hero 2-column with left-aligned text; feature rows alternate image side |
| Desktop | Pillars 3-up, testimonials 3-up, footer 4 columns |

- Fluid type via `clamp()` handles headline scaling; no per-breakpoint font overrides.
- Feature image panels drop from 500px to 280px height on mobile; screenshots stay oversized (120% height) inside.
- Grids reduce column count via `auto-fit, minmax()` rather than shrinking cards.
