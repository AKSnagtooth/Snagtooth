# Snagtooth Visual Redesign Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Redesign the visual layer of `index.html` to match the actual Snagtooth brand — correct fonts, colors, color blocking, pill buttons, two-tone hero, and proper section treatments.

**Architecture:** Single HTML file with inline CSS/JS. All changes are within the existing `<style>` block (CSS) and the `<body>` (HTML). Copy, section order, form logic, section IDs, and JS functions are locked — visual layer only.

**Tech Stack:** Vanilla HTML/CSS. Google Fonts (Anton + Barlow). No build tools. Verify each task by opening `index.html` in a browser at both desktop (1280px) and mobile (375px DevTools).

---

## Ground Rules

- **File to modify:** `/Users/aleksanderkocev/Desktop/Web_Dev/Projects/Snagtooth/index.html`
- **Never change:** section IDs (`#hero`, `#logos`, `#problem`, `#why`, `#work`, `#services`, `#process`, `#testimonials`, `#pricing`, `#contact`), any body copy/headlines, form fields, JS functions (`goToStep2`, `goToStep1`, `selectRadio`, `submitForm`)
- **Verification:** Open `index.html` in browser. No server needed — just `open index.html` or drag into Chrome.
- **Logo file:** `assets/snagtooth-logo.png` — use as `<img>` tag

---

## Task 1: CSS Foundation — Variables, Fonts, Buttons

**Files:**
- Modify: `index.html` lines 14 (fonts link), 16–30 (CSS variables), 57 (h tag styles), 77–109 (buttons)

**Step 1: Swap Google Fonts import (line 14)**

Replace:
```html
<link href="https://fonts.googleapis.com/css2?family=Big+Shoulders+Display:wght@400;600;700;800;900&family=Big+Shoulders+Text:wght@300;400;500;600&display=swap" rel="stylesheet" />
```
With:
```html
<link href="https://fonts.googleapis.com/css2?family=Anton&family=Barlow:wght@300;400;500;600;700&display=swap" rel="stylesheet" />
```

**Step 2: Replace all CSS variables (lines 16–30)**

Replace the entire `:root` block with:
```css
:root {
  --black:          #17180F;
  --charcoal:       #1E1F14;
  --charcoal-mid:   #242516;
  --charcoal-light: #2C2D1A;
  --bone:           #E8E2CC;
  --bone-dim:       #9E9880;
  --orange:         #FF5C00;
  --orange-hot:     #FF6D1A;
  --orange-dim:     #7A2C00;
  --gold:           #C9A84C;
  --line:           rgba(232,226,204,0.08);
  --line-hot:       rgba(255,92,0,0.25);
  --font-display:   'Anton', sans-serif;
  --font-body:      'Barlow', sans-serif;
}
```

**Step 3: Update h1–h4 base styles (line 57)**

Replace:
```css
h1, h2, h3, h4 { font-family: var(--font-display); line-height: 1.0; letter-spacing: 0.01em; }
```
With:
```css
h1, h2, h3, h4 { font-family: var(--font-display); line-height: 0.9; letter-spacing: -0.01em; }
```

**Step 4: Redesign buttons**

Replace the entire button block (`.btn`, `.btn--primary`, `.btn--ghost` and their hovers) with:
```css
.btn {
  display: inline-block;
  font-family: var(--font-display);
  font-size: 0.95rem;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  text-decoration: none;
  padding: 16px 36px;
  border-radius: 40px;
  border: none;
  cursor: pointer;
  transition: all 0.2s ease;
}

.btn--primary {
  background: var(--bone);
  color: var(--black);
}
.btn--primary:hover {
  background: var(--orange);
  color: white;
}

.btn--ghost {
  background: transparent;
  color: var(--bone);
  border: 2px solid var(--bone);
}
.btn--ghost:hover {
  border-color: var(--orange);
  color: var(--orange);
}
```

**Step 5: Verify**

