# Dominion Digital — Design Process & Memory File

## Project Overview
- **What:** Homepage for Dominion Digital, a Kansas City digital marketing agency
- **Tech stack:** Astro 6, vanilla CSS, no React/frameworks
- **Project path:** `c:\Users\Cody\.antigravity\.webdev\dominion-digital\`
- **Dev server:** `npm run dev` → `http://localhost:4322/`
- **Content docs:** All in project root (`content-homepage-dominion-digital.md`, `conversion-copy-dominion-digital.md`, `site-structure-dominion-digital.md`, `offers-dominion-digital.md`)

---

## Phase 1: Initial Homepage Build (Complete)

### What was built
A full working homepage using the **taste skill** design philosophy:
- **File:** `src/pages/index.astro` — complete page with all sections
- **File:** `src/styles/global.css` — full design system (tokens, components, animations, responsive)
- **Design:** Dark off-black base (`#0a0a0a`), single emerald accent (`#10b981`), Outfit font
- **Layout:** Asymmetric, left-aligned hero, zig-zag service sections, scroll reveal animations
- **Sections:** Nav → Hero → Intro → Web Design → SEO/GEO → Paid Ads → Automation → Service Areas → Guarantee → FAQ → CTA → Footer
- **SEO:** Full JSON-LD schema (LocalBusiness, Service x4, FAQPage), meta tags, semantic HTML
- **Interactivity:** Scroll reveals (IntersectionObserver), FAQ accordion, mobile hamburger nav, hover effects
- **Images:** 5 AI-generated images in `public/images/` (hero-bg, web-design, seo-geo, paid-ads, automation) plus logo files (logo-icon, logo-white, logo-black)
- **All copy is final SEO content** from the content docs, not placeholder

