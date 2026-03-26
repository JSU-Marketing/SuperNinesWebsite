# Super 9s Competition Website — Claude Code Brief

## Project Overview

Build a **single-page website** for a Super 9s GAA hurling competition. The site must be visually striking, fully mobile-optimised, and fun — built to impress sponsors, players, and fans alike.

---

## Tech Stack

- **Vanilla HTML/CSS/JS** — no frameworks, no build tools, single `index.html` file
- All assets (fonts, icons) loaded via CDN (Google Fonts, Font Awesome, etc.)
- Must work offline after initial load

---

## Color Scheme

- **Primary:** Purple (`#6B21A8` / `#7C3AED`)
- **Secondary:** White (`#FFFFFF`)
- **Accent:** Gold (`#F59E0B`) — for highlights, CTA buttons, countdown numbers
- **Dark base:** `#1A0533` for hero/footer sections

Use CSS custom properties (`--color-primary`, etc.) for the entire palette.

---

## Typography

- Use a **bold, characterful display font** (e.g. `Bebas Neue`, `Oswald`, or `Black Han Sans`) for headings and the competition name
- Use a clean, readable body font (e.g. `DM Sans`, `Nunito`, or `Outfit`) for body copy
- Load both from Google Fonts

---

## Custom Cursor

- Replace the default cursor with a **sliotar (hurling ball)** — use a small circular white element with black stitching lines drawn in CSS or inline SVG
- The sliotar cursor should have a subtle rotation animation on movement (use JS `mousemove` to track and rotate it)
- On mobile, hide the custom cursor (use media query)

---

## Sections — Build in This Order

### 1. Hero Section
- Full-viewport height
- Animated background: subtle purple particle field OR diagonal geometric pattern using CSS
- Large competition name: **"SUPER 9s"** in display font
- Tagline beneath (placeholder: *"The Ultimate Club Showdown"*)
- A glowing CTA button: *"View Events ↓"* that smooth-scrolls down
- Animated entrance (staggered fade-in/slide-up on load)

### 2. Countdown Timers — Four Events
- **4 separate countdown cards**, one per event
- Each card shows: Event name, date, and a live countdown (`DD : HH : MM : SS`)
- Use **hardcoded placeholder dates** (space them ~2 weeks apart from now) — the client will update them
- Cards laid out in a **2×2 grid** on desktop, **single column** on mobile
- Each card has a distinct accent colour on its top border (cycle through 4 shades of purple/gold)
- Countdown updates every second via `setInterval`

Placeholder event names:
- Quarter Final — Event 1
- Quarter Final — Event 2
- Semi Final
- Grand Final

### 3. Competition Information Boxes
- **One card per competition type** — minimum 4 cards
- Each card contains: Competition name, short description (2–3 sentences placeholder), key rules bullet points, and an icon
- Card layout: **masonry or responsive CSS grid** — not a boring equal-height row
- Cards lift/scale on hover with a purple glow shadow
- Icons from Font Awesome (e.g. trophy, shield, users, star)

Placeholder competitions:
- Under 14 Super 9s
- Under 16 Super 9s
- Junior Super 9s
- Senior Super 9s

### 4. Photo Gallery — Previous Years
- Responsive **CSS grid gallery** (3 cols desktop, 2 cols tablet, 1 col mobile)
- Use **placeholder images** from `https://picsum.photos` with a hurling/sport theme (use fixed seeds for consistency)
- On click, open a **lightbox modal** — pure JS, no libraries
- Lightbox: dark overlay, centred image, left/right arrow navigation, close button
- Year labels overlaid on each image (e.g. "2023", "2024")
- Images have a purple-tinted hover overlay with a zoom icon

### 5. Sponsorship Gallery
- Horizontal scrolling row of sponsor logo placeholders (use grey boxes with "Sponsor Name" text — client will replace)
- At least **6 sponsor slots**
- Auto-scrolling marquee effect (CSS `animation: scroll linear infinite`) — pause on hover
- Section header: "Our Sponsors" with a gold underline accent

### 6. Sponsorship Contact Section
- Clean contact form with fields: Name, Organisation, Email, Phone (optional), Message
- A brief pitch above the form (2–3 sentences: why sponsor this event, placeholder text)
- **Do NOT use a `<form>` tag** — use `<div>` with `onclick` handlers
- On submit: show a success message in the UI (no backend needed)
- Style the submit button with gold background, purple text, bold font