Open `index.html` in browser. Check:
- Font is Anton (condensed, heavy) — headlines should look dramatically different from Big Shoulders
- Buttons are pill-shaped (rounded corners)
- Primary button is cream/bone colored, not orange
- Orange is a brighter, purer `#FF5C00` vs the old brownish orange

**Step 6: Commit**
```bash
cd /Users/aleksanderkocev/Desktop/Web_Dev/Projects/Snagtooth
git add index.html
git commit -m "style: CSS foundation — Anton/Barlow fonts, correct brand variables, pill buttons"
```

---

## Task 2: Nav + Logo

**Files:**
- Modify: `index.html` lines 111–221 (nav CSS), 1192–1227 (nav HTML), 1702–1727 (footer HTML)

**Step 1: Update nav scrolled state (line 119–124)**

Replace:
```css
nav.scrolled {
  background: rgba(8,8,8,0.95);
  backdrop-filter: blur(12px);
  padding: 14px 0;
  border-bottom: 1px solid var(--line);
}
```
With:
```css
nav.scrolled {
  background: rgba(23,24,15,0.96);
  backdrop-filter: blur(12px);
  padding: 14px 0;
  border-bottom: 1px solid var(--line);
}
```

**Step 2: Replace nav logo SVG with actual image (line 1195–1202)**

Replace the `<a href="#hero" class="nav-logo">` block (SVG logo) with:
```html
<a href="#hero" class="nav-logo">
  <img src="assets/snagtooth-logo.png" alt="Snagtooth" style="height: 40px; width: auto;" />
</a>
```

**Step 3: Replace footer logo SVG (lines 1707–1711)**

Replace the footer `<svg ...>` logo with:
```html
<img src="assets/snagtooth-logo.png" alt="Snagtooth" style="height: 34px; width: auto;" />
```

**Step 4: Verify**

Open `index.html`. Check:
- Nav shows the chain-badge logo PNG at correct height
- Footer shows the same logo
- "Book a Call" button in nav is pill-shaped, bone colored

**Step 5: Commit**
```bash
git add index.html
git commit -m "style: swap nav/footer logo to actual PNG asset"
```

---

## Task 3: Hero — Two-Tone Redesign

**Files:**
- Modify: `index.html` — hero CSS (lines 223–310), hero HTML (lines 1230–1252)

The target: dark `#hero` section with ONLY the big poster headline. Then a hard-cut full-orange section directly below with the subheadline + CTA + social proof. The `#logos` section that follows will become the "Our Partners" bar (Task 4).

**Step 1: Update hero CSS**

Replace the `#hero` block and `.hero-headline` styles:

```css
#hero {
  min-height: 80vh;
  display: flex;
  align-items: flex-end;
  padding-top: 120px;
  padding-bottom: 60px;
  position: relative;
  overflow: hidden;
  background: var(--black);
}

/* Remove the hero-bg gradient — replace with nothing */
.hero-bg { display: none; }

.hero-content { position: relative; z-index: 1; width: 100%; }

.hero-eyebrow {
  font-family: var(--font-body);
  font-size: 0.8rem;
  font-weight: 500;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--bone-dim);
  margin-bottom: 20px;
}

.hero-headline {
  font-family: var(--font-display);
  font-size: clamp(5rem, 14vw, 14rem);
  line-height: 0.87;
  text-transform: uppercase;
  letter-spacing: -0.01em;
  color: var(--bone);
  margin-bottom: 0;
}
```

Add a new CSS block for the orange hero sub-section:
```css
/* HERO ORANGE SUB-SECTION */
.hero-orange {
  background: var(--orange);
  padding: 60px 0;
}

.hero-orange-inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 40px;
  flex-wrap: wrap;
}

.hero-orange-sub {
  font-family: Georgia, 'Times New Roman', serif;
  font-size: clamp(1.6rem, 3.5vw, 2.8rem);
  font-style: italic;
  color: white;
  max-width: 700px;
  line-height: 1.2;
}

.hero-orange-proof {
  font-family: var(--font-body);
  font-size: 0.78rem;
  color: rgba(255,255,255,0.7);
  margin-top: 12px;
  letter-spacing: 0.04em;
}

@media (max-width: 768px) {
  .hero-orange-inner { flex-direction: column; align-items: flex-start; }
  #hero { min-height: 70vh; padding-top: 100px; }
}
```

