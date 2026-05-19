# Feuji AI Rulebook — Claude

This is the persistent design rulebook for the Feuji website project. Every page, every section, every animation must follow these rules exactly. Do not guess, invent, or improvise on anything covered here.

---

## Project Structure

```
/
├── Feuji_Home.html          — Homepage
├── GCC-as-a-Service.html    — GCC page (S1 template reference)
├── QE-as-a-Service.html     — Quality Engineering page (S1 template)
├── Sustainability.html      — Sustainability page (community template)
├── Assets/
│   ├── images/              — All images
│   │   ├── feuji-orange-logo.png
│   │   ├── services-gcc-BOT-model/   — Build.jpg, operate.jpg, transfer.jpg
│   │   ├── home-services-v002/       — Cloud-Solutions.png, Data-and-Insights.png, Digital-Engineering.png
│   │   ├── manohar-reddy.avif
│   │   └── Firefly_Gemini-Flash-mountain.png  — footer reveal image
│   └── gif/
│       └── Feuji banner video 1.mp4  — GCC banner looping video
```

**Live URL:** `https://tanyagijywork.github.io/Feuji-Website/`

---

## Templates

### S1 — Feuji Services Template
The master template for all service pages. **GCC-as-a-Service.html is the reference file.** QE-as-a-Service.html is the second page built on S1.

When asked to build a page "in S1", replicate every structural, spacing, animation, and style decision from GCC exactly — only the content changes.

**S1 section order:**
1. Navigation
2. Page Banner (light, neutral-50 bg)
3. Intro (two-column sticky)
4. Tab section (BOT-style, neutral-50 bg)
5. Capabilities carousel (auto-scroll, white bg)
6. Impact numbers (neutral-50 bg)
7. Case studies (dark ink bg)
8. Insights (cascade, white bg)
9. Connect CTA (dark ink bg)
10. Footer
11. Footer reveal

---

## Design Tokens

All tokens are CSS custom properties. Never hardcode hex values — always use tokens.

### Fonts
```css
--f-display: 'Cormorant Garamond', Georgia, serif;
--f-ui:      'DM Sans', system-ui, sans-serif;
```

### Neutral Palette
```css
--neutral-50:  #F9F9F9;
--neutral-100: #EAEAEA;
--neutral-200: #DFDFDF;
--neutral-300: #C1C1C1;
--neutral-400: #A2A2A2;
--neutral-500: #848484;
--neutral-700: #474747;
--neutral-800: #292929;
--ink:         #0A0A0A;
--ink-90:      #1A1A1A;
--ink-70:      #333333;
--mid:         #656565;
--muted:       #848484;
--white:       #FFFFFF;
```

### Brand — Orange
```css
--orange:       #F3752C;
--orange-light: #FEF3EC;
--orange-dark:  #DA6A29;
```

### Brand — Green (full scale)
```css
--green-100: #A4EBDB;
--green-200: #5DDCC2;
--green-300: #00CEA9;
--green-400: #00BE91;
--green-500: #00B784;
--green-600: #00A577;
--green-700: #00805D;
--green-800: #005C43;
--green-900: #003727;   ← dark banner background (Sustainability)
```

### Brand — Yellow
```css
--yellow-50:  #FFFBEA;
--yellow-100: #FEF3B0;
--yellow-200: #FDE47A;
--yellow-700: #92650A;
--yellow-800: #6B4A08;
```

### Semantic Aliases
```css
--border:    var(--neutral-200);
--border-dk: var(--neutral-800);
--surface:   var(--neutral-50);
```

### Layout
```css
--nav-h:   80px;
--max-w:   1280px;
--pad-x:   80px;   /* 20px on mobile */
--sec-py:  80px;   /* 60px on mobile */
--gap:     32px;
```

### Easing
```css
--ease:     cubic-bezier(0.25,0.1,0.25,1);
--ease-out: cubic-bezier(0,0,0.2,1);
```

---

## Typography Scale

Never deviate from these. Apply via class. Do not recreate inline.

| Class | Font | Size | Weight | Line-height | Letter-spacing |
|---|---|---|---|---|---|
| `.t-display-m` | Display | 72px | 500 | 72px | -3px |
| `.t-h2` | Display | 64px | 500 | 64px | -3px |
| `.t-h3` | Display | 40px | 500 | 40px | -2px |
| `.t-h4` | UI | 32px | 500 | 35px | -1px |
| `.t-h5` | UI | 24px | 500 | 29px | -1px |
| `.t-body-xl` | UI | 20px | 400 | 28px | -1px |
| `.t-body-l` | UI | 18px | 400 | 25px | -1px |
| `.t-body-m` | UI | 16px | 400 | 24px | 0 |
| `.t-body-s` | UI | 14px | 400 | 21px | 0 |
| `.t-label-s` | UI | 12px | 600 | 13px | 1px uppercase |
| `.t-label-m` | UI | 14px | 600 | 15px | 1px uppercase |
| `.t-btn` | UI | 16px | 400 | 18px | 0 |
| `.t-nav` | UI | 18px | 400 | 20px | -1px |
| `.t-legal` | UI | 14px | 400 | 20px | 0 |

