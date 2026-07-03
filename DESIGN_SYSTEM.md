# LeadSpark Design System

> Extracted from Webflow project and refined through build corrections.
> This document is structured for both human readability and LLM consumption.
> When building pages, reference these tokens by their CSS variable names.

---

## 1. Colors

| Token Name | CSS Variable | Value | Usage |
|---|---|---|---|
| Off-White BG | `--off-white-bg` | `#d9d2ca` | Page background |
| White Card | `--white-card` | `#e5ded7` | Card/bento surfaces |
| Transparent | `--transparent` | `hsla(0, 0%, 100%, 0)` | Transparent overlays |
| Brand Green | `--brand-green` | `#40775f` | Primary brand color |
| Brand Ember | `--brand-ember` | `#d8602f` | Accent / CTA color |
| Forest Green | `--forest-green` | `#273730` | Dark text / dark sections |
| Pale Ember | `--pale-ember` | `#e8a075` | Soft accent / hover states |
| Light Green | `--light-green` | `#a9d8c0` | Secondary green / highlights |
| Muted Text | `--muted-text` | `#6b6862` | Secondary / caption text |
| Forest Green Trans | `--forest-green-trans` | `hsla(153.75, 17%, 18.4%, 0.5)` | Semi-transparent dark overlay |
| White | `--color` | `white` | Pure white text/elements |

### Color Palette Summary
- **Warm neutral base**: Off-white/beige tones (`#d9d2ca`, `#e5ded7`)
- **Primary**: Deep forest green (`#273730`) + mid green (`#40775f`)
- **Accent**: Ember/burnt orange (`#d8602f`) with pale variant (`#e8a075`)
- **Supporting**: Light green (`#a9d8c0`), muted text (`#6b6862`)

---

## 2. Typography

### Font Families
| Role | CSS Variable | Font |
|---|---|---|
| Headings | `--_fonts---headings` | **Bricolage Grotesque** |
| Paragraphs | `--_fonts---paragraphs` | **DM Mono** |

### Heading Types (4 only — do not invent others)

| Class | Usage | SEO Role |
|---|---|---|
| `.hero-heading` | Hero section + large CTA sections only | NOT an H1 — conversion focused |
| `.section-heading` | Most sections — conversion + SEO | Can be H2/H3 |
| `.secondary-heading` | Keyword-heavy, pairs with section/hero headings, some cards (e.g. stats) | **First instance on each page = H1** |
| `.card-heading` | Smaller bentos, important cards | Semantic as appropriate |

**Rules:**
- H1/H2/H3 HTML tags are for crawlers only — applied independently of visual heading class
- The first `.secondary-heading` on every page is the H1
- `.hero-heading` is NOT an H1 — never make it one
- Do not make up additional heading types

### Font Sizes (Responsive)

| Token | CSS Variable | Desktop | Large Laptop | Small Desktop | Large Desktop | iPad | Phone |
|---|---|---|---|---|---|---|---|
| Hero Heading | `--_font-sizes---hero-heading--size` | 60px | 60px | 60px | 60px | 6vw | 8vw |
| Section Heading | `--_font-sizes---section-heading--size` | 32px | 32px | 32px | 32px | 3.6vw | 6vw |
| Sub Heading | `--_font-sizes---sub-heading--size` | 20px | 20px | 20px | 20px | 2vw | 3.2vw |
| Paragraph | `--_font-sizes---paragraph--size` | 18px | 18px | 18px | 18px | 2vw | 2.8vw |

### Line Heights

| Token | CSS Variable | Default | Small Desktop |
|---|---|---|---|
| Hero Heading | `--_font-sizes---hero-heading--height` | 120% | 120% |
| Sub Heading | `--_font-sizes---sub-heading--height` | 120% | 120% |
| Section Heading | `--_font-sizes---section-heading--percentage` | 110% | 140% |

### Typography Rules
- **Desktop**: fixed `px` values
- **iPad + Phone**: `vw` units for fluid scaling — use `clamp()` to prevent extremes
- **IMPORTANT**: Ignore the Phone mode text sizes in the font-size variable collection — use `vw` with `clamp()` in code instead. Phone mode in all other variable collections should NOT be ignored.
- Never use inline `font-size` overrides on `.paragraph` elements — always inherit `var(--font-paragraph)`