**Step 2: Update hero HTML**

Replace the entire `<section id="hero">...</section>` block (lines 1230–1252) with:
```html
<!-- ============ HERO ============ -->
<section id="hero">
  <div class="hero-bg"></div>
  <div class="container">
    <div class="hero-content">
      <p class="hero-eyebrow">Creative Production + Paid Media</p>
      <h1 class="hero-headline">
        Your Agency<br>
        Makes Pretty Ads.<br>
        We Make<br>
        Ads That Sell.
      </h1>
    </div>
  </div>
</section>

<!-- HERO ORANGE SUB-SECTION -->
<div class="hero-orange">
  <div class="container">
    <div class="hero-orange-inner">
      <div>
        <p class="hero-orange-sub">One team, one roof — the person who builds your ad is the same one reading your data.</p>
        <p class="hero-orange-proof">Trusted by BOSS, Maui &amp; Sons, Young Nails, Converse, and the New York Islanders</p>
      </div>
      <a href="#contact" class="btn btn--ghost" style="white-space:nowrap; border-color:white; color:white; flex-shrink:0;">Get Started →</a>
    </div>
  </div>
</div>
```

**Step 3: Verify**

Open `index.html`. Check:
- Hero headline is HUGE — fills most of the viewport width, bone on near-black
- Below it: hard-cut full orange block with serif italic subheadline in white
- "Get Started →" is a pill ghost button on the right of the orange block
- No gradient anywhere — just flat dark, then hard-cut orange

**Step 4: Commit**
```bash
git add index.html
git commit -m "style: two-tone hero — dark headline block + orange sub-section"
```

---

## Task 4: Partners Bar — Full Orange "Our Partners"

**Files:**
- Modify: `index.html` — `#logos` CSS (lines 312–348), logos HTML (lines 1254–1269)

**Step 1: Replace `#logos` CSS**

Remove the existing `#logos`, `.logos-label`, `.logos-row`, `.logo-pill` blocks and replace with:
```css
/* ============ PARTNERS BAR ============ */
#logos {
  background: var(--orange);
  padding: 70px 0 60px;
}

.partners-title {
  font-family: Georgia, 'Times New Roman', serif;
  font-size: clamp(2rem, 4vw, 3.2rem);
  font-style: italic;
  color: white;
  text-align: center;
  margin-bottom: 48px;
}

.logos-row {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 40px;
  flex-wrap: wrap;
}

.logo-pill {
  font-family: var(--font-body);
  font-weight: 700;
  font-size: 1rem;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: white;
  opacity: 0.85;
  white-space: nowrap;
  transition: opacity 0.2s;
}
.logo-pill:hover { opacity: 1; }

/* Special treatment for script-style brands */
.logo-pill--script {
  font-family: Georgia, serif;
  font-style: italic;
  font-weight: 400;
  letter-spacing: 0;
  font-size: 1.1rem;
}

@media (max-width: 768px) {
  .logos-row { gap: 24px; }
  .logo-pill { font-size: 0.85rem; }
}
```

**Step 2: Replace `#logos` HTML**

Replace the `<section id="logos" ...>` block with:
```html
<!-- ============ PARTNERS BAR ============ -->
<section id="logos">
  <p class="partners-title">Our Partners</p>
  <div class="container">
    <div class="logos-row">
      <span class="logo-pill">VANS</span>
      <span class="logo-pill logo-pill--script">young nails</span>
      <span class="logo-pill">CONVERSE</span>
      <span class="logo-pill">SELDOM SEEN</span>
      <span class="logo-pill">BOSS</span>
      <span class="logo-pill">University of Oregon</span>
      <span class="logo-pill">adidas</span>
      <span class="logo-pill">FUCKING AWESOME</span>
    </div>
  </div>
</section>
```

