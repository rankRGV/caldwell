# Handoff: Caldwell Humane & Animal Services Consultants — Homepage

## Overview
This is a high-fidelity homepage design for **Caldwell Humane & Animal Services Consultants**, a consulting firm serving animal welfare organizations. The design goal is "compassionate, warm, but authoritative" — prestige editorial aesthetic with a dark navy foundation, warm gold accents, and forest green.

The client is building this site in **Astro**. The HTML file in this folder is the design reference. Recreate it faithfully in Astro components using the token values and layout specs below.

---

## About the Design File
`Caldwell B - Impact Statement.html` is a **high-fidelity design reference** created in HTML/CSS. It is NOT production code — do not copy it directly. Your job is to recreate this design in Astro using its component model, with the exact colors, typography, spacing, and interactions documented here.

**Fidelity: High-fidelity.** Recreate pixel-precisely: colors, font sizes, spacing, hover states, and scroll animations are all intentional.

---

## Design System

### Color Tokens
These use `oklch()` for perceptual consistency. Map to CSS custom properties:

| Token | Value | Usage |
|---|---|---|
| `--navy` | `oklch(21% 0.090 253)` | Primary background, nav, hero, about, footer |
| `--navy2` | `oklch(27% 0.090 253)` | Hover states on navy cards |
| `--green` | `oklch(36% 0.115 143)` | Forest green — challenge outro, approach text, btn hover |
| `--gold` | `oklch(73% 0.130 78)` | Accent — labels, borders, stat numbers, CTA button |
| `--cream` | `oklch(97% 0.018 82)` | Primary light background, body text on dark |
| `--cream2` | `oklch(94% 0.021 80)` | Alternate section background (challenge, CTA) |
| `--cream3` | `oklch(90% 0.023 78)` | Dividers, card gaps |
| `--text` | `oklch(20% 0.060 250)` | Body text on light backgrounds |

### Typography
```
Heading font: Playfair Display (Google Fonts — weights 400, 700; italic variants)
Body font:    Nunito (Google Fonts — weights 400, 500, 600, 700; italic)
```

**Type scale:**
| Role | Font | Size | Weight | Notes |
|---|---|---|---|---|
| Hero wordmark | Playfair Display | clamp(64px, 9vw, 128px) | 400 | `line-height: 0.88`, `letter-spacing: -0.01em` |
| Section H2 | Playfair Display | clamp(28px, 3.4vw, 48px) | 400 | `line-height: 1.2` |
| Card H3 | Playfair Display | 21px | 400 | `line-height: 1.3` |
| Pull quote | Playfair Display italic | clamp(22px, 3.1vw, 44px) | 400 | |
| Body | Nunito | 16.5px / 17px | 400 | `line-height: 1.7–1.75` |
| Label caps | Nunito | 10–10.5px | 700 | `letter-spacing: 0.16em`, `text-transform: uppercase`, gold color |
| Nav links | Nunito | 13.5px | 600 | |
| Buttons | Nunito | 13–14px | 700 | `letter-spacing: 0.04em` |

**Label component pattern:** All section labels (e.g. "What We Do", "About Caldwell") use this style:
```css
font-size: 10.5px; font-weight: 700; letter-spacing: 0.16em;
text-transform: uppercase; color: var(--gold);
display: inline-flex; align-items: center; gap: 10px;
margin-bottom: 18px;
/* Trailing rule: */
::after { content: ''; display: block; width: 36px; height: 1px; background: var(--gold); }
```

### Spacing
- Section vertical padding: `96px 0`
- Container max-width: `1240px`, padding: `0 56px`
- Nav height: `68px`
- Card gap in grid: `2px` (background acts as gap color)

---

## Page Sections (top to bottom)

### 1. Nav (sticky)
- Background: `--navy`
- Sticky, `z-index: 100`
- On scroll: adds `box-shadow: 0 2px 24px oklch(0% 0 0 / 0.35)` via `.scrolled` class
- Left: wordmark — "CALDWELL" in Playfair Display 19px cream, subtitle in Nunito 9px gold caps below
- Center-right: nav links (cream/72% opacity → gold on hover)
- Far right: "Book a Consultation →" button — gold outline, fills gold on hover (text turns navy)

### 2. Hero (full-viewport)
- **Layout:** CSS grid, `52fr 48fr`, min-height `calc(100vh - 68px)`, background `--navy`
- **Left column** (text):
  - Padding: `72px 48px 72px 80px`
  - Eyebrow: gold caps label (no trailing rule here)
  - "CALDWELL" at max 128px Playfair Display, cream, `line-height: 0.88`
  - Subtitle caps in gold below
  - 48px wide, 2px gold horizontal rule
  - Italic Playfair tagline: *"Stronger organizations. / Safer communities. / More lives saved."* — clamp 20–33px, cream 90% opacity
  - Body sub-text: 16px, cream 68% opacity, max-width 480px
  - Two CTAs: gold-fill button + ghost text link (cream → gold on hover)