---

## 3. Spacing (Padding + Gaps)

### Section & Container Spacing

| Token | CSS Variable | Desktop | Small Desktop | iPad | Phone | Mobile Phone |
|---|---|---|---|---|---|---|
| Section Side Padding | `--_padding-gaps---section-containers--section-side-padding` | 48px | 64px | 16px | 16px | 8px |
| Section Top/Bottom Padding | `--_padding-gaps---section-containers--top-bottom-padding` | 4px | 4px | 4px | 4px | 4px |

### Bento Card Spacing

| Token | CSS Variable | Desktop | Small Desktop | iPad | Phone | Mobile Phone |
|---|---|---|---|---|---|---|
| Large Bento Padding | `--_padding-gaps---inner-bento-padding-gaps--large-bento-padding` | 32px | 48px | 24px | 24px | 12px |
| Small Bento Padding | `--_padding-gaps---inner-bento-padding-gaps--small-bento-padding` | 16px | 24px | 16px | 16px | 8px |
| Bento Inner Gap | `--_padding-gaps---inner-bento-padding-gaps--size` | 16px | 16px | 16px | 16px | 16px |
| Min Bottom Pad | `--_padding-gaps---inner-bento-padding-gaps--minimum-bottom-pad` | 64px | 64px | 48px | 48px | 32px |

### Grid Spacing

| Token | CSS Variable | Desktop | Small Desktop | iPad | Phone | Mobile Phone |
|---|---|---|---|---|---|---|
| Grid Gap | `--_padding-gaps---gaps-padding-grid--grid-gap` | 8px | 8px | 6px | 6px | 4px |

### Text Spacing

| Token | CSS Variable | Desktop | Small Desktop | iPad | Phone | Mobile Phone |
|---|---|---|---|---|---|---|
| H + Para Gap | `--_padding-gaps---text-padding-gaps--h-para-gap` | 16px | 24px | 8px | 8px | 8px |
| Text Wrap Padding | `--_padding-gaps---text-padding-gaps--text-wrap-padding` | 8px | 8px | 6px | 6px | 4px |
| Paragraph Top Margin | `--_padding-gaps---text-padding-gaps--paragraph-top-margin` | 16px | 16px | 16px | 12px | 12px |
| Button Holder Margin | `--_padding-gaps---gaps-text--cta--button-holder-margin` | 48px | 48px | 32px | 32px | 24px |

### Divider

| Token | CSS Variable | Desktop | Small Desktop | iPad | Phone | Mobile Phone |
|---|---|---|---|---|---|---|
| Divider Height | `--_padding-gaps---divider-height--divider` | 100px | 100px | 64px | 56px | 56px |

- Sections are separated by `margin-bottom: var(--divider-height)` — **do not use divider div elements**

---

## 4. Corner Radius

| Token | CSS Variable | Desktop | iPad | Phone |
|---|---|---|---|---|
| Outside Corner | `--_corner-radiuses---outside-corner` | 8px | 6px | 4px |

---

## 5. Max Dimensions

| Token | CSS Variable | Desktop | Mobile |
|---|---|---|---|
| Max Section Width | `--_max-dimensions---max-section-width` | 1600px | 1600px |
| Max Section Height | `--_max-dimensions---max-section-height` | 100vh | 100vh |
| Min Text Bento Height | `--_max-dimensions---bento--minumum-text-bento-height` | 300px | 100px |
| Min Hero Bento Height | `--_max-dimensions---bento--minimum-hero-bento-height` | 600px | 400px |
| Boxy Paragraph Max Width | `--_max-dimensions---text--boxy-paragraph` | 500px | 380px |

---

## 6. Breakpoint Modes (Webflow Variable Modes)

### Font Sizes Modes
| Mode | Target |
|---|---|
| Default | Standard laptop (~1024-1279px) |
| Large Laptop | ~1280-1439px |
| Small Desktop | ~1440-1599px |
| Large Desktop | 1600px+ |
| iPad | Tablet (~768-1023px) |
| Phone | Mobile (~320-767px) — **use vw + clamp in code, ignore phone px values** |