### 7. Footer
- Dark purple (`#1A0533`) background
- Competition name, nav links, social media icons (Font Awesome), copyright line
- Mobile: stacked layout

---

## Animations & Interactions

- **Page load:** Staggered fade-in for hero elements (CSS `animation-delay`)
- **Scroll reveal:** Use `IntersectionObserver` — elements slide up into view as user scrolls
- **Hover states:** Cards scale up (`transform: scale(1.03)`), glow shadow appears
- **Countdown:** Digits flip or pulse on each second tick (CSS keyframe on the number element)
- **Smooth scroll:** All internal anchor links use `scroll-behavior: smooth`
- **Active nav highlight:** JS updates active link on scroll via `IntersectionObserver`

---

## Navigation

- **Sticky top navbar** — transparent over hero, solid purple once scrolled past hero
- Links: Home · Events · Competitions · Gallery · Sponsors · Contact
- **Hamburger menu** on mobile — slides in a full-width drawer from the top
- Navbar collapses smoothly, no layout shift

---

## Mobile Optimisation Requirements

- All layouts use CSS Grid / Flexbox — zero fixed pixel widths
- Touch targets minimum 44×44px
- Hamburger nav on screens < 768px
- Custom cursor hidden on touch devices
- Gallery lightbox swipe-navigable on mobile (use `touchstart`/`touchend` events)
- Countdown grid: 2×2 → 1 column on mobile
- Font sizes scale with `clamp()` for fluid typography

---

## Code Quality Standards

- All CSS in a `<style>` block within `index.html` — no external stylesheets
- All JS in a `<script>` block at bottom of `body` — no external scripts except CDN libraries
- Use CSS custom properties for ALL colors, spacing, and font sizes
- Comment each major section clearly: `/* === SECTION: HERO === */`
- No inline styles except where dynamically set by JS
- Accessible: all images have `alt` text, form inputs have labels, nav has `aria-label`

---

## Deliverable

One complete `index.html` file. Open in a browser with no server required. All placeholder content (text, images, dates) is clearly marked with `<!-- TODO: -->` comments so the client knows what to update.

---

## Change Log

### 2026-03-24

**Content updates applied from `update-prompt.txt`:**

- Hero badge changed from "GAA Hurling Competition" → "Camogie Competition"
- Hero tagline changed from "The Ultimate Club Showdown" → "The Ultimate Schools Showdown"
- All instances of "Presented by Meekever Sports" changed to "Sponsored by Meekever Sports" (navbar, hero, contact section, footer)
- Removed the "Categories" and "Est." stat boxes from the hero stats bar entirely

**Countdown cards replaced with real event data:**
- Event 1: Saint Flannan's College — Camogie — Tuesday 21 April 2026, 10:00am
- Event 2: Loreto Navan — Ladies Gaelic Football — Thursday 23 April 2026, 10:00am
- Event 3: Gort Community College — Men's Hurling — Thursday 30 April 2026, 10:00am
- Event 4: CBS Green Tralee — Men's Gaelic Football — Friday 8 May 2026, 10:00am

**Competition category card titles updated** to match the four events above.

**Sponsors marquee:** Added "JSU Marketing" as a sponsor tile (in both real and duplicate tracks to preserve seamless loop animation).

**Footer:** Updated brand paragraph and quick-links event list to match new event names and dates.

**GitHub:** Repo created and code pushed to `https://github.com/JSU-Marketing/SuperNinesWebsite` (public). GitHub Pages can be enabled via Settings → Pages for free hosting.

### 2026-03-26

**Assets folder created** at `assets/` to store all static files.

**Super Nines logo added:**
- Logo file placed at `assets/super-nines-logo.png`
- Navbar: replaced dashed placeholder with real `<img>` tag
- Footer: replaced text-only logo link with logo image

**2025 photo gallery added:**
- 10 real photos placed at `assets/gallery/2025-1.jpg` → `2025-10.jpg` (converted from `.jfif`)
- New 2025 year card added to the gallery section (first/featured position)
- 2025 entry added to the JS `YEAR_DATA` object — all 10 photos accessible via lightbox
