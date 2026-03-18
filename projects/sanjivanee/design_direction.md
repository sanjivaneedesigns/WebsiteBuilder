# Design Direction — Sanjivanee
> Phase 4 — Visual Direction (Revised)
> Energy: Edge × Craft
> Expressive Layer: Typography + Color

---

## 1. Design Energy Intersection

| | |
|---|---|
| **Primary Energy (Structural)** | Edge — sets surfaces, contrast, typographic boldness (60% of UI) |
| **Secondary Energy (Expressive)** | Craft — sets brand color, material texture, and considered detail (40% of UI) |
| **Intersection Name** | Editorial Studio |
| **Visual Zone** | "I work with precision and intent — and the work itself shows the thinking behind it." |

**What this looks like in practice:**
The background reads like uncoated paper. The type is bold and unapologetic — large display, clear hierarchy, no decoration. One vivid accent carries the energy. Grid lines and structure are visible features, not hidden scaffolding. The surface does the warmth work — bone in light mode, near-black in dark — so the accent can be cool, precise, and intense without the palette feeling cold.

---

## 2. Typography

**Selected Pairing: Custom — Bricolage Grotesque + Manrope**
> Custom pairing. Bricolage is the display font from pairing #14 (Edge/Craft/Depth). Spectral (its original body match) is dropped in favour of Manrope — a geometric sans from pairings #10/#12 (Clarity/Precision) that provides clean contrast without competing with Bricolage's ink-trap character.

| Role | Font | Rationale |
|---|---|---|
| **Display / Hero** | Bricolage Grotesque (Bold / ExtraBold) | Radical ink traps and wide stance = Edge. Crafted, textural letterforms = Craft. Sets the editorial tone immediately. |
| **Heading (H2–H4)** | Bricolage Grotesque (SemiBold / Medium) | Consistent family at lighter weight. Hierarchy through weight, not family switching. |
| **Body / Long-form** | Manrope (Regular / Light) | Geometric sans — highly readable, clean. Provides contrast to Bricolage's character without fighting it. |
| **Labels / Eyebrow / Captions** | Manrope (Medium, tracked +0.10em) | Slightly more tracking than previous system — suits the editorial metadata style (e.g., `(Client)`, `(Year)` style labels). |
| **Monospace (if needed)** | IBM Plex Mono | Optional: for code-adjacent content or data callouts. |

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

**Palette Name: Bone & Klein**
> Edge is structural (high-contrast bone surfaces, warm near-black ink). Craft is expressive (a single vivid blue that reads with pigment-like intensity — not corporate, not digital, painterly in its depth). Together: an editorial studio that feels graphic, precise, and confident without leaning into earthy neutrals.
>
> The two blues are surface-specific: Klein Blue (`hsl(228, 92%, 40%)`) is optimised for the bone surface — its depth reads like pigment on uncoated paper. Cobalt (`hsl(218, 85%, 62%)`) is optimised for the near-black dark mode surface — brighter, sharper, more clarifying against the ink field. Same editorial family; different tuning for each register.

### CSS Tokens

```css
:root {
  /* Brand (Craft — 40%) */
  /* One vivid accent. No secondary range — Edge × Craft uses singular colour. */
  --color-primary:    hsl(228, 92%, 40%);   /* Klein Blue — intense pigment-like depth on bone surface */
  /* Hover/active state: hsl(228, 92%, 32%) — decisive darkening, no softness */

  /* Surfaces (Edge — 60%) */
  --color-background: hsl(40, 16%, 92%);   /* Bone — uncoated paper quality, not digital white */
  --color-surface-1:  hsl(38, 12%, 87%);   /* Pressed paper — card backgrounds */
  --color-surface-2:  hsl(36, 9%, 82%);    /* Deep paper — elevated containers */
  --color-border:     hsl(36, 7%, 75%);    /* Visible rule — slightly more present than previous system */

  /* Content (Edge — ink-forward) */
  --color-foreground: hsl(22, 15%, 9%);    /* Warm Ink — near-black with red-brown undertone */
  --color-muted-fg:   hsl(24, 8%, 40%);    /* Warm dark gray — body copy */
  --color-disabled-fg:hsl(28, 5%, 62%);    /* Placeholder text */
}

/* Dark Mode — near-black ink surface + Cobalt: sharp, clarifying, high-contrast editorial */
@media (prefers-color-scheme: dark) {
  :root {
    --color-background: hsl(20, 10%, 7%);    /* Warm near-black — not cold, not pure #000 */
    --color-surface-1:  hsl(20, 8%, 12%);    /* Warm dark surface */
    --color-surface-2:  hsl(20, 6%, 17%);    /* Elevated dark */
    --color-border:     hsl(20, 5%, 22%);    /* Quiet dark rule */
    --color-foreground: hsl(38, 18%, 94%);   /* Warm off-white — not stark */
    --color-muted-fg:   hsl(32, 8%, 64%);    /* Warm mid-gray */
    --color-primary:    hsl(218, 85%, 62%);  /* Cobalt — lightened for dark surface, retains clarity */
  }
}
```

### Palette at a Glance

| Swatch | Name | Hex (approx) | Role |
|---|---|---|---|
| Bone | Background | `#E8E4DB` | Page background |
| Pressed Paper | Surface-1 | `#DEDAD2` | Card backgrounds |
| Warm Ink | Foreground | `#1C1612` | Headlines, primary text |
| Warm Dark Gray | Muted FG | `#6A6460` | Body copy, labels |
| Klein Blue | Primary | `#0A28C4` | CTAs, links, active states — on bone |

**Dark mode additionally:**