**Page banner H1:** 80px / 500 / 80px lh / -4px tracking (Cormorant Garamond)
**Mobile H1:** 48px / 50px lh / -2px

Use `<em>` for italic weight-400 variants within display headings.

---

## Button System

Always use the full `.btn` base class plus a modifier. Never create custom button styles.

| Class | Appearance | Usage |
|---|---|---|
| `.btn--primary` | Black fill, white text | Primary action on light bg |
| `.btn--primary-inv` | White fill, ink text → black on hover | Primary on dark bg |
| `.btn--primary-orange` | Orange fill → ink on hover | Nav CTA only |
| `.btn--secondary` | Transparent, ink border → orange on hover | Secondary on light bg |
| `.btn--secondary-inv` | Transparent, white border → orange on hover | Secondary on dark bg |
| `.btn--tertiary-inv` | No border/bg, white text + arrow | Text link on dark bg |
| Tertiary (light) | No border/bg, ink text + arrow | Text link on light bg — used in tab bodies |

All buttons use `.btn-arrow` span for the `→` arrow (animates on hover).

```html
<a href="#" class="btn btn--primary t-btn">
  Label <span class="btn-arrow">→</span>
</a>
```

---

## Navigation

### Light Nav (service pages — S1)
- Starts as `nav--light` (ink logo, ink links)
- Becomes `is-scrolled` (frosted glass) after banner scrolls past

### Dark Nav (Sustainability — green-900 banner)
- Starts as `nav--dark` (white logo via `filter: brightness(0) invert(1)`, white links)
- Becomes `nav--light is-scrolled` after banner scrolls past

### Nav CTA
Always: `btn btn--primary-orange t-btn` — "Let's connect →"
On dark nav: automatically renders white fill via `.nav--dark .btn--primary-orange`.

### Active link
Add `is-active` class to the relevant `nav__link`.
- Service pages → Services is active
- Sustainability → Community is active

---

## Animations

### 1. Quill-Scroll (character typewriter on scroll)
Applied via JS to: all `h2` elements on every page.
- Characters split into `.tw-char` spans at `opacity: 0`
- Scroll drives reveal zone: bottom of viewport → 38% from top
- **Do not manually apply** — JS `setupScrollTypewriter` picks up all `h2` automatically

### 2. Hero Typewriter (timed on load)
Applied to: `.page-banner__heading` (H1) on every page.
- Characters reveal at 80ms intervals, 500ms after page load

### 3. Reveal (scroll fade-up)
```css
.reveal             — opacity 0, translateY 28px → visible on IntersectionObserver
.reveal-d1          — 0.08s delay
.reveal-d2          — 0.16s delay
.reveal-d3          — 0.24s delay
```
Apply to: section headers, body blocks, cards, grid containers.

### 4. Word-Reveal (scroll-driven opacity)
Used on: Sustainability intro paragraph.
- Words split into `.sus-intro__word` spans at `opacity: 0.15`
- Scroll position drives individual word opacity to 1

### 5. Impact Stat Fade-Up
Class: `.impact-stat--animate` — triggers on IntersectionObserver, staggered per child.

### 6. Tab Progress Bar
Active tab `::after` pseudo-element animates width 0→100% over the tab duration.
- S1 pages: `var(--orange-dark)` — matches GCC
- Sustainability: `var(--orange-dark)` — same rule

---

## Section Patterns

### Page Banner
- **S1 (service pages):** `background: var(--neutral-50)` — light
- **Sustainability:** `background: var(--green-900)` — dark, uses `page-banner--dark` modifier
- Two-column grid (1fr 1fr), 80px gap, image/video right
- Min-height: 70vh
- Padding: `calc(var(--nav-h) + 48px)` top, 80px bottom

### Breadcrumb
- Light page: standard `.breadcrumb`
- Dark page: `.breadcrumb--inv` (translucent white border, white text)

### Intro Section
- White background
- Two-column grid (1fr 1fr, 80px gap)
- Left: H2 heading, `position: sticky` (stays visible while body scrolls)
- Right: body copy `.t-body-l`, `color: var(--mid)`, `.reveal`

### Tab Section (BOT / Sub-services)
- Background: `var(--neutral-50)`
- Two-column grid (1fr 1fr, 32px gap)
- Left: image panel with crossfading images
- Right: stacked tab cards with top border
- Progress bar: `var(--orange-dark)`
- Active title: ink. Inactive: muted
- Auto-advances every 4s (S1) / 5s (Sustainability initiatives)
- Pause on hover
- Tab body CTA: tertiary style (no pill, ink text, arrow slides right)

### Capabilities Carousel
- White background
- Auto-scrolling belt (28s loop, pauses on hover)
- Cards: `var(--yellow-50)` bg, `var(--yellow-100)` border → `var(--yellow-200)` on hover
- Card size: 300px wide, min 220px tall, 12px border-radius
- Odd cards: margin-top 0. Even cards: margin-top 48px (stagger)
- Edge fade: mask-image gradient left and right
- **Duplicate card set** for seamless loop