### Padding+Gaps Modes
| Mode | Target |
|---|---|
| Default | Standard laptop |
| Desktop Small | Larger desktops |
| iPad | Tablet |
| Phone | Phone landscape |
| Mobile Phone | Phone portrait |

### Corner Radius Modes
| Mode | Target |
|---|---|
| Default | Desktop |
| iPad | Tablet |
| Phone | Mobile |

### Max Dimensions Modes
| Mode | Target |
|---|---|
| Default | Desktop |
| Mobile | All mobile |

---

## 7. Layout Patterns

### Main Grid System

- Parent grids are called `main-grid`
- Always `width: 100%`, `height: auto` — full width of parent, height determined by content
- Always use `grid-template-columns/rows: repeat(N, minmax(0, 1fr))` — ensures equal cells sized by the largest/hug bento
- **Column layout**: 12 columns desktop → 8 columns iPad → 6 columns mobile
- **Row layout**: 2 rows desktop → 6 rows iPad → 6 rows mobile (rows are determined by content/hug bento)
- Grid gap: 8px desktop → 4px mobile

#### Combo Classes: `locked` vs `unlocked`
- `main-grid|locked` — all rows are equal height, driven by one hug bento; all other bentos fill. Use when row height consistency matters.
- `main-grid|unlocked` — 2 or more hug bentos; rows flex to their own content. Use when multiple bentos need to drive their own row height (e.g. section 2: text bento is hug, card bento is hug, rest fill to card bento height).

### Bento Types

There are two types of bentos:

**`hug-bento`**
- Height: `auto` (hugs content)
- Width: fills column span
- Controls the cell height of the overall grid row
- Usually the most content-heavy bento in the grid
- Only one hug bento per locked grid (in unlocked grids there may be more)
- The designer specifies which bento is hug — do not decide independently

**`fill-bento`**
- Height: `100%` (fills its grid cell)
- Width: `100%` (fills its column span)
- All content within must fit inside it — content does not expand the cell
- Bentos have **no padding** — padding lives in the content wraps inside them

### Content Wraps

- Content wraps live inside bentos and carry all padding
- One parent content wrap per bento
- Main reusable wraps: `fill-bento-wrap-large`, `fill-bento-wrap-small`, `hug-bento-wrap`
- `fill-bento-wrap-small` — used in most smaller fill bentos; child elements are also fill
- `stretch-wrap` — flex column, `height: 100%`, `justify-content: space-between` on desktop; `height: auto` on mobile so hug-bento can hug
- Content wrap padding values come from variables — large bento padding for large bentos, small bento padding for small ones

### Section Structure

- **Hero sections** (`hero-section`): `max-height: 80vh` on all breakpoints, no max-height on mobile
- **All other sections** (`universal-section`): `max-height: 100vh` on desktop, no max-height on mobile
- Max width: 1600px, centered
- Side padding: 48–64px desktop → 16px tablet → 8px mobile portrait
- Top/bottom padding: 4px on all breakpoints
- Sections separated by `margin-bottom: var(--divider-height)` — no divider divs

### Text Wrap System

- Every piece of text sits inside a `.text-wrap`
- `.text-wrap` padding: 8px desktop → 4px mobile (all sides)
- `.text-wrap` gap: 16px desktop → 8px mobile
- **Associated text** (e.g. heading + sub-heading intentionally close together) shares **one** `.text-wrap`
- **Separate/distinct text** (e.g. a standalone paragraph) gets its **own** `.text-wrap`
- Do NOT wrap every individual element — group by visual intent
- **UX rule**: section header/text always comes first in layout/source order, regardless of visual position

### Paragraph Rules

- All `.paragraph` elements: `margin-top: var(--paragraph-top-margin)` — 16px desktop → 8px mobile
- Exception: first child inside a `.text-wrap` has no top margin (gap handles spacing)
- `.paragraph.block` — max-width **50% of parent element**
- Full-width (12-col spanning) bento paragraphs: max-width 65% desktop, 100% mobile
- Never use inline `font-size` on paragraphs — always inherit the variable