| Swatch | Name | Hex (approx) | Role |
|---|---|---|---|
| Warm Near-Black | Background | `#141210` | Dark bg |
| Warm Off-White | Foreground | `#F1EDE4` | Dark mode text |
| Cobalt | Primary | `#4C88F1` | Dark mode CTAs — sharp and clarifying on near-black |

### Color Usage Rules
- **CTA buttons**: `--color-primary` background + white text. Klein Blue is deep enough for white to pass AAA at normal text sizes.
- **Hover states**: `hsl(228, 92%, 32%)` (Klein Blue, darkened 8%) — decisive, no softness. Dark mode: `hsl(218, 85%, 55%)`.
- **Bone background**: The warmth engine of the light mode. The warm ground makes Klein Blue read richer — let it do that work. Never override with pure white containers.
- **Borders**: More visible than the previous system — 1px `--color-border`. In Edge × Craft, the grid and structure are features, not hidden scaffolding.
- **One accent rule**: Do not add a second accent. Klein Blue / Cobalt is singular. If you need a dark treatment, use `--color-foreground` (ink) — invert blocks use ink-on-bone rather than introducing new colours.

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

**Intersection Blend: Edge decisiveness × Craft considered timing**

| Property | Value | Rationale |
|---|---|---|
| **Primary ease** | `cubic-bezier(0.19, 1, 0.22, 1)` — Expo Out | Fast to destination, confident finish. Edge energy: decisive, not lingering. |
| **Standard duration** | 250ms | Slightly faster than the previous system. Crisp. |
| **Section entrance duration** | 450ms | Still considered — Craft slows the Edge impulse just enough. |
| **Micro-interaction duration** | 150ms | `--duration-fast`. Hover states are immediate. |
| **Y-axis shift (entrance)** | 16px | Slightly more movement than before — Edge permits a more graphic entrance. |
| **Stagger (list items)** | 50ms between items | Tight stagger. Feels deliberate, not slow. |
| **Overshoot / bounce** | None | Edge is decisive, not playful. |

### Motion Rules
- All section content fades up (opacity 0→1, Y 16px→0) on scroll entrance.
- Hero headline animates first, subhead second (200ms stagger), CTA third (350ms stagger).
- No scroll-jacking. No parallax on mobile.
- Process step numbers: scale reveal (0.90→1) + fade on scroll, staggered per step.

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
- Color treatment: slightly desaturated and warm-graded so it sits against bone backgrounds without competing with the Klein Blue accent.

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
| **Energy** | Edge × Craft |
| **Visual Zone** | Editorial Studio |
| **Expressive Layer** | Typography + Color |
| **Display Font** | Bricolage Grotesque (Bold / ExtraBold) |
| **Body Font** | Manrope (Regular / Light) |
| **Background** | Bone `#E8E4DB` |
| **Foreground** | Warm Ink `#1C1612` |
| **Primary / CTA** | Klein Blue `#0A28C4` — on bone surface |
| **Accent** | None — Klein Blue is singular |
| **Dark BG** | Warm Near-Black `#141210` |
| **Dark Primary** | Cobalt `#4C88F1` — on near-black surface |
| **Motion** | Expo Out, 250ms standard, 16px Y-shift |
| **Grid** | 12-col, 1100px max, 96px section padding |

---

## 8. Visual Reference Images (Art Direction)

Three reference images to anchor the revised visual direction. Use these prompts to source or generate.

---

### Reference 1 — Grid as Structure (Editorial Print Register)
**Prompt / Description:**
> A large-format poster on warm bone/uncoated paper. A visible grid of thin lines divides the surface into cells. Inside the cells: a mix of bold, wide Grotesque headline type ("Everything around you was made by people") and small collaged images — some in near-black, some in bone. The typography is the star. No color except the paper tone and near-black ink. Feels like a risograph print or a well-designed studio zine. Bricolage Grotesque energy — wide, editorial, crafted.

**Purpose:** Establishes the bone paper surface, grid structure as a feature, and the ink-on-paper material quality that defines the light mode.

---

### Reference 2 — Dark Editorial with Single Accent
**Prompt / Description:**
> A website screenshot on a warm near-black background (not pure black — a dark brown-charcoal). A large headline in warm off-white Grotesque type. One vivid cobalt-blue element: a CTA button or a highlighted name, bright and clarifying against the dark field. Grid lines visible as thin warm-gray rules. The overall feel is graphic, editorial, and precise — the single cobalt accent does all the structural work. Manrope body copy in warm off-white, small and clear. Feels like a high-contrast poster or editorial magazine: intelligent, high contrast, uncompromising.

**Purpose:** Defines the dark mode register and shows how the Cobalt accent behaves at full contrast on near-black. Also anchors the motion towards decisive rather than soft.

---

### Reference 3 — Editorial Studio Homepage
**Prompt / Description:**
> A homepage mockup in the bone-and-ink palette. A very large Bricolage Grotesque headline dominates the top — wide, bold, with visible ink traps. Below it, a short Manrope body paragraph in warm dark gray. A metadata row in small tracked Manrope labels: `(Discipline)` `(Location)` `(Availability)` — each followed by a short value. One Klein Blue CTA: `→ Book a Call` — intense, almost pigment-like against the warm bone ground. No decorative elements, no gradients, no icons. The grid is perceptible but not forced. Feels like the homepage of a design studio or editorial consultancy that trusts the typography completely.

**Purpose:** Full-page visual anchor for the revised direction. Shows Bricolage + Manrope in hierarchy, bone backgrounds, and Klein Blue accent in context — the blue against warm bone is the defining visual contrast of the light mode.

---
