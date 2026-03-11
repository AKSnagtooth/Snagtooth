# CLAUDE.md — Snagtooth Website Project

You are working on **snagtooth.com** — the agency website for Snagtooth, a lean creative production + paid media agency founded by Aleks Kocev (former Creative Director, LA Kings) and Jasper Poore. This file is your complete operating context. Read it before touching anything.

---

## What Snagtooth Is

A two-person performance marketing agency specializing in Meta Ads and Google Ads with in-house creative production. The core differentiator: **the person who makes the ad is the person who reads the data**. No handoff. No broken telephone. No full-service bloat.

**What they do:** Creative production + paid media. That's it.
**What they don't do:** Organic social, SEO, community management, influencer outreach, PR.
**Target client:** DTC and lifestyle/outdoor brands doing $3M–$10M/year with $10K–$80K/month in ad spend.
**Retainers:** $2K–$6K/month. Month-to-month. No long-term contracts.

---

## Project Files

```
/
├── CLAUDE.md                          ← you are here
├── index.html                         ← primary build file
├── assets/
│   └── snagtooth-logo.png             ← chain badge logo (OG_STICKER_DESIGNS.png)
├── docs/
│   ├── PRD.md                         ← full product requirements, page architecture, success metrics
│   ├── ICP.md                         ← ideal customer profile, pain language, buying triggers
│   ├── research-summary.md            ← market landscape, competitive analysis, positioning gaps
│   ├── positioning.md                 ← Schwartz levels, angles, anti-positioning, headline tests
│   ├── copy.md                        ← full page copy, all 11 sections, voice-checked
│   └── claude-code-brief.md           ← visual design brief with color tokens, typography, layout rules
└── references/
    ├── ad-creative.png                ← campaign ad — primary visual reference
    ├── site-hero.png                  ← existing site hero section
    ├── site-orange-block.png          ← orange section + halftone treatment
    ├── site-what-we-do.png            ← what we do section
    ├── site-services.png              ← services layout with gold category labels
    ├── site-partners.png              ← partners bar — full orange, white logos
    └── site-testimonials.png          ← testimonials section design
```

---

## Brand Identity

### Colors (use these exact values, no substitutions)

```css
--black:          #17180F;   /* near-black olive — NOT pure black */
--charcoal:       #1E1F14;   /* dark section backgrounds */
--charcoal-mid:   #242516;   /* card backgrounds */
--charcoal-light: #2C2D1A;   /* hover states */
--bone:           #E8E2CC;   /* primary text — warm cream */
--bone-dim:       #9E9880;   /* secondary/muted text */
--orange:         #FF5C00;   /* PRIMARY — pure, fully saturated orange */
--orange-hot:     #FF6D1A;   /* hover state orange */
--orange-dim:     #7A2C00;   /* dark orange borders/accents */
--gold:           #C9A84C;   /* accent — service category labels only */
--line:           rgba(232,226,204,0.08);
```

### Typography

- **Display font:** Anton (Google Fonts) — hero headlines, section headers, nav
- **Body font:** Barlow — body copy, form labels, supporting text
- Hero headline size: `clamp(5rem, 14vw, 14rem)`, line-height `0.87`
- Section headline size: `clamp(3.5rem, 8vw, 9rem)`, line-height `0.9`
- Anton is naturally all-caps — no `text-transform` needed on display elements
- Body: `1rem`, line-height `1.75`

### Logo

File: `assets/snagtooth-logo.png` — the chain-border orange badge with SNAGTOOTH wordmark and tooth icon integrated in the T. Use as `<img>` tag, height 38–42px in nav.

### Visual Language

The site uses **hard-cut full-viewport color blocks**. Dark sections and full orange sections alternate with zero gradients between them. When a section switches from dark to orange, the color change IS the divider — no border, no fade.

Section color pattern:
- Hero → dark (`#17180F`)
- Partners bar → full orange (`#FF5C00`)
- Problem → dark
- Solution → full orange
- Case Studies → dark
- Services → dark with gold category labels
- Process → full orange
- Testimonials → orange gradient (`#FF5C00` → `#E8683A`)
- Pricing → dark
- Contact → dark
- Footer → dark

### Buttons

Primary: pill-shaped (`border-radius: 40px`), bone background, dark text. On hover: orange background, white text.
Ghost: pill-shaped, bone border, bone text. On hover: orange border + text.

---

## Site Architecture

Single HTML file (`index.html`). No external dependencies except Google Fonts. All CSS and JS inline.

**Page sections (in order):**
1. Hero — full-bleed poster headline, CTA, social proof micro-copy
2. Partners bar — full orange, "Our Partners", white client logos
3. Problem — mirrors ICP pain, three pain cards
4. Solution / Why Us — one-roof pitch, three differentiator cards
5. Case Studies — BOSS, FA×Converse, Middle Calling (real numbers)
6. Services — two columns: Creative Production + Paid Media, gold category labels
7. Process — three steps, orange background
8. Testimonials — Nick Sultana, Habib Salo, Jay Carson
9. Pricing — starting at $2K/mo, month-to-month, what's included
10. Contact Form — 2-step qualifying form → confirmation + Calendly link
11. Footer

