# Snagtooth.com — Claude Code Design Brief
**For use with:** `snagtooth-homepage.html` (base HTML with all copy, structure, and form logic)
**Goal:** Redesign the visual layer to match actual Snagtooth brand. Copy and structure are locked. Design is not.

---

## What's Working (Keep)
- All copy — do not change any text
- All section structure and scroll order
- 2-step contact form logic and JS
- Mobile-first responsive breakpoints
- Scroll reveal animations
- Nav hamburger + mobile menu logic
- SEO meta tags

---

## What Needs a Full Visual Overhaul

### 1. Brand Colors — Replace All CSS Variables With These

```css
:root {
  --black:         #17180F;   /* near-black olive — NOT pure black */
  --charcoal:      #1E1F14;   /* section background dark */
  --charcoal-mid:  #242516;   /* card backgrounds */
  --charcoal-light:#2C2D1A;   /* hover states */
  --bone:          #E8E2CC;   /* primary text — warm cream */
  --bone-dim:      #9E9880;   /* secondary text */
  --orange:        #FF5C00;   /* PRIMARY orange — pure, fully saturated */
  --orange-hot:    #FF6D1A;   /* hover orange */
  --orange-dim:    #7A2C00;   /* dark orange for borders/accents */
  --gold:          #C9A84C;   /* accent gold — used on category labels */
  --line:          rgba(232,226,204,0.08);
  --line-hot:      rgba(255,92,0,0.25);
}
```

---

### 2. Typography — Swap Google Font

Replace `Big Shoulders Display` with **Anton** (Google Fonts, free):

```html
<link href="https://fonts.googleapis.com/css2?family=Anton&family=Barlow:wght@300;400;500;600;700&display=swap" rel="stylesheet" />
```

- `--font-display: 'Anton', sans-serif;` — hero headlines, section headers, nav labels
- `--font-body: 'Barlow', sans-serif;` — body copy, form labels, small text

**Typography scale rules:**
- Hero headline: `clamp(5rem, 13vw, 13rem)` — fills the full viewport width, flush left
- Section headlines: `clamp(3.5rem, 8vw, 9rem)` — same massive energy
- Anton is ALL-CAPS by nature — no `text-transform` needed
- Line height on display: `0.88` — tight, stacked, poster-style
- Body copy stays readable: `font-size: 1rem`, `line-height: 1.75`

---

### 3. Section Color Blocking — The Key Visual Move

The real site uses **hard-cut full-viewport color blocks** — not subtle dark cards. 

**Pattern to implement:**

| Section | Background | Text | Accent |
|---|---|---|---|
| Hero | `var(--black)` | `var(--bone)` | — |
| Logo/Partners bar | `var(--orange)` | white | — |
| Problem | `var(--black)` | `var(--bone)` | `var(--orange)` border |
| Solution/Why | `var(--orange)` | `var(--black)` | — |
| Case Studies | `var(--black)` | `var(--bone)` | `var(--orange)` stats |
| Services | `var(--black)` | `var(--bone)` | `var(--gold)` category labels |
| Process | `var(--orange)` | `var(--black)` | — |
| Testimonials | `var(--orange)` | `var(--black)` | gradient to `#E8683A` |
| Pricing | `var(--black)` | `var(--bone)` | `var(--orange)` |
| Contact | `var(--black)` | `var(--bone)` | `var(--orange)` |

**Critical:** No soft gradients between sections. Hard cut, full-width. When switching from dark to orange, the color change IS the divider.

---

### 4. Logo — Replace SVG Placeholder

Replace the nav SVG badge with the actual logo image:

```html
<a href="#hero" class="nav-logo">
  <img src="assets/snagtooth-logo.png" alt="Snagtooth" style="height: 38px; width: auto;" />
</a>
```

Create an `assets/` folder. The logo file is `OG_STICKER_DESIGNS.png` — use the chain badge version.

---

### 5. Partners Bar — Match the Real Site

