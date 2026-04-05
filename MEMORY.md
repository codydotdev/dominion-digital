# Dominion Digital — Project Reference

**Business:** Dominion Digital | dominion.digital
**Location:** Kansas City, MO
**Dev server:** `npm run dev` → `http://localhost:4322/`
**Project path:** `c:\Users\Cody\.antigravity\.webdev\dominion-digital\`

---

## Current Status

**Homepage is mostly finished.** All component files exist and render. Build the rest of the site using the homepage as the reference design — not this file, not old screenshots.

**Next up:** `/web-design` category page.

---

## Design System (Live — source of truth is `src/styles/global.css`)

| Token | Value |
|-------|-------|
| Background | `#0d0d0b` (Obsidian) |
| Surface | `#161614` |
| Primary text | `#f0ebe1` (Warm white) |
| Secondary text | `#8a8880` (Ash) |
| Accent / CTA | `#c8511a` (Burnt orange) |
| Accent hover | `#e05e20` |
| Display / H1 / H2 / labels | Space Grotesk |
| Body | DM Sans |
| Wordmark | Raleway |

**Typography sizing:**
- H1 display: `clamp(3.5rem, 7vw, 7.5rem)`, weight 800, `tracking-tighter`
- H2: `clamp(2rem, 4vw, 3.5rem)`, weight 700, `tracking-tight`
- Body: `1.125rem`, `leading-relaxed`, `max-w-2xl`
- Label/caption: `0.75rem`, `tracking-widest`, uppercase, Space Grotesk

**Layout patterns:**
- Container: `max-w-7xl mx-auto`, `padding: clamp(2rem, 6vw, 6rem)`
- Section padding: `clamp(8rem, 14vw, 14rem)` top/bottom
- Preferred grid: `grid-cols-[3fr_2fr]` (asymmetric, never equal 3-col)
- Section numbers: `01`, `02`, `03…` above H2, in Ash color, Space Grotesk label size

**Buttons:**
- Primary: pill shape (`border-radius: 9999px`), burnt orange bg, warm white text, orange glow `box-shadow`
- Ghost/secondary: `border: 1px solid rgba(240,235,225,0.25)`, same font, accent on hover
- All buttons use `data-open-contact` attribute to trigger the contact modal

**Motion (intensity 4/10):**
- Scroll reveal: `.reveal` class → add `.visible` via IntersectionObserver → `opacity 0→1` + `translateY 24px→0`, `600ms ease-out`, fires once
- Stagger: `.stagger` parent, 80ms delay per child
- Hero shader: always animating (WebGL, not Three.js library)
- Nav scroll: `backdrop-filter: blur(16px)` + dark glass on scroll

**Explicit bans:**
- No gradient backgrounds on sections
- No purple of any kind
- No centered hero text
- No 3-column equal card grids
- No rounded section dividers
- No neon glows (the btn-cta orange glow is the only exception, defined in CSS)
- No emojis
- No Inter font
- No gradient text on headlines
- No fake statistics or placeholder testimonial names

---

## File Structure

```
dominion-digital/
├── src/
│   ├── components/
│   │   ├── Nav.astro            ← Fixed nav, frosted glass on scroll, contact modal trigger
│   │   ├── Hero.astro           ← Full-viewport, WebGL shader, left-aligned H1
│   │   ├── Signs.astro          ← "Sound familiar?" pain points section
│   │   ├── WebDesign.astro      ← Section 01 — homepage web design block
│   │   ├── SeoGeo.astro         ← Section 02 — SEO + GEO block
│   │   ├── Advertising.astro    ← Section 03 — Paid ads block
│   │   ├── Automation.astro     ← Section 04 — Automation block
│   │   ├── Guarantee.astro      ← Section 05 — Guarantee block
│   │   ├── Intro.astro          ← About/who we are block
│   │   ├── ServiceAreas.astro   ← KC metro service areas
│   │   ├── FAQ.astro            ← FAQ accordion
│   │   ├── Footer.astro         ← 4-col footer
│   │   └── ContactModal.astro   ← Full contact modal (triggered by data-open-contact)
│   ├── layouts/
│   │   └── Layout.astro         ← HTML shell, fonts, meta, ContactModal slot
│   ├── pages/
│   │   └── index.astro          ← Homepage (mostly finished)
│   └── styles/
│       └── global.css           ← Design tokens, reveal, container, marquee, btn-cta
├── public/
│   └── images/                  ← Logo files + any images
├── design-dna-dominion-digital.md      ← Full design spec (reference)
├── site-structure-dominion-digital.md  ← All 32 pages: slugs, H1s, meta, links
├── conversion-copy-dominion-digital.md ← H1s, subheadlines, CTAs, value props per page
├── content-homepage-dominion-digital.md← Full homepage body copy
├── offers-dominion-digital.md          ← Pricing tiers, guarantees, bonus values
└── MEMORY.md                           ← This file
```

---

## Page Architecture (32 total pages)

See `site-structure-dominion-digital.md` for full details. Summary:

| Type | Count | Status |
|------|-------|--------|
| Homepage | 1 | ✅ Mostly done |
| Category pages | 4 | 🔲 Not started |
| Service pages | 10 | 🔲 Not started |
| Location pages | 13 | 🔲 Not started |
| Standard pages (About, Contact, Pricing) | 3 | 🔲 Not started |

**Category pages (build in this order):**
1. `/web-design` — GBP: Website Designer
2. `/internet-marketing` — GBP: Internet Marketing Service
3. `/advertising` — GBP: Advertising Agency
4. `/ai-automation` — GBP: Automation Company

---

## Copy Sources

- **H1s, subheadlines, CTAs, value props:** `conversion-copy-dominion-digital.md` ← use this first
- **Site structure notes (positioning, linking):** `site-structure-dominion-digital.md`
- **Body copy:** write fresh per page using the positioning notes + conversion copy as anchors
- **Offers/pricing:** `offers-dominion-digital.md`
- **Design rules:** `design-dna-dominion-digital.md`

---

## How to Build a New Page

1. Create `src/pages/[slug].astro`
2. Import `Layout`, `Nav`, `Footer` — same as `index.astro`
3. Add page-specific JSON-LD schema in the `head` slot
4. Build sections as inline HTML (or new component files if reusable)
5. Use the same `.reveal` + IntersectionObserver pattern for scroll animations
6. CTA buttons: `<button type="button" data-open-contact class="btn-cta ...">` — the modal handles the rest
7. Internal links: use the link map from `site-structure-dominion-digital.md`
8. Meta title + description: finalize from `conversion-copy-dominion-digital.md` (meta descriptions are still placeholders in the structure file — write them fresh)
