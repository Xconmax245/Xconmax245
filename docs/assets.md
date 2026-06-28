# Asset System Documentation

This document describes each SVG asset in this profile repository — its purpose, dimensions, design tokens, animation parameters, and update instructions.

---

## Design System Reference

| Token | Value | Usage |
|---|---|---|
| Background | `#000000`, `#111111`, `#181818` | Base surfaces |
| Primary text | `#FFFFFF` | Headings, values |
| Accent blue | `#4F9DFF` | Borders, lines, nodes |
| Cyan | `#00F0FF` | Highlights, flagship elements |
| Violet | `#8844FF` | Research/experimental elements |
| Muted | `#555555`, `#333333` | Secondary text |
| Glass fill | `rgba(255,255,255,0.05)` | Card backgrounds |
| Fonts | Inter, JetBrains Mono (system fallbacks) | Typography |

---

## Assets

### `assets/banner/hero.svg`
- **Dimensions:** 800 × 280
- **Purpose:** Main profile header banner
- **Animations:**
  - `nodePulse` — 8 network nodes breathe in opacity (3–4s cycles)
  - `beamMove` — two light beams sweep left-to-right (11s, staggered 5.5s)
  - `cursorBlink` — blinking cursor after subtitle text (1.1s step)
  - `gridFade` — background grid pulses subtly (7s)
  - `ringExpand` — expanding rings on primary nodes (3s)
  - SMIL `animateMotion` — 6 data packets travel along connection paths
- **Update:** Edit name/subtitle/tagline text elements directly in the SVG

---

### `assets/footer.svg`
- **Dimensions:** 800 × 80
- **Purpose:** Closing footer with animated laser line
- **Animations:**
  - `laserPulse` — center line pulses (3s)
  - `dotMove` — two moving dots traverse the line (6s, staggered 3s)
- **Update:** Edit signature text at the bottom

---

### `assets/diagrams/architecture.svg`
- **Dimensions:** 800 × 360
- **Purpose:** Animated vertical technology stack map
- **Animations:**
  - `pulseFlow` — 6 data flow rectangles animate down connector lines (2s staggered)
  - `connPulse` — dashed connector lines pulse in opacity (3s)
- **Update:** Edit layer labels and tech annotations in the text elements. Add/remove layers by copying a `<rect>` + `<text>` pair and updating the y-coordinate (each layer is 56px apart)

---

### `assets/diagrams/timeline.svg`
- **Dimensions:** 800 × 200
- **Purpose:** Engineering career progression timeline
- **Animations:**
  - `nodeBeat` — 4 timeline nodes pulse with size and opacity
  - `arrowPulse` — connector arrows fade in/out
- **Update:** Edit year labels, title text, and description text. Node x-positions: 150, 340, 530, 680

---

### `assets/diagrams/metrics.svg`
- **Dimensions:** 800 × 130
- **Purpose:** Custom engineering metrics panel (auto-updated by `release.yml`)
- **Token format:** Values are injected via `sed` replacement targeting HTML comment markers:
  - `<!--REPOS-->` — public repository count
  - `<!--STARS-->` — total stars across all repos
  - `<!--COMMITS-->` — total commits (current year)
  - `<!--FOLLOWERS-->` — GitHub followers
  - `<!--PRS-->` — merged pull requests
  - `<!--ISSUES-->` — closed issues

> **Important:** Do not remove or rename the `<!--TOKEN-->` comment markers — the `release.yml` Action depends on them.

---

### `assets/cards/card-proxy.svg` (Flagship)
- **Dimensions:** 260 × 200
- **Accent color:** `#00F0FF` (cyan — flagship)
- **Update:** Edit project name, description lines, tech stack tags

### `assets/cards/card-oss.svg` (Open Source)
- **Dimensions:** 260 × 200
- **Accent color:** `#4F9DFF` (blue — OSS)
- **Update:** Same as above

### `assets/cards/card-research.svg` (Research)
- **Dimensions:** 260 × 200
- **Accent color:** `#8844FF` (violet — research/experimental)
- **Update:** Same as above. Icon is a mini consensus network graph.

---

### `assets/icons/logo.svg`
- **Dimensions:** 64 × 64
- **Purpose:** Monogram badge / avatar supplement
- **Update:** Swap the `X` character for your preferred monogram

---

## Adding a New Asset

1. Follow the design system tokens above
2. Use only CSS `@keyframes` or SMIL for animations — no JavaScript
3. Embed all filters and gradients in `<defs>` — no external references
4. Test with `xmllint --noout your-file.svg`
5. Reference it in `README.md` and add an entry to this document