- **Right column** (image):
  - Full-bleed hero image: `https://caldwell.rankrgv.com/images/hero.jpg`
  - `object-fit: cover`, `object-position: center 15%`
  - **Left-edge fade:** `::before` pseudo-element, `position: absolute`, width 120px, gradient `--navy → transparent` (left to right), `z-index: 1` — creates seamless blend from text col into photo
  - Background fallback: `--navy2`
  - In Astro: replace with your own hosted image asset

### 3. Ticker bar
- Background: `--navy`, `border-top: 1px solid cream/8%`
- Infinite horizontal marquee, 35s, `animation: ticker-go`
- Content: "Mission Focused ◆ People Centered ◆ Operations Excellence ◆ Meaningful Impact" (repeated ×2 for seamless loop)
- Text: 11px, Nunito 700, gold, `letter-spacing: 0.14em`
- `aria-hidden="true"` — decorative only

### 4. Impact Strip
- Background: `--cream`, `border-bottom: 1px solid --cream3`
- 3-column grid, full-width (no container constraint — `max-width: 1440px`)
- Each item: `padding: 52px 56px`, `text-align: center`, `border-right: 1px solid --cream3`
- Stat number: Playfair Display 64px, navy, bold
- Label: 10px Nunito caps, green, `margin-top: 10px`
- Description: 13.5px, text color 62% opacity

**Current sample data (replace with real figures):**
| Stat | Value | Label | Description |
|---|---|---|---|
| 1 | 20+ | Years of Experience | Executive leadership in animal welfare & municipal government |
| 2 | 30+ | Organizations Supported | Shelters, humane societies, and animal welfare agencies |
| 3 | $1M+ | Grant Dollars Secured | Funding that sustains the mission long-term |

### 5. The Challenge
- Background: `--cream2`
- Section label + H2: *"Animal welfare organizations face increasing operational challenges."*
- Intro paragraph (opacity 0.75)
- **4 challenge strips** — CSS grid `72px 260px 1fr`, gap 28px, each with:
  - Gold Playfair number (38px, bold)
  - Playfair title (21px, navy)
  - Body description
  - `border-top: 1px solid --cream3`; last item also `border-bottom`
- Closing italic blockquote in green with gold left border (3px)

### 6. Services
- Background: `--cream`
- Section label + H2 + intro paragraph
- **6-card grid:** `repeat(3, 1fr)`, gap `2px`, background `--cream3` (acts as gap)
- Each card:
  - Background: `--navy`
  - `border-bottom: 3px solid --gold`
  - Padding: `38px 30px`
  - H3: Playfair 21px, gold
  - Body: 14.5px, cream 76% opacity
  - Hover: background `--navy2`

**Services (in order):**
1. **Leadership Development** — Building confident, accountable leaders and boards...
2. **Operational Excellence** — Tightening the day-to-day systems — intake, staffing, workflows...
3. **Strategy & Solutions** — Clear-eyed planning grounded in your reality...
4. **Compassion & Community** — Programs and partnerships that deepen community trust...
5. **Impact & Sustainability** — Turning good intentions into measurable outcomes...
6. **Grant & Funding Development** — Finding the right funding, telling the story that wins it...

### 7. Pull Quote (full-width)
- Background: `--navy`, padding `100px 0`, `text-align: center`
- Giant decorative `"` via `::before` — Playfair, 5em, gold, opacity 0.2
- Quote text: Playfair italic, clamp 22–44px, cream, max-width 880px
- **Quote:** *"People may forget specific decisions. They rarely forget how leaders made them feel."*

### 8. Approach
- **Layout:** CSS grid, `1fr 1fr`, min-height 580px, background `--cream`
- **Left (text):**
  - Padding: `80px 72px`
  - Label, H2: *"Strong organizations are not built by accident."*
  - Bullet list (3 items) — green `8×2px` dash marker, `position: absolute, left: 0, top: 11px`
  - Blockquote: Playfair italic, green, gold left border 2px
- **Right (image):**
  - `https://caldwell.rankrgv.com/images/approach-real.jpg`
  - `object-fit: cover`, full-height fill
  - Replace with your own hosted asset

### 9. About
- Background: `--navy`, padding `96px 0`
- **Grid:** `1.1fr 0.9fr`, gap 72px
- **Left (copy):**
  - Label, H2: *"Leadership built from the ground up — and proven in the field."*
  - 3 paragraphs of bio copy (see HTML source for exact text)
  - Gold underline CTA link
