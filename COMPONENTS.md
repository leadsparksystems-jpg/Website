# Components

## Genuine Components (reuse in code)

### `btn-cta`
**Purpose:** Primary call-to-action button with label + arrow icon circle.  
**Element:** `<a>` or `<button>` with class `btn-cta`  
**Structure:**
```html
<a href="#" class="btn-cta">
  <span class="btn-cta__label">Label Text</span>
  <span class="btn-cta__icon"><img src="..." alt="" aria-hidden="true" /></span>
</a>
```
**Tokens used:** `--soft-ember`, `--dark-green`, `--cta-button-shadow`, `--arrow-circle-shadow`, `--button-radius`

---

### `btn-scroll`
**Purpose:** Secondary page-scroll link (e.g. "SEE HOW") with rotated arrow icon.  
**Element:** `<a>` or `<button>` with class `btn-scroll`  
**Structure:**
```html
<a href="#section" class="btn-scroll">
  <span class="btn-scroll__label">See How</span>
  <span class="btn-scroll__icon"><img src="..." alt="" aria-hidden="true" /></span>
</a>
```
**Tokens used:** `--dark-green`, `--button-radius`

---

## Classes / Wraps (Figma components → CSS classes)

### `.bento`
Base bento card. `overflow: hidden`. Add modifier for sizing:
- `.bento--leadspark` — col 1, full height, vertical text image
- `.bento--main` — col 2–9, main content area
- `.bento--image` — col 10–12 top, image display
- `.bento--stats` — col 10–12 bottom, stat + scroll link

### `.hero-grid`
12-col / 2-row CSS grid. Gap + padding from `--main-grid-hero-grid-gap`.

### `.text-wrap-paragraph`
Padding wrapper around body paragraph text. Uses `--text-wrap-default-*` tokens.

### `.stats-text`
Inner padding + gap for stat number + label pair. Uses `--text-wrap-stat-*` tokens.

---

## Sections Built

| Section | File | Status |
|---------|------|--------|
| Hero (desktop) | `index.html` | ✅ Done |