**Navigation:** WORK · SERVICES · ABOUT — anchor links only, no separate pages. Sticky, collapses to hamburger on mobile.

---

## Conversion Flow

The site is a 24/7 salesperson. Primary goal: **booked discovery calls from qualified leads**.

Contact flow:
1. Visitor fills out qualifying form (Step 1: name, email, brand, URL)
2. Step 2: monthly ad budget (dropdown) + biggest challenge (radio select)
3. Confirmation screen: "Nice. We'll be in touch within 24 hours."
4. Calendly link appears: "Want to skip the wait? Book directly."

All form submissions go to email list regardless of whether they book. Form backend: Formspree (endpoint TBD — use placeholder `https://formspree.io/f/PLACEHOLDER`).

**Do not add friction.** The form is intentionally short. Do not add fields.

---

## Copy Rules — LOCKED

**All copy is final and voice-checked. Do not rewrite, paraphrase, or "improve" any copy.**

If you think copy needs to change, flag it with a comment — don't change it.

The voice is: direct, specific, practitioner-not-preacher, anti-corporate, slightly dangerous. Read `docs/copy.md` to internalize it before touching anything text-related.

**Words that must never appear in copy:**
- leverage, synergy, holistic, optimize, innovative, disruptive
- "we're passionate about"
- "full-service"
- "solutions"
- "storytelling" as a service descriptor
- "reach out" (say "call us" or "email us")

**Numbers that must stay exact:**
- 119x ROAS (FA×Converse, first 48 hours)
- 28.78x average ROAS
- $7.95 cost per purchase
- 218 enrollments / 63 enrollments (BOSS)
- $206 CAC on $6,300 product
- 90,000 followers / $0.41 per follow (Middle Calling)
- 93rd percentile growth on Meta
- 836 followers/day

---

## What You Can Change

- Visual design: colors, spacing, typography sizing, layout
- Section backgrounds to match color-block pattern above
- Button styles
- Card/component styling
- Animation timing and easing
- Mobile layout and responsive breakpoints
- Adding halftone texture effects or visual treatments to orange sections (reference `references/site-orange-block.png`)
- Logo swap from SVG placeholder to actual `assets/snagtooth-logo.png`

## What You Cannot Change

- Any body copy or headlines
- Section order
- Anchor link IDs (used for nav)
- Form field structure and 2-step logic
- Form JS functions: `goToStep2()`, `goToStep1()`, `selectRadio()`, `submitForm()`
- SEO meta title and description
- Section IDs: `#hero`, `#logos`, `#problem`, `#why`, `#work`, `#services`, `#process`, `#testimonials`, `#pricing`, `#contact`

---

## Open Items (Not Your Problem Yet)

These are placeholders — don't remove them, don't break the structure around them:

- `CALENDLY_LINK_HERE` — Aleks will provide the Calendly URL
- `FORMSPREE_ENDPOINT` — form submission endpoint TBD
- Logo file — use `assets/snagtooth-logo.png` once copied in
- Instagram and LinkedIn handles — footer social links TBD

---

## Performance Requirements

- Single HTML file, all CSS/JS inline
- No JS libraries (vanilla only)
- Load time target: under 2 seconds on mobile 4G
- Google Fonts only for external dependencies
- Images: only the logo + any assets explicitly added to `/assets`
- No carousels, no auto-play, no parallax

---

## Success Metrics (Post-Launch)

| Metric | Target |
|---|---|
| Bounce rate | < 50% |
| Time on page | > 2 min |
| Scroll depth to contact form | > 40% |
| Form completion rate | > 5% of visitors |
| Call booking rate (of completions) | > 30% |
| Lead quality (% that fit ICP) | > 60% |

---

## Key Business Context

**Founders:**
- Aleks Kocev — former Creative Director, LA Kings. Brings elite-level production quality.
- Jasper Poore — performance marketing and media buying.

**Current clients:** BOSS (Boulder Outdoor Survival School), Maui & Sons, Young Nails, RIGd Supply, Ages Skincare, NetRecovery, WolfCycle.ai, Community Brigade, Middle Calling, Literati

**Client logos visible on site:** Vans, Young Nails, Converse, Seldom Seen, BOSS, University of Oregon, Adidas, Fucking Awesome

**Positioning statement:** Snagtooth is the creative production + paid media team for DTC and lifestyle brands that are done paying agencies to make ads that don't convert.

**Anti-positioning:** Not a full-service agency. Not trying to be. We make ads and run ads. That's it.

---

## How to Work on This Project

1. Read this file first. Always.
2. Read `docs/PRD.md` for scope decisions.
3. Read `docs/claude-code-brief.md` for visual design specs.
4. Reference `/references/` screenshots before making any visual changes.
5. `index.html` is the single source of truth for the build.
6. Test on mobile viewport (375px) before considering anything done.
7. When in doubt: make it bigger, make it bolder, make it more orange.