- **Right (founder card):**
  - Outer: `background: cream/5%`, `border: 1px solid cream/12%`
  - Image: `aspect-ratio: 4/5`, `object-fit: cover`, `object-position: center 12%`
  - **Headshot URL (replace with hosted asset):** `https://s.yimg.com/lo/mysterio/api/...` (Yahoo CDN — temporary, not reliable for production)
  - Info block: `padding: 22px 26px 26px`
  - Name: Playfair 21px, cream — **fill in: `[Founder Name]`**
  - Title: Nunito 11px gold caps — "Founder & Principal Consultant"
  - Credentials: 13px, cream 45% opacity
- **Stats strip** (below grid, `margin-top: 72px`, `border-top: 1px solid cream/12%`):
  - 3-column, same sample data as impact strip
  - Stat number: Playfair 56px, cream
  - Label: 10px gold caps
  - Description: 13px, cream 50% opacity

### 10. CTA Section
- Background: `--cream2`
- Centered layout
- H2: Playfair, clamp 26–50px, navy — *"Ready to build a stronger organization?"*
- Body: 17px, opacity 0.72, max-width 520px
- Two buttons: navy-fill (→ green on hover) + navy outline (→ full border on hover)
- Email CTA: `mailto:hello@caldwellhumaneconsultants.com`

### 11. Footer
- Background: `--navy`
- 3-column grid: `2fr 1fr 1fr` — Brand / Explore / Connect
- Brand: wordmark + tagline
- Explore: anchor links to all page sections
- Connect: Email, LinkedIn, Consultation booking
- Bottom bar: copyright line, cream 35% opacity

---

## Interactions & Animations

### Scroll-in animations
All `.anim` elements animate in when entering the viewport:
```css
/* Base state */
.anim { opacity: 0; transform: translateY(18px); transition: opacity 0.65s ease, transform 0.65s ease; }
/* Triggered state */
.anim.in { opacity: 1; transform: none; }
/* Stagger delays */
.anim.d1 { transition-delay: 0.1s; }
.anim.d2 { transition-delay: 0.2s; }
.anim.d3 { transition-delay: 0.3s; }
```
Triggered via `IntersectionObserver` — add class `in` when element enters viewport at 8% threshold. Elements already in view on load get `in` immediately.

Wrap in `@media (prefers-reduced-motion: no-preference)` — always show content without animation for users who prefer reduced motion.

In Astro, implement with a client-side script in a layout or via a small Alpine.js / vanilla JS island.

### Nav scroll shadow
```js
window.addEventListener('scroll', () => {
  nav.classList.toggle('scrolled', window.scrollY > 10);
}, { passive: true });
```

### Services card hover
`background` transitions from `--navy` → `--navy2` on hover, `transition: background 0.25s`.

### Ticker marquee
```css
@keyframes ticker-go { from { transform: translateX(0); } to { transform: translateX(-50%); } }
```
Inner `.ticker-track` contains content repeated ×2 side-by-side. Animation duration: 35s linear infinite.

---

## Assets to Replace
| Location | Current (temp) | Replace with |
|---|---|---|
| Hero image | `https://caldwell.rankrgv.com/images/hero.jpg` | `src/assets/hero.jpg` (or equivalent) |
| Approach image | `https://caldwell.rankrgv.com/images/approach-real.jpg` | `src/assets/approach.jpg` |
| Founder headshot | Yahoo CDN URL | `src/assets/founder-headshot.jpg` (professional portrait) |

**Hero image guidance:** The hero image should be animals (dog + cat preferred). Warm, editorial feel. The left-edge fade gradient blends it into the navy text column — this only works well if the left 15% of the image is not critically important.

---

## Content to Fill In
- `[Founder Name]` — full name in the About section founder card
- Stats (20+, 30+, $1M+) are sample data — confirm or update with real figures
- Email address: confirm `hello@caldwellhumaneconsultants.com`
- LinkedIn URL: add real URL to footer LinkedIn link

---

## Suggested Astro Component Structure
```
src/
  components/
    Nav.astro
    Hero.astro
    Ticker.astro
    ImpactStrip.astro
    Challenge.astro
    Services.astro
    PullQuote.astro
    Approach.astro
    About.astro
    CtaSection.astro
    Footer.astro
  layouts/
    BaseLayout.astro   ← Google Fonts import, CSS custom properties, global reset
  pages/
    index.astro        ← assembles all components
  assets/
    hero.jpg
    approach.jpg
    founder-headshot.jpg
  styles/
    global.css         ← CSS custom properties, reset, .anim, .label, .container
```

---

## Files in This Package
| File | Description |
|---|---|
| `Caldwell B - Impact Statement.html` | High-fidelity design reference. Open in a browser to see the intended output. |
| `README.md` | This document — full implementation spec. |
