# Snagtooth.com — Product Requirements Document (PRD)
**Version:** 1.0
**Date:** March 2026
**Owner:** Aleks Kocev / Jasper Poore — Snagtooth

---

## 1. Project Overview

Build a production-ready homepage for snagtooth.com that converts visitors into qualified leads through a structured form-first flow before Calendly booking. The site is the primary digital footprint for the agency and must function as a 24/7 salesperson — closing warm referrals, converting cold paid traffic, and qualifying out unfit prospects before they reach the calendar.

---

## 2. Business Goals

1. **Generate qualified discovery calls** — primary KPI is booked calls from brands who fit the ICP ($3M–$10M revenue, DTC/lifestyle/outdoor, $10K–$80K/month ad spend)
2. **Qualify leads before booking** — form collects brand URL, monthly ad budget, and biggest challenge before Calendly access is granted
3. **Build the marketing list** — all form submissions added to email nurture sequence regardless of whether they book
4. **Establish credibility on first visit** — visitor should understand what Snagtooth does, who it's for, and why it works within 10 seconds of landing
5. **Support paid traffic** — mobile-first, fast-loading, scroll-optimized for Meta ad traffic

---

## 3. Scope

### In Scope — Phase 1 (This Build)
- Single-page homepage (index.html)
- Full nav with anchor links to page sections (no separate pages yet)
- Mobile-first responsive layout
- Multi-step contact form (qualifying questions) → Calendly embed or redirect
- All copy, section structure, and visual design
- SEO meta tags, OG tags
- Logo placeholder (to be swapped with real asset)

### Out of Scope — Phase 2 (Future)
- Case study detail pages
- Blog / content section
- Careers page
- Separate service pages
- CMS integration
- Email automation backend (form submissions handled via Formspree or similar)

---

## 4. Page Architecture

### Navigation (sticky, minimal)
- Logo (left)
- Nav links: Work · Services · Why Us · Pricing · Contact (right)
- CTA button: "Book a Call" (top right, primary color)

### Page Sections (in scroll order)

| # | Section | Purpose |
|---|---|---|
| 1 | **Hero** | Stop the scroll. State the value prop. One CTA. |
| 2 | **Social Proof Bar** | Logos: BOSS, Maui & Sons, Young Nails, New York Islanders, Converse |
| 3 | **Problem** | Mirror the ICP's pain. Agency frustration. The broken model. |
| 4 | **Solution / Differentiator** | The one-roof pitch. Why integrated beats fragmented. |
| 5 | **Case Studies** | 3 results snapshots with real numbers. BOSS, FA×Converse, Middle Calling. |
| 6 | **Services** | What Snagtooth actually does. Two pillars: Creative Production + Paid Media. |
| 7 | **How It Works** | 3-step process. Simple. De-risks the decision. |
| 8 | **Testimonials** | 3 quotes. Nick Sultana, Habib Salo, Jay Carson. |
| 9 | **Pricing** | Starting at $2K–$6K/month. Month-to-month. No bullshit. |
| 10 | **Contact Form** | Multi-step qualifying form. Step 1: Name/Email/Brand. Step 2: Budget/Challenge. Confirmation → Calendly. |
| 11 | **Footer** | Logo, nav links, social handles, legal. |

---

## 5. Contact Form Flow

### Step 1 — Who are you?
- Name (required)
- Email (required)
- Brand name (required)
- Website URL (required)

### Step 2 — Tell us about your situation
- Monthly ad budget (dropdown): Under $5K / $5K–$15K / $15K–$50K / $50K+ / Not running ads yet
- Biggest challenge (select one): Creative that converts / Scaling paid media / Both / Starting from scratch
- Anything else? (optional textarea, 2 lines max)

### Confirmation
- "Nice. We'll be in touch within 24 hours." message
- Calendly embed or link: "Want to skip the wait? Book directly."
- All submissions go to email list (Mailchimp / Klaviyo / Formspree — to be configured)

---

## 6. Design Directives

### Visual Identity
- **Palette:** Near-black background (#0D0D0D), off-white text (#F0EDE6), ember/burnt orange accent (#C45C26)
- **Typography:** Headlines — strong, wide-set sans-serif (e.g., Space Grotesk Bold or similar via Google Fonts). Body — clean, readable (Inter or similar)
- **Texture:** Subtle noise/grain overlay on hero. Not heavy. Just enough to feel tactile.
- **Imagery:** No stock photos. Placeholder blocks for actual creative/production shots. Dark, high-contrast aesthetic.
- **Borders/dividers:** Thin, warm-toned lines. No rounded corners on containers — sharp edges only.

### Mobile-First Rules
- Hero CTA must be thumb-reachable
- Section padding optimized for 375px+ width
- Sticky nav collapses to hamburger on mobile
- Case study cards stack vertically on mobile
- Form is two steps, not one long scroll — reduces drop-off

### Animations
- Subtle fade-in on scroll for section headers (CSS only, no JS libraries)
- No parallax. No auto-play video. No carousels.
- CTA button: subtle glow/pulse on hover

---

## 7. Technical Requirements

- Single HTML file with embedded CSS + minimal vanilla JS
- No external dependencies except Google Fonts
- Target load time: under 2 seconds on mobile 4G
- Semantic HTML for accessibility and SEO
- Meta title: "Snagtooth — Creative Production + Paid Media for DTC Brands"
- Meta description: "We make the ads. We run the ads. One team, one roof — no handoff. Results-driven creative and performance marketing for DTC and lifestyle brands."
- OG image: placeholder (to be replaced)
- Form action: Formspree endpoint (placeholder — to be configured with real endpoint)

---

## 8. Success Metrics (Post-Launch)

| Metric | Target |
|---|---|
| Bounce rate | < 50% |
| Time on page | > 2 minutes |
| Scroll depth to contact form | > 40% of visitors |
| Form completion rate | > 5% of visitors |
| Call booking rate (of form completions) | > 30% |
| Lead quality (% that fit ICP) | > 60% |

---

## 9. Build Sequence

1. ✅ Research Summary
2. ✅ ICP
3. ✅ PRD (this document)
4. ⬜ Positioning Angles
5. ⬜ Landing Page Copy
6. ⬜ Production HTML
7. ⬜ Expert Review Pass
8. ⬜ Final Output

---

## 10. Open Items / Decisions Needed from Aleks

- [ ] Calendly link URL
- [ ] Formspree or preferred form backend
- [ ] Real logo file upload (placeholder used in build)
- [ ] Social media handles (Instagram, LinkedIn)
- [ ] Any specific pricing tiers to display publicly (or "starting at $X")?
- [ ] Client logos approved for use (BOSS, Maui & Sons, Converse, NYI, Young Nails)
- [ ] Photography / creative assets for hero or case study sections (or confirm placeholder)