The partners section should be:
- Full `var(--orange)` background
- Serifed headline "Our Partners" — use `font-family: 'Georgia', serif` or similar
- White logo text/wordmarks at reduced opacity (0.85)
- Horizontal row, evenly spaced
- Clients: Vans, Young Nails, Converse, BOSS (Boulder Outdoor Survival School), Adidas, University of Oregon, Seldom Seen, Fucking Awesome

---

### 6. Hero Section — Full-Bleed Poster Energy

The hero headline should feel like it's painted on a wall:

```css
.hero-headline {
  font-family: 'Anton', sans-serif;
  font-size: clamp(5rem, 14vw, 14rem);
  line-height: 0.87;
  text-transform: uppercase;
  letter-spacing: -0.01em;
  color: var(--bone);
  /* No max-width constraint — let it bleed */
}
```

Below the dark hero block, cut to a **full-width orange block** with the subheadline in the same Anton font but smaller, in `var(--bone)` or `var(--black)`. This is the two-tone hero effect from the real site.

---

### 7. Services Section — Match "What We Offer" Layout

Left side: Giant stacked headline "WHAT WE OFFER" in Anton, `var(--bone)`, dark background.
Right side: Two columns of service lists.
Category label style:
```css
.service-category-label {
  font-family: 'Anton', sans-serif;
  font-size: 1.3rem;
  color: var(--gold);  /* #C9A84C */
  letter-spacing: 0.06em;
  margin-bottom: 16px;
}
```

---

### 8. Buttons — Match Campaign Ad Style

Primary button from the ad creative:
```css
.btn--primary {
  background: var(--bone);
  color: var(--black);
  font-family: 'Anton', sans-serif;
  font-size: 0.95rem;
  letter-spacing: 0.1em;
  padding: 16px 36px;
  border-radius: 40px;  /* pill shape — matches "BOOK A CALL" button in ad */
  border: none;
}
.btn--primary:hover {
  background: var(--orange);
  color: white;
}
```

Ghost/secondary button:
```css
.btn--ghost {
  background: transparent;
  border: 2px solid var(--bone);
  color: var(--bone);
  border-radius: 40px;
  padding: 14px 36px;
}
```

---

### 9. Reference Screenshots

Feed Claude Code all 6 screenshots from the current snagtooth.com build, plus the ad creative and sticker logo. Say:

> "These screenshots show the existing Snagtooth website. Use the visual language — color blocking, typography scale, layout rhythm — and apply it to the HTML file I'm giving you. Do not change any copy. Redesign the visual layer to match this aesthetic while improving on the conversion structure."

---

### 10. Websites to Reference for Additional Inspiration

Drop URLs of sites with similar energy. Good targets to find and download HTML from:
- Supreme (supreme.com) — editorial hard-cut layout
- Fucking Awesome — raw streetwear energy
- Any Squarespace Fluid Engine site with editorial blocking

**Instructions for Claude Code:**
> "Here is the HTML base file. Here are brand screenshots. Here are reference sites. The copy, form logic, and section structure are locked. Redesign the visual design layer only: colors, typography, spacing, section backgrounds, button styles, and layout polish. Output a single updated HTML file."

---

## File Checklist for Claude Code Session

- [ ] `snagtooth-homepage.html` — the base file
- [ ] `OG_STICKER_DESIGNS.png` — logo
- [ ] `Screenshot_2026-03-08_at_11_02_51_PM.png` — ad creative reference
- [ ] `Screenshot_2026-03-08_at_11_06_04_PM.png` — hero section reference  
- [ ] `Screenshot_2026-03-08_at_11_06_16_PM.png` — orange block + halftone reference
- [ ] `Screenshot_2026-03-08_at_11_06_31_PM.png` — What We Do section
- [ ] `Screenshot_2026-03-08_at_11_06_44_PM.png` — What We Offer / services section
- [ ] `Screenshot_2026-03-08_at_11_06_55_PM.png` — Partners bar
- [ ] `Screenshot_2026-03-08_at_11_07_17_PM.png` — Testimonials section
- [ ] Any reference site HTML files you want to pull from

---

## What NOT to Change

- Any body copy or headlines
- Section order
- Form fields and step logic
- Anchor link IDs
- SEO meta tags
- Mobile breakpoints (keep mobile-first)
- Scroll reveal JS logic