### Image Rules

- All images **except** the LEADSPARK vertical logo: `max-width: 70%`, `max-height: 70%` of parent, centered
- **Eye image** specifically: `height: 70%` of parent, `width: auto` — must never be stretched or warped
- **LEADSPARK vertical logo**: fills container width, `opacity: 0.2`, `position: absolute` on inner container to prevent inflating grid row heights

### LEADSPARK Bento

- Inner container uses `position: absolute` (top/left/width/height 100%) to remove image from document flow
- Top padding = `calc(var(--large-bento-padding) + var(--text-wrap-padding))` — aligns L with hero text
- Side padding: 8px desktop → 4px mobile
- Bottom padding: 32px desktop → 12px mobile

### Buttons

- Scale all button properties proportionally on mobile — height, border-radius, arrow circle size, gap, and font-size together
- Do not adjust font-size alone without adjusting the other properties

### Flip Cards

- Class: `flip-card-{}`
- Flip animation on hover, flip back on hover-off
- Use natural easing
- Default state and flipped state defined in Figma design system page

### Nav

- Nav follows the same bento grid as the rest of the site
- Logo sits in its own 1-column bento
- Nav links: `position: absolute`, centered horizontally in the nav links bento
- CTA button right-aligned in nav links bento
- Hamburger menu replaces nav links on tablet (≤991px) and below

### Spark

- 8 spokes at 45° intervals, 1px ember-coloured lines
- Max width/height: 200px
- Centre circle: pale ember, semi-transparent, glows on scroll
- Whole spark rotates: slow idle spin + accelerates proportional to scroll speed

---

## 8. Design Principles

1. **Warm & Organic** — Beige/cream backgrounds with green + ember accents. Not sterile white.
2. **Technical Craft** — DM Mono body text signals technical competence. Bricolage Grotesque headings add personality.
3. **Bento Layout** — Grid-based card system is the primary compositional tool. Cards hug content or expand to fill.
4. **Responsive via Variables** — Systematic scaling through variable modes, not ad-hoc media query overrides.
5. **Tight Grid Gaps** — 8px/6px/4px gaps give a dense, editorial feel.
6. **Progressive Reduction** — Every token scales down proportionally across breakpoints.
7. **Content-first order** — Section headers/text always first in source order for UX and accessibility.

---

## 9. CSS Variable Quick Reference

```css
:root {
  /* Colors */
  --off-white-bg: #d9d2ca;
  --white-card: #e5ded7;
  --transparent: hsla(0, 0%, 100%, 0);
  --brand-green: #40775f;
  --brand-ember: #d8602f;
  --forest-green: #273730;
  --pale-ember: #e8a075;
  --light-green: #a9d8c0;
  --muted-text: #6b6862;
  --forest-green-trans: hsla(153.75, 17%, 18.4%, 0.5);
  --color: white;

  /* Fonts */
  --font-headings: 'Bricolage Grotesque', sans-serif;
  --font-paragraphs: 'DM Mono', monospace;

  /* Font Sizes (desktop defaults) */
  --font-hero: 60px;
  --font-section-heading: 32px;
  --font-sub-heading: 20px;
  --font-paragraph: 18px;

  /* Spacing */
  --section-side-padding: 48px;
  --section-tb-padding: 4px;
  --large-bento-padding: 32px;
  --small-bento-padding: 16px;
  --grid-gap: 8px;
  --h-para-gap: 16px;
  --text-wrap-padding: 8px;       /* → 4px on phone */
  --text-wrap-gap: 16px;          /* → 8px on phone */
  --paragraph-top-margin: 16px;   /* → 8px on phone */
  --button-holder-margin: 48px;
  --divider-height: 100px;
  --min-bottom-pad: 64px;

  /* Radii */
  --outside-corner: 8px;

  /* Dimensions */
  --max-section-width: 1600px;
  --max-section-height: 100vh;
  --hero-section-max-height: 80vh;  /* hero sections only */
  --min-text-bento-height: 300px;
  --min-hero-bento-height: 600px;
  --boxy-paragraph-max-width: 500px;
}
```