**Step 3: Verify**

Open `index.html`. Check:
- Partners section is full saturated orange (#FF5C00), no borders
- "Our Partners" heading is serif italic, centered, white
- 8 brand names in a row, white text, slightly reduced opacity
- Hard cut from dark hero-sub (wait — the hero-orange div and this section would both be orange and merge visually — that's intentional: dark hero → orange sub → orange partners → hard cut back to dark problem)

**Step 4: Commit**
```bash
git add index.html
git commit -m "style: partners bar — full orange, Georgia serif title, white logos"
```

---

## Task 5: Color Blocking — Problem, Solution, Case Studies

**Files:**
- Modify: `index.html` CSS blocks for `#problem` (line 351), `#why`/solution (line 413), `#work` (line 487)

**Step 1: Problem section — dark + orange pain card accents**

The `#problem` section already has `background: var(--charcoal)`. Update the pain cards to have more presence:

Replace `.pain-card` styles:
```css
.pain-card {
  padding: 32px 36px;
  background: var(--charcoal-mid);
  border-left: 3px solid var(--orange-dim);
  transition: border-color 0.2s, background 0.2s;
}
.pain-card:hover {
  border-color: var(--orange);
  background: var(--charcoal-light);
}

.pain-card-title {
  font-family: var(--font-display);
  font-size: 1rem;
  letter-spacing: 0.05em;
  text-transform: uppercase;
  margin-bottom: 10px;
  color: var(--bone);
}
```

Update `.problem-headline` size:
```css
.problem-headline {
  font-size: clamp(2.4rem, 5vw, 4.8rem);
  line-height: 0.9;
  margin-bottom: 28px;
}
```

**Step 2: Solution/Why section — FULL ORANGE background**

The `#why` section needs a complete color flip. Replace the `#solution` / related CSS and add to it:

```css
#why {
  background: var(--orange);
  position: relative;
  overflow: hidden;
}

/* On orange bg, labels and text need to flip */
#why .label {
  color: rgba(23,24,15,0.6);
}

#why .solution-headline {
  color: var(--black);
}
#why .solution-headline .accent {
  color: var(--black);
  -webkit-text-stroke: 1px var(--black);
}

#why .solution-sub,
#why .solution-body {
  color: rgba(23,24,15,0.7);
}
#why .solution-body strong {
  color: var(--black);
}

/* Diff cards on orange bg */
#why .diff-cards { margin-top: 60px; }
#why .diff-card {
  background: rgba(23,24,15,0.08);
  border-top: 2px solid rgba(23,24,15,0.3);
}
#why .diff-number {
  color: rgba(23,24,15,0.2);
}
#why .diff-title { color: var(--black); }
#why .diff-card p { color: rgba(23,24,15,0.65); }
```

**Step 3: Case Studies section — keep dark, punch up stat display**

`#work` already has `background: var(--charcoal)`. Update the stat color to use the new orange:
```css
.cs-stat-big {
  font-family: var(--font-display);
  font-size: clamp(4rem, 7vw, 8rem);
  color: var(--orange);
  line-height: 0.9;
  display: block;
}
```

Update `.section-headline` to be bigger:
```css
.section-headline {
  font-size: clamp(3rem, 7vw, 7rem);
  line-height: 0.9;
}
```

**Step 4: Verify**

Open `index.html`. Check:
- Problem: dark background, pain cards with left orange border
- Solution/Why: FULL ORANGE background — dark/black text, everything readable
- Case Studies: dark background, orange stats pop

**Step 5: Commit**
```bash
git add index.html
git commit -m "style: color blocking — solution section orange bg, stat sizes updated"
```

---

## Task 6: Services Section — Giant Headline Layout

**Files:**
- Modify: `index.html` — services CSS (lines 621–731), services HTML (lines 1447–1491)

**Step 1: Replace services CSS**

Replace the entire services CSS block with:
```css
/* ============ SERVICES ============ */
#services {
  background: var(--black);
  padding: 100px 0;
}

.services-layout {
  display: grid;
  grid-template-columns: 1fr 1.4fr;
  gap: 80px;
  align-items: start;
}

.services-headline-block {}

.services-big-headline {
  font-family: var(--font-display);
  font-size: clamp(4rem, 9vw, 10rem);
  line-height: 0.88;
  color: var(--bone);
  text-transform: uppercase;
  margin-bottom: 32px;
}

.services-label {
  font-family: var(--font-body);
  font-size: 0.8rem;
  font-weight: 500;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--bone-dim);
  margin-bottom: 20px;
}

.services-intro {
  font-size: 0.95rem;
  color: var(--bone-dim);
  line-height: 1.75;
  margin-bottom: 40px;
  max-width: 340px;
}

.services-cta { display: inline-block; }

.services-columns {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 48px;
}

.service-col {}

.service-category-label {
  font-family: var(--font-display);
  font-size: 1.1rem;
  color: var(--gold);
  letter-spacing: 0.06em;
  text-transform: uppercase;
  margin-bottom: 20px;
  display: block;
}

.service-list {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 10px;
  margin-bottom: 24px;
}
.service-list li {
  font-family: var(--font-body);
  font-size: 0.9rem;
  color: var(--bone-dim);
  display: flex;
  align-items: flex-start;
  gap: 10px;
  line-height: 1.55;
}
.service-list li::before {
  content: '—';
  color: var(--orange);
  flex-shrink: 0;
}

.service-note {
  font-family: var(--font-body);
  font-size: 0.82rem;
  color: var(--bone-dim);
  font-style: italic;
  line-height: 1.6;
  padding-top: 16px;
  border-top: 1px solid var(--line);
}

.not-included {
  margin-top: 60px;
  padding: 32px 40px;
  background: var(--charcoal);
  border-left: 3px solid var(--orange-dim);
}

.not-included-title {
  font-family: var(--font-display);
  font-size: 0.7rem;
  letter-spacing: 0.16em;
  text-transform: uppercase;
  color: var(--bone-dim);
  margin-bottom: 12px;
}

.not-included p {
  font-size: 0.88rem;
  color: var(--bone-dim);
  line-height: 1.7;
}
.not-included strong { color: var(--bone); }

@media (max-width: 900px) {
  .services-layout { grid-template-columns: 1fr; gap: 48px; }
  .services-columns { grid-template-columns: 1fr; gap: 32px; }
  .not-included { padding: 28px 24px; }
}
```

**Step 2: Replace services HTML**

Replace the entire `<section id="services">...</section>` block with:
```html
<!-- ============ SERVICES ============ -->
<section id="services">
  <div class="container">
    <div class="services-layout reveal">
      <div class="services-headline-block">
        <p class="services-label">What We Do</p>
        <h2 class="services-big-headline">WHAT<br>WE<br>OFFER</h2>
        <p class="services-intro">We are not a full-service agency. We do two things and we do them at a level most agencies can't match with ten.</p>
        <a href="#contact" class="btn btn--primary services-cta">Contact Us →</a>
      </div>
      <div>
        <div class="services-columns reveal reveal-delay-1">
          <div class="service-col">
            <span class="service-category-label">Creative Production</span>
            <ul class="service-list">
              <li>Concept development and creative strategy</li>
              <li>Video production — anthem, short-form, UGC-style</li>
              <li>Static and motion ad creative (Meta, Google, YouTube)</li>
              <li>Landing page design and copywriting</li>
              <li>Brand refresh and visual identity (when it's the root of the problem)</li>
            </ul>
            <p class="service-note">Production quality from a former LA Kings Creative Director. Built for the data, not the awards shelf.</p>
          </div>
          <div class="service-col">
            <span class="service-category-label">Paid Media</span>
            <ul class="service-list">
              <li>Campaign architecture and audience strategy</li>
              <li>Creative testing frameworks (thumbstop, CTR, CAC by creative)</li>
              <li>Weekly optimization based on real performance data</li>
              <li>Retargeting systems and funnel sequencing</li>
              <li>Reporting on CAC, ROAS, and revenue — not vanity metrics</li>
            </ul>
            <p class="service-note">We report on the numbers that affect your P&amp;L. That's it.</p>
          </div>
        </div>
        <div class="not-included reveal">
          <p class="not-included-title">What We Don't Do</p>
          <p>Organic social. Community management. Influencer outreach. SEO. Email marketing. Podcast production. PR. <strong>We stay in our lane because our lane is where we win.</strong> If you need those things, we'll point you to someone good.</p>
        </div>
      </div>
    </div>
  </div>
</section>
```

**Step 3: Verify**

Open `index.html`. Check:
- "WHAT WE OFFER" is stacked vertically, huge Anton font, bone on dark
- "CREATIVE PRODUCTION" and "PAID MEDIA" labels are gold (#C9A84C)
- Service lists use `—` dash in orange
- "Contact Us" button is pill-shaped, bone/cream

**Step 4: Commit**
```bash
git add index.html
git commit -m "style: services section — giant stacked headline, gold category labels, two-column layout"
```

---

## Task 7: Process (Orange) + Testimonials (Orange Gradient)

**Files:**
- Modify: `index.html` — process CSS (lines 733–787), testimonials CSS (lines 789–844), and their section HTML

**Step 1: Process section — full orange background**

Replace `#process { background: var(--charcoal); }` with:
```css
#process {
  background: var(--orange);
}
```

Add scoped overrides for all text inside process on orange bg:
```css
#process .label { color: rgba(23,24,15,0.55); }
#process .section-headline { color: var(--black); }
#process .section-headline .text-orange { color: var(--black); }
#process .step-number { color: rgba(23,24,15,0.12); }
#process .step-title { color: var(--black); }
#process .step-body { color: rgba(23,24,15,0.65); }

#process .process-step {
  background: rgba(23,24,15,0.07);
  padding: 48px 36px;
}

#process .process-coda {
  border-left: 3px solid rgba(23,24,15,0.3);
  background: rgba(23,24,15,0.05);
}
#process .process-coda p { color: rgba(23,24,15,0.65); }
#process .process-coda strong { color: var(--black); }
```

**Step 2: Testimonials section — orange gradient**

Replace `#testimonials {}` with:
```css
#testimonials {
  background: linear-gradient(160deg, #FF5C00 0%, #E8683A 100%);
}
```

Add scoped overrides for testimonial cards on gradient bg:
```css
#testimonials .label { color: rgba(23,24,15,0.55); }
#testimonials .section-headline { color: var(--black); }

#testimonials .testimonial {
  background: rgba(23,24,15,0.07);
  backdrop-filter: blur(4px);
}

#testimonials .testimonial-quote {
  color: var(--black);
}
#testimonials .testimonial-quote::before {
  color: rgba(23,24,15,0.3);
}

#testimonials .testimonial-author {
  border-top: 1px solid rgba(23,24,15,0.15);
}
#testimonials .testimonial-name { color: var(--black); }
#testimonials .testimonial-title { color: rgba(23,24,15,0.6); }
```

**Step 3: Verify**

Open `index.html`. Check:
- Process section: full saturated orange, dark/black text, step numbers are ghost-dark
- Testimonials: orange-to-coral gradient, dark text on semi-transparent cards

**Step 4: Commit**
```bash
git add index.html
git commit -m "style: process orange bg, testimonials orange-to-coral gradient"
```

---

## Task 8: Pricing, Contact, Footer + Halftone Texture + Mobile Polish

**Files:**
- Modify: `index.html` — pricing CSS, contact CSS, footer CSS, orange section texture

**Step 1: Pricing section — dark with orange accent**

`#pricing` already has `background: var(--charcoal)`. Update the pricing card:
```css
.pricing-card {
  max-width: 760px;
  margin: 60px auto 0;
  background: var(--charcoal-mid);
  border: 1px solid var(--line);
  padding: 56px 56px;
  border-radius: 0;
}

.pricing-amount {
  font-family: var(--font-display);
  font-size: clamp(2.5rem, 5vw, 5rem);
  text-transform: uppercase;
  line-height: 0.9;
  margin-bottom: 8px;
  color: var(--bone);
}
.pricing-amount span { color: var(--orange); }
```

**Step 2: Add halftone texture to all orange sections**

Add this CSS just before the `/* ============ SCROLL ANIMATIONS ============ */` comment:

```css
/* ============ HALFTONE TEXTURE — ORANGE SECTIONS ============ */
.hero-orange::after,
#logos::after,
#why::after,
#process::after,
#testimonials::after {
  content: '';
  position: absolute;
  inset: 0;
  background-image: radial-gradient(circle, rgba(23,24,15,0.15) 1px, transparent 1px);
  background-size: 6px 6px;
  pointer-events: none;
  z-index: 0;
}

/* Ensure content inside orange sections stays above the texture */
.hero-orange { position: relative; }
#logos { position: relative; }
#why { position: relative; }
#process { position: relative; }
#testimonials { position: relative; }

.hero-orange .container,
#logos .partners-title,
#logos .container,
#why .container,
#process .container,
#testimonials .container {
  position: relative;
  z-index: 1;
}
```

**Step 3: Footer — update font references**

The footer SVG logo references `'Big Shoulders Display'` in the text element. That was already replaced in Task 2. Verify the footer looks correct. Update footer links font if needed:
```css
.footer-links a {
  font-family: var(--font-body);
  font-size: 0.78rem;
  font-weight: 600;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--bone-dim);
  text-decoration: none;
  transition: color 0.2s;
}
```

**Step 4: Mobile pass — verify at 375px**

Open browser DevTools, set to 375px width. Check:
- Hero headline doesn't overflow — `clamp(5rem, 14vw, 14rem)` at 375px = `5rem = 80px` ✓
- Orange hero sub-block: CTA button stacks below subheadline ✓
- Partners logos wrap cleanly (flex-wrap) ✓
- Services: single column, big headline collapses to readable size ✓
- Process steps: single column ✓
- Testimonials: single column ✓
- Form: full width inputs ✓
- No horizontal scroll ✓

**Step 5: Verify full page**

Scroll the full page top-to-bottom at desktop. Confirm the color-block sequence:
1. `#hero` — near-black (`#17180F`)
2. `.hero-orange` — full orange
3. `#logos` — full orange (merges with above, hard cut from dark below)
4. `#problem` — dark (`#1E1F14`)
5. `#why` — full orange
6. `#work` — dark
7. `#services` — dark (`#17180F`)
8. `#process` — full orange
9. `#testimonials` — orange gradient
10. `#pricing` — dark
11. `#contact` — dark
12. `footer` — dark

**Step 6: Commit**
```bash
git add index.html
git commit -m "style: halftone texture on orange sections, pricing polish, mobile verify"
```

---

## Final Checklist

Before declaring done, confirm:

- [ ] Font is Anton (not Big Shoulders) — headlines are condensed, heavy, wall-like
- [ ] Orange is `#FF5C00` — electric, not brownish
- [ ] All buttons are pill-shaped (40px radius)
- [ ] Primary button = bone/cream background, dark text, orange hover
- [ ] Hero: massive headline on dark, hard-cut to orange sub-block below
- [ ] Partners bar: full orange, "Our Partners" in Georgia italic
- [ ] Problem: dark. Solution: orange. Case studies: dark. Services: dark. Process: orange. Testimonials: orange gradient.
- [ ] Services: giant stacked "WHAT WE OFFER" on left, gold category labels
- [ ] All body copy is unchanged
- [ ] Logo is the actual PNG, not SVG placeholder
- [ ] No gradients between sections — hard cuts only
- [ ] Mobile at 375px: no overflow, no horizontal scroll, buttons thumbable
- [ ] Form logic works: step 1 → step 2 → confirmation
