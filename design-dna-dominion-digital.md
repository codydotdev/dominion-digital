# Design DNA: Dominion Digital

## Brand Context
- **Business:** Dominion Digital — Kansas City digital marketing agency (SEO, GEO/AI search, web design, ads, automation)
- **Target audience:** SMB/B2B owners who've been burned by agencies before — skeptical, results-oriented, no patience for dashboards without ROI
- **Brand adjectives:** Dark, aggressive, dominant
- **Core message:** Results or you don't pay. The Authority Stack (SEO + GEO simultaneously). No other KC agency does both.
- **Do NOT look like:** WebFX, Thrive, Straight North (corporate feature-grid templates), generic KC WordPress agency sites (stock photo heroes, Bootstrap blue, rounded everything)

---

## Color Palette

| Role | Name | Hex |
|------|------|-----|
| Background | Obsidian | `#0d0d0b` |
| Surface | Lifted obsidian | `#161614` |
| Primary text | Warm white | `#f0ebe1` |
| Secondary text | Ash | `#8a8880` |
| Accent / CTA | Burnt orange | `#c8511a` |
| Accent hover | Hot orange | `#e05e20` |

**Palette rules:**
- Accent is for CTAs, active states, and key callouts ONLY — never use as a decorative background fill
- No pure black (#000000) anywhere — use Obsidian (#0d0d0b)
- No pure white (#ffffff) anywhere — use Warm white (#f0ebe1)
- No grays outside the defined palette — no Tailwind `gray-*` or `slate-*` defaults
- Warm white body text on Obsidian background is the baseline — never flip to dark text on light background within a section unless it's a deliberate contrast block

---

## Typography

| Role | Font | Weight | Size guidance |
|------|------|--------|--------------|
| Display / H1 | Space Grotesk | 800 | `clamp(3.5rem, 7vw, 7.5rem)`, `tracking-tighter`, `leading-none` |
| H2 | Space Grotesk | 700 | `clamp(2rem, 4vw, 3.5rem)`, `tracking-tight` |
| H3 | Space Grotesk | 600 | `1.5rem`, `tracking-tight` |
| Body | DM Sans | 400 | `1.125rem`, `leading-relaxed`, `max-w-2xl` |
| Body emphasis | DM Sans | 500 | Same as body |
| Label / Caption | Space Grotesk | 500 | `0.75rem`, `tracking-widest`, `uppercase` |
| Section number | Space Grotesk | 700 | `0.875rem`, `tracking-widest`, `uppercase`, color: Ash |

**Font loading:**
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500&family=Space+Grotesk:wght@500;600;700;800&display=swap" rel="stylesheet">
```

**Typography rules:**
- Headlines always `tracking-tighter` or `tracking-tight` — never default tracking
- No italic body text
- Section numbers (01, 02, 03…) always displayed in Ash above the H2, small caps style
- Body text max-width: `max-w-2xl` (prose constraint) — never full-width paragraphs
- No gradient text effects on headlines

---

## Spacing System
- Base unit: 8px
- Section vertical padding: `py-24 md:py-32`
- Container max-width: `max-w-7xl mx-auto px-8 md:px-16 lg:px-24`
- Content text block max-width: `max-w-2xl`
- Tight content spacing (between label + heading + body): `space-y-4`
- Section gap (between sibling sections): `gap-16 md:gap-24`

---

## Layout Philosophy

Stark and deliberate — Flow Directive-inspired. Every element earns its place. Wide margins, no ornamentation, whitespace is intentional. Sections feel like chapters, not feature lists.

- **Hero:** Full viewport. Text left-aligned, large display headline. Shader animation fills the background behind. Single CTA. Never centered.
- **Sections:** Numbered (01, 02, 03…). Large left-aligned H2. Body text constrained to `max-w-2xl`. No 3-column card grids — use alternating text/data layouts or single-column with heavy type.
- **Stats/proof:** Raw numbers displayed large with no card boxes. Number + short label, nothing else.
- **Grid:** Prefer 2-column asymmetric (60/40 or 55/45) over equal columns. Use `grid grid-cols-1 md:grid-cols-[3fr_2fr]` patterns.

---

## Motion Personality
- **Overall intensity:** 4/10 — mostly static, two deliberate exceptions (hero shader + image marquee)
- **Hero shader:** Always animating — Three.js GLSL concentric ripple rings in `#c8511a` (burnt orange) on `#0d0d0b`, slow pulse (time scale 0.03)
- **Section entry:** `opacity: 0 → 1` + `translateY: 24px → 0`, duration `600ms`, `ease-out`, triggered by IntersectionObserver — fire once, no repeat
- **Stagger on lists:** 80ms delay between children
- **Nav scroll transition:** `backdrop-filter: blur(16px)` + `background: rgba(13,13,11,0.75)`, `transition: 300ms ease`
- **Image marquee:** CSS infinite horizontal scroll, no JS required, constant velocity
- **Hover — CTA buttons:** `background` transitions to `#e05e20` in `200ms`
- **Hover — text links:** Underline draws left-to-right in `200ms`
- **Click/active:** `scale(0.97)` on buttons — tactile, not playful
- **Explicitly forbidden:** No bounces, no elastic/spring easing, no floating elements, no parallax on content, no page transition effects

---

## Component Patterns

- **Navigation:** Fixed top, `height: 72px`. Logo (wordmark) left. Links center or right. Single CTA button right. Transparent on load → frosted dark glass on scroll (`backdrop-filter: blur(16px)`, `background: rgba(13,13,11,0.75)`, `border-bottom: 1px solid rgba(240,235,225,0.06)`).

- **Hero:** Full viewport (`min-h-[100dvh]`). Three.js shader canvas as `position: absolute, inset: 0, z-index: 0`. Content layer `position: relative, z-index: 1`. Headline left-aligned, display size. Subheadline in DM Sans body. One primary CTA button. Optional: secondary ghost link ("See our work ↓").

- **Section header pattern:** Section number (e.g., `01`) in Ash label above H2. H2 left-aligned. Body paragraph below, `max-w-2xl`. Optional CTA link at bottom.

- **Stats row:** 3–4 stats displayed as large number (Space Grotesk 700, `clamp(2.5rem,5vw,4rem)`) + short label below (DM Sans 400, Ash). No boxes. Horizontal row, `divide-x divide-white/10` separator.

- **Image marquee:** After process/services section. Single row of project/client images, infinite CSS scroll. Images in `aspect-[4/3]`, `object-fit: cover`, slight dark overlay (`brightness-75`). No gaps that expose the background between images — seamless loop.

- **Buttons — Primary:** `background: #c8511a`, `color: #f0ebe1`, `padding: 0.75rem 2rem`, `border-radius: 0`, `font: Space Grotesk 600 0.875rem tracking-widest uppercase`. Hover: `background: #e05e20`.

- **Buttons — Ghost/Secondary:** `border: 1px solid rgba(240,235,225,0.25)`, `color: #f0ebe1`, same padding/font. Hover: `border-color: #c8511a`, `color: #c8511a`.

- **Footer:** Full-width, `background: #0a0a09` (slightly deeper than page bg). 4-column grid on desktop (logo+tagline | links | links | contact CTA). `border-top: 1px solid rgba(240,235,225,0.08)`. Minimal — no decorative elements.

---

## Reference Sites
1. `thecreed.agency` — color palette and numbered section architecture
2. `flowdirective.com` — layout stark minimalism, section whitespace, typography weight
3. `solemedia.com.au` — sticky frosted nav behavior, image marquee section

## Three.js Shader Reference
- Source: https://21st.dev/community/components/aliimam/shader-animation/default
- Technology: Three.js + GLSL (fragment shader with concentric ripple rings)
- Customization: Remap color channels to `#c8511a` (burnt orange), background `#0d0d0b`, time scale `0.03` (slow pulse)
- Implement as: `ShaderHero.astro` with `<script>` tag loading Three.js via CDN or npm

---

## Explicit Bans
- No gradient backgrounds (mesh gradients, linear-gradient fills on sections)
- No purple of any kind
- No centered hero text
- No stock photography in hero
- No 3-column equal card grids
- No rounded buttons (border-radius: 0 on all primary CTAs)
- No neon glows or box-shadow glows
- No Inter font (Tailwind default — must be overridden)
- No Tailwind default color classes (`gray-*`, `slate-*`, `blue-*`, etc.) — use DNA tokens only
- No emojis anywhere
- No fake statistics or placeholder testimonial names