### Impact Numbers
- Background: `var(--neutral-50)`
- Border-top: `var(--green-500)` — green accent line, not orange
- Hover: green-500 glow radial gradient + value turns `var(--green-700)`
- Value: Cormorant Garamond, 80px (S1) or 72px (QE with 4 stats)
- S1 (3 stats): `repeat(3, 1fr)` grid
- QE (4 stats): `repeat(4, 1fr)` grid

### Case Studies
- Background: `var(--ink)`
- Cards: dark with orange rising-sun glow on hover, gradient border
- CTA inside card: `btn--tertiary-inv` — "Discover now →"
- S1 standard: 2 cards, `grid-template-columns: 1fr 1fr`

### Insights
- Background: `var(--white)`
- 3-column cascade: cells have `padding-top: 0 / 80px / 160px`
- Card images: `aspect-ratio: 3/2`, 12px border-radius
- Tags: orange text, white pill
- Link: "Read more →" — ink text, gap widens on hover
- Header: H2 left, secondary CTA right — "View all insights →"

### Connect CTA
- Background: `var(--ink)`
- Center-aligned: flex-direction column, align-items center, text-align center
- Eyebrow: "Get in touch" (label-m, neutral-400)
- H2: Cormorant Garamond, 64px, white, -3px tracking
- CTA: `btn--secondary` with white border override

### Footer
- Background: `var(--ink)`
- 6-column grid, border-top `var(--neutral-800)`
- Column titles: white, label-s uppercase, non-interactive on desktop
- Links: `var(--neutral-500)` → white on hover
- Mobile: accordion with chevron

### Footer Reveal
- `position: sticky; bottom: 0; z-index: 0` — sits behind `.page-content`
- `.page-content` has `z-index: 1; box-shadow: 0 24px 80px 20px rgba(0,0,0,0.85)` to cast shadow above it
- Image: `object-position: center 60%`
- Bottom gradient: `height: 30%`, transparent → `rgba(0,0,0,0.55)`
- Legal bar pinned to bottom: copyright left, policy links right
- Image used: `Assets/images/Firefly_Gemini-Flash-mountain.png`

---

## Page-Specific Rules

### GCC-as-a-Service.html
- Nav: light, no dark phase
- Banner: neutral-50, looping video (`Feuji banner video 1.mp4`), `mix-blend-mode: multiply`, `scale(1.05)`, `aspect-ratio: 4/3`
- Tab section: BOT model (3 tabs: Build, Operate, Transfer)
- Impact: 3 stats

### QE-as-a-Service.html
- Nav: light, no dark phase
- Banner: neutral-50, no image yet
- Tab section: Sub-services (4 tabs)
- Impact: 4 stats, `repeat(4, 1fr)` grid, value font-size 72px
- Case studies: 2 cards

### Sustainability.html
- Nav: **starts dark** (white logo/links) over green-900 banner, transitions to light after scroll
- Banner: `var(--green-900)` dark, `page-banner--dark` modifier, white H1, 65% white sub
- Breadcrumb: `.breadcrumb--inv`
- Intro: word-by-word scroll-driven opacity reveal (not standard reveal)
- Tab section: Our Initiatives (4 tabs), images from `services-gcc-BOT-model`
- CEO quote section: `var(--green-900)` bg, 40px italic Cormorant Garamond, quill-scroll typewriter, green-500 `"` mark, avatar 70px circle
- No impact numbers section
- No capabilities carousel

---

## What Must Never Change

These are core S1 decisions. Do not alter without explicit instruction:

- **Token names** — never rename or add new tokens outside the established palette
- **Font families** — Cormorant Garamond + DM Sans only
- **Button shapes** — 999px border-radius pill only
- **Orange accent** — `#F3752C` for primary orange, `#DA6A29` for dark orange (tab bar, accordion open state)
- **Tab progress bar colour** — always `var(--orange-dark)` on S1 pages
- **Impact stat border** — always `var(--green-500)`, never orange
- **Footer reveal shadow** — `0 24px 80px 20px rgba(0,0,0,0.85)` on `.page-content`
- **Nav height** — 80px
- **Max content width** — 1280px
- **Horizontal padding** — 80px desktop, 20px mobile

---

## Commit Convention

Always commit with descriptive message + co-author line:

```
Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>
```

---

## How to Use This Rulebook

- **"Build X page in S1"** → Follow GCC-as-a-Service.html exactly, section by section, only swapping content
- **"Build X page in Sustainability style"** → Follow Sustainability.html, keep green-900 dark banner, word-reveal, initiatives tabs
- **"Add a new section"** → Match the background alternation pattern (white → neutral-50 → white → neutral-50), use existing CSS classes
- **"Change a colour"** → Only via token; never hardcode hex
- **"Add an animation"** → Use one of the 6 defined animation patterns above; do not invent new ones
- **"Add a button"** → Pick from the 7 defined button variants; no custom styles