### Taste Skill Rules Applied
- DESIGN_VARIANCE=8, MOTION=6, DENSITY=4
- No emojis, no Inter font, no purple/neon, no centered hero, no 3-column card grids
- Pure black avoided (uses #0a0a0a), single accent color only

---

## Phase 2: Google Stitch Exploration (In Progress)

### Setup
- **Stitch MCP** is connected via `@_davideast/stitch-mcp` proxy
- **API Key:** `AQ.Ab8RN6KkjyA5Z0LqPe83G-q8r-gpa0Vn0XaeSzFeBMEtMMV77Q`
- **Google Cloud project:** "personal"
- **Stitch project:** "Dominion Digital Home Variant 2" (ID: `15333340392466352429`)

### What exists in Stitch
The project has an auto-generated design system called **"Dominion Dark Ether"** with:
- Deep navy-black background (`#060e20`)
- Plus Jakarta Sans headlines, Manrope body
- Blue (`#7799ff`) primary, purple (`#ddb7ff`) secondary, pink-red (`#ffb2b7`) tertiary
- Glassmorphism, atmospheric depth, no hard borders, ambient shadows
- Blue-to-purple gradient CTAs (`#3e76fe` → `#9c48ea`)

### The Inspiration Image
- **Screen ID:** `687023506455122569` — an uploaded image (no HTML code)
- **Label:** "hero and about" on the Stitch canvas
- **What it shows:** A "Boostly" branded SaaS-style page with:
  - Center-aligned layout, deep black background
  - "SEO Experts" pill badge above headline
  - Large bold centered headline with gradient-highlighted keyword
  - Email input + gradient CTA button
  - Rising gradient line chart (purple→pink) with glowing nodes and vertical markers
  - 4-column feature grid below the chart
  - "About Us" section with large centered paragraph, 3 overlapping circular avatars embedded in text flow, and 4 colored service pills
- **Why Cody likes it:** Clean center-aligned hero, the growth chart visual, the inline avatars in the about text, the pill tags with colored dots, the overall "atmospheric" dark feel

### Screens Generated in Stitch
All of these were generated to match the "Dominion Dark Ether" design system:

| Screen | ID | Status |
|--------|----|--------|
| **Hero + About** (adapted from inspiration) | `3a353543415f489693ff97097879c734` | ✅ Generated with HTML |
| **Web Design Services** | `f7c51dcc78c84c1794173f4d321cf5f7` | ✅ Generated with HTML |
| **Internet Marketing / SEO** (2 variants) | `55f9536889e4...` / `af404fcf...` | ✅ Generated with HTML |
| **Paid Advertising** | `044822d4a03544b381ca398064efa1da` | ✅ Generated with HTML |
| **AI Automation** | `fcfd72fe94264d36b53db3968b378acf` | ✅ Generated with HTML |
| **Guarantee + FAQ** | (latest gen) | ✅ Generated with HTML |
| **CTA Banner + Footer** | (latest gen) | ✅ Generated with HTML |

### Current Problem — Stitch Output Not Satisfactory
Cody reviewed the generated "Hero + About" screen and is **not happy with the result**. The Stitch-generated version:
- Captured the general structure (centered headline, chart, features, about section)
- Used the Dominion Dark Ether design system
- BUT something about the execution isn't meeting expectations

**Possible issues to explore:**
1. The Stitch output may look too generic / template-y compared to the original inspiration
2. The gradient colors or typography may not feel right
3. The growth chart visual may not be as polished as the original
4. The overall "atmospheric" quality may be lacking
5. The layout spacing or proportions may feel off
6. The design system (Dark Ether) may need adjustment
7. The prompting strategy may need to be more specific or reference the original image differently

### Options to Consider
1. **Iterate in Stitch** — Edit the generated screens with more specific prompts
2. **Tweak the design system** — Adjust Dominion Dark Ether's colors, fonts, or design MD
3. **Generate variants** — Use Stitch's variant generation to explore alternatives
4. **Different approach** — Skip Stitch entirely and hand-code the design based on the inspiration image directly in the Astro site
5. **Hybrid** — Use Stitch for design exploration only, then hand-code the final version with more precision
6. **Different inspiration** — Find or generate a new reference design that better fits Dominion's brand

---

## Content (Already Finalized)

### Homepage H1s & Section Structure
- **Hero H1:** "Digital Marketing That Generates Leads or You Don't Pay"
- **Intro H2:** "Most Kansas City businesses that call us have already hired an agency."
- **Web Design H2:** "A Website That Actually Brings In Leads"
- **SEO/GEO H2:** "Rank on Google. Show Up in AI. Own Both."
- **Paid Ads H2:** "Paid Ads That Produce Leads, Not Just Clicks"
- **Automation H2:** "Automate the Work That's Eating Your Day"
- **Guarantee H2:** "Results or You Don't Pay. That's the Offer."
- **FAQ:** 4 questions with full answers
- **CTA:** "Ready to stop wondering where your next client is coming from?"

### Service Categories (GBP)
1. Website Designer
2. Internet Marketing Service
3. Advertising Agency
4. Automation Company

### Pricing Tiers
- **Free Tier:** Landing page + $200/mo hosting
- **Authority Accelerator:** $6,000 setup + $400/mo (5-7 page site, SEO, GBP)
- **Total Online Omnipresence:** $10,000 setup + $1,500/mo (30-40 pages, SEO, GEO, social, ads, automation)

### Guarantees
- Unconditional site guarantee (full refund if not satisfied with site)
- 90-day results guarantee (keep working free if no qualified leads)

### Target Service Areas
Kansas City MO/KS, Overland Park, Olathe, Lee's Summit, Independence, Liberty, Blue Springs, Shawnee, Leawood, Leavenworth, Parkville, Gladstone, North Kansas City

---

## Key Files & Assets

### Project Structure
```
dominion-digital/
├── src/
│   ├── pages/
│   │   └── index.astro          ← Full homepage (Phase 1 build)
│   └── styles/
│       └── global.css           ← Complete design system
├── public/
│   └── images/
│       ├── logo-icon.png        ← Diamond shield icon
│       ├── logo-white.png       ← Full logo, white text
│       ├── logo-black.png       ← Full logo, black text
│       ├── hero-bg.png          ← KC skyline (AI generated)
│       ├── web-design.png       ← Monitor mockup (AI generated)
│       ├── seo-geo.png          ← Network visual (AI generated)
│       ├── paid-ads.png         ← Funnel/analytics (AI generated)
│       └── automation.png       ← Automation/workflow (AI generated)
├── content-homepage-dominion-digital.md
├── conversion-copy-dominion-digital.md
├── site-structure-dominion-digital.md
├── offers-dominion-digital.md
└── MEMORY.md                   ← This file
```

### Design Skills Referenced
- **Taste skill:** `c:\Users\Cody\.claude\skills\taste\SKILL.md` — Design engineering directives for typography, color, layout, motion
- **Local SEO content skill:** `c:\Users\Cody\.claude\skills\local-seo-content\SKILL.md` — Used for content generation

### Stitch MCP Config
Located at `c:\Users\Cody\.gemini\antigravity\mcp_config.json`
- Server: `@_davideast/stitch-mcp` with `proxy` command
- Uses `STITCH_API_KEY` environment variable

---

## Next Steps — Decision Point
1. Decide on design direction: iterate Stitch, hand-code from inspiration, or hybrid
2. Once design is locked, implement final homepage in Astro
3. Replace lorem ipsum in Stitch sections with final SEO copy if pulling from Stitch
4. Build remaining pages (contact, pricing, service pages, location pages)
5. Deploy
