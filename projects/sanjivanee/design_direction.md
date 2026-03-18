# Design Direction — Sanjivanee
> Phase 4 — Visual Direction
> Energy: Precision × Warmth
> Expressive Layer: Typography

---

## 1. Design Energy Intersection

| | |
|---|---|
| **Primary Energy (Structural)** | Precision — sets surfaces, grid, content tokens (60% of UI) |
| **Secondary Energy (Expressive)** | Warmth — sets brand color and accent (40% of UI) |
| **Intersection Name** | Boutique Consultancy |
| **Visual Zone** | "I am rigorous and expert, and I am also a thinking partner who cares about your outcome." |

**What this looks like in practice:**
The grid is tight. The type hierarchy is strong and intentional. The spacing is generous but structured. Then — in the accent color, in the texture of the background, in the body font's rounded terminals — warmth surfaces. Never soft. Never precious. Just human.

---

## 2. Typography

**Selected Pairing: #3 — Sora + IBM Plex Sans**
> Direct match for Precision × Warmth per the font pairing system.

| Role | Font | Rationale |
|---|---|---|
| **Display / Hero** | Sora (Bold / ExtraBold) | Geometric ink traps = Precision. Rounded terminals = Warmth. Feels sharp and expert without being cold. |
| **Heading (H2–H4)** | Sora (SemiBold / Medium) | Consistent family, lighter weight creates hierarchy without introducing a second personality. |
| **Body / Long-form** | IBM Plex Sans (Regular / Light) | Humanist structure. Designed for reading. Carries warmth through its letter forms. Technical enough to not feel casual. |
| **Labels / Eyebrow / Captions** | IBM Plex Sans (Medium, tracked +0.08em) | Adds formality to metadata without a separate typeface. |
| **Monospace (if needed)** | IBM Plex Mono | Optional: for code-adjacent content or stat callouts. Shares Plex DNA, stays coherent. |

### Typographic Scale (Desktop)

| Token | Size | Weight | Line Height | Use |
|---|---|---|---|---|
| `--text-hero` | 64–80px | 800 (ExtraBold) | 1.05 | Hero headline |
| `--text-h1` | 48px | 700 (Bold) | 1.1 | Section titles |
| `--text-h2` | 36px | 600 (SemiBold) | 1.15 | Sub-section titles |
| `--text-h3` | 24px | 600 (SemiBold) | 1.3 | Card titles, service names |
| `--text-body-lg` | 18px | 400 (Regular) | 1.65 | Lead body copy |
| `--text-body` | 16px | 400 (Regular) | 1.7 | Standard body |
| `--text-label` | 12px | 500 (Medium) | 1.4 | Eyebrows, labels, tags — tracked |
| `--text-caption` | 14px | 400 (Regular) | 1.5 | Fine print, footer |

### Mobile Scale Adjustments
- `--text-hero`: 40–48px
- `--text-h1`: 32px
- `--text-body-lg`: 17px

---

## 3. Color Palette

**Palette Name: Linen + Ink**
> Precision is structural (cool, high-contrast surfaces). Warmth is expressive (earthy, organic accent). Together: a boutique consultancy that reads as expert, not corporate.

### CSS Tokens

```css
:root {
  /* Brand (Warmth — 40%) */
  --color-primary:    hsl(16, 48%, 44%);   /* Muted Terracotta — warm authority */
  --color-secondary:  hsl(16, 30%, 58%);   /* Terracotta mid — hover states */
  --color-accent:     hsl(38, 60%, 52%);   /* Warm Amber — selective highlights */

  /* Surfaces (Precision — 60%) */
  --color-background: hsl(36, 20%, 97%);   /* Linen — warm off-white, not stark */
  --color-surface-1:  hsl(36, 15%, 93%);   /* Parchment — card backgrounds */
  --color-surface-2:  hsl(36, 10%, 89%);   /* Stone — elevated containers */
  --color-border:     hsl(36, 8%, 84%);    /* Soft rule — low contrast, structural */

  /* Content (Precision — ink-forward) */
  --color-foreground: hsl(36, 8%, 10%);    /* Near-black with a warm tint */
  --color-muted-fg:   hsl(36, 5%, 42%);    /* Warm mid-gray — body copy */
  --color-disabled-fg:hsl(36, 4%, 65%);    /* Placeholder text */
}

/* Dark Mode */
@media (prefers-color-scheme: dark) {
  :root {
    --color-background: hsl(36, 6%, 9%);
    --color-surface-1:  hsl(36, 5%, 13%);
    --color-surface-2:  hsl(36, 4%, 17%);
    --color-border:     hsl(36, 4%, 22%);
    --color-foreground: hsl(36, 12%, 95%);
    --color-muted-fg:   hsl(36, 6%, 65%);
  }
}
```

### Palette at a Glance

| Swatch | Name | Hex (approx) | Role |
|---|---|---|---|
| Linen | Background | `#F9F7F4` | Page background |
| Parchment | Surface-1 | `#EDEBE6` | Card backgrounds |
| Near-black | Foreground | `#1C1A18` | Headlines, primary text |
| Warm gray | Muted FG | `#6B6762` | Body copy, labels |
| Terracotta | Primary | `#B05A38` | Primary CTAs, links |
| Amber | Accent | `#C88C3A` | Selective highlights only |

### Color Usage Rules
- **CTA buttons**: `--color-primary` background + white text. Always high contrast.
- **Accent** (`--color-accent`): Use only once per page — e.g., a step number, an underline, a hover state. Never for body text.
- **Linen background**: Creates warmth without effort. Let it do its work. Don't override with pure white containers.
- **Borders**: Visible but quiet. 1px `--color-border`. Never dark.

---

## 4. Spacing & Grid

