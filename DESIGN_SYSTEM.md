# LeadSpark Design System

> Extracted from Webflow project. This document is structured for both human readability and LLM consumption.
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

### Font Sizes (Responsive)

| Token | CSS Variable | Desktop (default) | iPad | Phone | Large Laptop | Small Desktop | Large Desktop |
|---|---|---|---|---|---|---|---|
| Hero Heading | `--_font-sizes---hero-heading--size` | 60px | 6vw | 8vw | 60px | 60px | 60px |
| Section Heading | `--_font-sizes---section-heading--size` | 32px | 3.6vw | 6vw | 32px | 32px | 32px |
| Sub Heading | `--_font-sizes---sub-heading--size` | 20px | 2vw | 3.2vw | 20px | 20px | 20px |
| Paragraph | `--_font-sizes---paragraph--size` | 18px | 2vw | 2.8vw | 18px | 18px | 18px |

### Line Heights

| Token | CSS Variable | Default | Small Desktop |
|---|---|---|---|
| Hero Heading | `--_font-sizes---hero-heading--height` | 120% | 120% |
| Sub Heading | `--_font-sizes---sub-heading--height` | 120% | 120% |
| Section Heading | `--_font-sizes---section-heading--percentage` | 110% | 140% (small desktop) |

### Typography Rules
- iPad and Phone use **viewport-width units** for fluid scaling
- Desktop sizes use **fixed px values**
- Headings: Bricolage Grotesque (geometric, modern)
- Body: DM Mono (monospace — gives a technical/dev feel)

---

## 3. Spacing (Padding + Gaps)

### Section & Container Spacing

| Token | CSS Variable | Desktop | Small Desktop | iPad | Phone | Mobile Phone |
|---|---|---|---|---|---|---|
| Section Side Padding | `--_padding-gaps---section-containers--section-side-padding` | 48px | 64px | 16px | 16px | 8px |
| Section Top/Bottom Padding | `--_padding-gaps---section-containers--top-bottom-padding` | 8px | 8px | 8px | 8px | 8px |

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

The design system uses **Webflow variable modes** to handle responsiveness. Each variable collection has device-specific modes:

### Font Sizes Modes
| Mode | Target |
|---|---|
| Default | Standard laptop (~1024-1279px) |
| Large Laptop | ~1280-1439px |
| Small Desktop | ~1440-1599px |
| Large Desktop | 1600px+ |
| iPad | Tablet (~768-1023px) |
| Phone | Mobile (~320-767px) |

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

### Bento Grid System
- Uses CSS Grid with **auto-fit** behavior
- Grid gap: 8px desktop → 4px mobile
- Cards have two tiers: **Large Bento** (32px padding) and **Small Bento** (16px padding)
- Hero bento minimum height: 600px (400px mobile)
- Text bento minimum height: 300px (100px mobile)
- Outside corner radius: 8px → 4px on mobile
- Card surface color: `--white-card` (#e5ded7)
- Grid items auto-size to the largest bento's dimensions

### Section Structure
- Max width: 1600px, centered
- Max height: 100vh per section
- Side padding: 48-64px desktop, 16px tablet, 8px mobile portrait
- Sections separated by dividers: 100px desktop → 56px mobile

### Text Wrap System
- **Every piece of text** sits inside a `.text-wrap` container
- `.text-wrap` has padding of `--text-wrap-padding`: 8px desktop → 4px mobile (all sides)
- `.text-wrap` has internal gap of `--text-wrap-gap`: 16px desktop → 8px mobile
- **Associated text** (e.g. heading + sub-heading that are intentionally close together) shares **one** `.text-wrap`
- **Separate text** (e.g. a paragraph that is visually distinct from the heading group) gets its **own** `.text-wrap`
- Do NOT wrap every individual text element — group by intent

### Paragraph Rules
- All `.paragraph` elements have a top margin of `--paragraph-top-margin`: 16px desktop → 8px mobile
- Exception: a paragraph that is the first child inside a `.text-wrap` has no top margin (gap handles the spacing)
- Paragraph max-width capped at 500px (`--boxy-paragraph`) for readability
- Button/CTA sits `--button-holder-margin` (48px desktop → 24px mobile) below text content

### Image Rules
- All images (except the LEADSPARK vertical logo) have `max-width: 70%` and `max-height: 70%` of their parent container, and are centered
- The LEADSPARK vertical logo image fills its container at `opacity: 0.2`

### LEADSPARK Bento
- Top padding matches the neighboring hero content div: `calc(--large-bento-padding + --text-wrap-padding)` for visual alignment
- Bottom and side padding uses `--logo-side-padding`

### Nav
- Nav follows the same bento grid as the rest of the site
- Logo sits in its own 1-column bento (matches LEADSPARK vertical column width)
- Nav links are `position: absolute` centered horizontally in the nav links bento
- CTA button right-aligned in nav links bento
- Hamburger menu replaces nav links on tablet (≤991px) and below

### Spark
- 8 spokes at 45° intervals, 1px ember-colored lines
- Max width/height: 200px
- Center circle: pale ember, semi-transparent, glows on scroll
- Whole spark rotates: slow idle spin + accelerates proportional to scroll speed

---

## 8. Design Principles (Inferred)

1. **Warm & Organic** — Beige/cream backgrounds with green + ember accents. Not sterile white.
2. **Technical Craft** — DM Mono body text signals technical competence. Bricolage Grotesque headings add personality.
3. **Bento Layout** — Grid-based card system is the primary compositional tool. Cards hug content or expand to fill.
4. **Responsive via Variables** — Not media-query overrides; uses Webflow variable modes for systematic scaling.
5. **Tight Grid Gaps** — 8px/6px/4px gaps give a dense, editorial feel.
6. **Progressive Reduction** — Every token scales down proportionally across breakpoints (padding, radii, font sizes, dividers).

---

## 9. CSS Variable Quick Reference (for code)

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
  --section-tb-padding: 8px;
  --large-bento-padding: 32px;
  --small-bento-padding: 16px;
  --grid-gap: 8px;
  --h-para-gap: 16px;
  --text-wrap-padding: 8px;    /* → 4px on phone */
  --text-wrap-gap: 16px;       /* → 8px on phone */
  --paragraph-top-margin: 16px; /* → 8px on phone */
  --button-holder-margin: 48px;
  --divider-height: 100px;
  --min-bottom-pad: 64px;

  /* Radii */
  --outside-corner: 8px;

  /* Dimensions */
  --max-section-width: 1600px;
  --max-section-height: 100vh;
  --min-text-bento-height: 300px;
  --min-hero-bento-height: 600px;
  --boxy-paragraph-max-width: 500px;
}
```