| Token | Value | Notes |
|---|---|---|
| `--space-unit` | 8px | Base grid unit |
| Section padding | 96–128px (desktop) / 64px (mobile) | Generous. Breathing room is credibility. |
| Max content width | 1100px | Prevents line lengths from going too wide |
| Column grid | 12-col, 24px gutter | Standard. Let the content feel intentional, not tight. |
| Card padding | 32px | Roomy. Not cramped. |

---

## 5. Motion Profile

**Intersection Blend: Precision eases × Warmth timing**

| Property | Value | Rationale |
|---|---|---|
| **Primary ease** | `cubic-bezier(0.25, 1, 0.5, 1)` — Fluid Out (Circ Out) | Long, smooth finish. Warm and confident, not snappy. |
| **Standard duration** | 300ms | Fast enough to feel Precise; long enough to feel deliberate. |
| **Section entrance duration** | 500ms | `--duration-slow`. Sections settle, not snap. |
| **Micro-interaction duration** | 150ms | `--duration-fast`. Hover states are instant but smooth. |
| **Y-axis shift (entrance)** | 12px | Small. No dramatic flying in. Just a gentle settle. |
| **Stagger (list items)** | 60ms between items | Left-to-right, top-to-bottom. Precision order. |
| **Overshoot / bounce** | None | Precision rejects it. |

### Motion Rules
- All section content fades up (opacity 0→1, Y 12px→0) on scroll entrance.
- Hero headline animates first, subhead second (200ms stagger), CTA third (400ms stagger).
- No scroll-jacking. No parallax on mobile.
- Process step numbers: subtle scale reveal (0.85→1) on scroll, staggered per step.

---

## 6. Imagery Direction

**Three types of images, used selectively:**

### A. The Working Portrait (Used in Hero + About)
- Sanjivanee in a real working moment — at a whiteboard, at a table with Post-its, in conversation
- Warm, natural light preferred. Not studio/glamour lighting.
- Direct or slightly off-camera gaze. Confident, not performed.
- Color treatment: slight warm tone grade. Not heavily edited. Feels real.
- **NOT:** LinkedIn-style corporate headshot. **NOT:** generic "woman smiling at laptop."

### B. The Room (Used in Process / Services sections)
- Collaborative working spaces — workshop rooms, design sprint walls, annotated sketches
- Focus on the work surface, not the people. Artifacts visible: Post-its, markers, printed frames.
- Warm tones. Natural light or warm incandescent.
- Used as supporting imagery, not hero imagery.
- Color treatment: slightly desaturated so it doesn't compete with the terracotta accent.

### C. The Outcome Moment (Used in Case Studies)
- Abstract or detail-level: a decision being written on a whiteboard, a prototype on a device, a team nodding in agreement
- Can be illustrative or photographic. Could be a clean wireframe screenshot.
- Keep these minimal and purposeful. One per case study.

### Imagery Don'ts
- No stock photos of "business people in a meeting room"
- No photos of generic laptops, coffee cups, or blurred bokeh
- No overly saturated, high-saturation lifestyle photography

---

## 7. Design Direction Summary Card

| Property | Decision |
|---|---|
| **Energy** | Precision × Warmth |
| **Visual Zone** | Boutique Consultancy |
| **Expressive Layer** | Typography |
| **Display Font** | Sora (Bold / ExtraBold) |
| **Body Font** | IBM Plex Sans (Regular) |
| **Background** | Linen `#F9F7F4` |
| **Foreground** | Near-black `#1C1A18` |
| **Primary / CTA** | Terracotta `#B05A38` |
| **Accent** | Warm Amber `#C88C3A` |
| **Motion** | Fluid Out, 300ms standard, 12px Y-shift |
| **Grid** | 12-col, 1100px max, 96px section padding |

---

## 8. Visual Reference Images (Art Direction)

Three reference images to anchor the visual direction. Use these prompts to source or generate.

---

### Reference 1 — Typography as Architecture
**Prompt / Description:**
> A minimal editorial layout on warm linen paper. A bold, geometric sans-serif headline ("Precision. Warmth. Strategy.") in near-black ink at large scale, with a short paragraph of smaller humanist sans body text below. Generous white space. A single muted terracotta rule or underline accent. No photography. Pure typography. Feels like a high-end consultancy brochure from a boutique strategy firm. Sora + IBM Plex Sans energy.

**Purpose:** Confirms the typographic hierarchy and shows that the Expressive Layer (Typography) can carry the entire design without needing color or imagery to do the heavy lifting.

---

### Reference 2 — The Working Portrait
**Prompt / Description:**
> A candid photograph of a South Asian woman in her late 30s, photographed in warm natural light. She is standing at a large whiteboard covered in sticky notes and handwritten frameworks. Her posture is confident and engaged — mid-gesture, pointing at something on the board. She's dressed in clean, minimal clothing (not corporate, not casual — smart, considered). The room has warm tones: wood surfaces, natural daylight from a window. The image is slightly warm-graded, slightly desaturated in the shadows. Feels real, not posed.

**Purpose:** Sets the standard for Sanjivanee's portrait photography. Art direction for the session or for sourcing a reference.

---

### Reference 3 — The Boutique Consultancy Page
**Prompt / Description:**
> A screenshot or mockup of a minimal, premium consultancy homepage. Linen/cream background. A large bold headline in a geometric sans ("Move faster. Decide together."). Below it, a short subheadline in a warm gray humanist sans. A single terracotta-colored CTA button ("Book a Call"). Below the fold, a clean row of three small impact stats in near-black with warm gray labels. The feel is: boutique strategy firm meets editorial magazine. Restrained, expert, human. No decoration. No icons. No gradients.

**Purpose:** Full-page visual anchor. Shows the team what the finished design should feel like before a single line of code is written.

---
