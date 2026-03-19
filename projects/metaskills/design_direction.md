# Metaskills — Design Direction
**Phase 4 Output | Precision × Warmth**

---

## Energy Intersection

| Role | Energy | Contribution |
|---|---|---|
| Structural (60%) | **Precision** | Tight grid, clean hierarchy, controlled spacing, cool-neutral surfaces |
| Expressive (40%) | **Warmth** | Display serif headlines, terracotta accent, soft section entrances |

**Why this intersection:**
Precision signals competence — employers trust what looks controlled and expert. Warmth signals humanity — candidates trust what feels approachable. Together they express exactly what no competitor is doing: a firm that is both rigorous AND human.

---

## Expressive Layer: Typography

Typography is the hero layer. Everything else (color, motion, spacing, imagery) is restrained.

The surprise is in the headlines — a high-contrast serif display face doing the brand storytelling while the UI stays clean and structured beneath it.

**Font Pairing: DM Serif Display + DM Sans**
*(Pair #19 — Trust × Clarity × Momentum — "top-tier modern agency feel")*

| Role | Font | Weight | Use |
|---|---|---|---|
| Display / H1 | DM Serif Display | Regular (400) | Hero headline, section openers |
| H2 / H3 | DM Serif Display | Regular (400) | Sub-headlines, tab headings |
| Body / UI | DM Sans | 300–400 | Body copy, nav, labels, captions |
| Eyebrow | DM Sans | 500, tracked | Section labels (e.g., "For Employers") |
| CTA / Button | DM Sans | 500–600 | Buttons, links |

**Type Scale (Desktop):**
- H1: 64–72px / line-height 1.1 / letter-spacing -0.02em
- H2: 40–48px / line-height 1.2
- H3: 28–32px / line-height 1.3
- Body: 17–18px / line-height 1.65
- Eyebrow: 12px / tracking 0.12em / uppercase
- Caption: 14px / DM Sans 300

---

## Color Palette

**Logic:** Bone surfaces (Precision's cool-warm neutrals) + Terracotta as the sole expressive action color (Warmth's earthy, confident personality). No blues. No grays. Instantly different from every competitor.

```css
:root {
  /* Brand */
  --color-primary:     hsl(14, 55%, 35%);   /* Deep Terracotta — CTAs, buttons */
  --color-secondary:   hsl(20, 8%, 13%);    /* Warm Charcoal — text, logo */
  --color-accent:      hsl(14, 62%, 52%);   /* Terracotta Pop — hover states, underlines */

  /* Surfaces */
  --color-background:  hsl(36, 28%, 97%);   /* Bone — page base */
  --color-surface-1:   hsl(36, 22%, 93%);   /* Cream — cards, tabs, nav */
  --color-surface-2:   hsl(36, 18%, 88%);   /* Deep Cream — active tab, authority band */
  --color-border:      hsl(36, 14%, 84%);   /* Warm hairline */

  /* Content */
  --color-foreground:  hsl(20, 8%, 13%);    /* Primary text */
  --color-muted-fg:    hsl(20, 5%, 44%);    /* Body copy, secondary labels */
  --color-disabled-fg: hsl(20, 3%, 68%);    /* Placeholders */
}
```

**Palette Story:**
- **60% Bone/Cream** — warm, airy, premium. Makes the page feel like high-quality paper.
- **30% Warm Charcoal** — the authority and structure. All headings, nav, footer.
- **10% Terracotta** — the only color with saturation. Every CTA, every active state, every key highlight. Earthy, confident, Indian-warm without being clichéd.

**What it avoids:** Corporate blue, cold gray, generic white. Nothing in this palette reads "job portal."

---

## Motion Profile

**Rule:** Since typography is expressive, motion is restrained. It communicates, not performs.

| Trigger | Duration | Easing | Property |
|---|---|---|---|
| Section entrance (scroll into view) | 500ms | `cubic-bezier(0.25, 1, 0.5, 1)` Fluid Out | opacity 0→1, translateY 14px→0 |
| Tab switch | 300ms | `cubic-bezier(0.25, 1, 0.5, 1)` Fluid Out | opacity fade + subtle Y shift |
| Button hover | 150ms | `cubic-bezier(0.34, 1.56, 0.64, 1)` Soft Back | background-color, slight scale (1.02) |
| Nav link hover | 150ms | linear | terracotta underline expand from left |
| Stagger (process steps) | 500ms + 80ms stagger | Fluid Out | Entrance cascade, left-to-right |

**No parallax. No kinetic hero. No scroll-jacking.** The premium feel comes from typography and color — not motion complexity.

---

## Spacing System

Editorial. Generous. Content breathes.

```css
:root {
  --space-xs:  8px;
  --space-sm:  16px;
  --space-md:  32px;
  --space-lg:  64px;
  --space-xl:  96px;
  --space-2xl: 144px;

  /* Section padding */
  --section-padding-y: var(--space-xl);     /* 96px top/bottom */
  --section-padding-x: var(--space-lg);     /* 64px sides (desktop) */

  /* Max content width */
  --max-width: 1200px;
  --content-width: 720px;    /* body copy max-width */
}
```

---

## Imagery Direction

**Rule:** No stock photography. Typography and space do the visual work.

- **Hero:** Pure typographic treatment. Large serif headline, sub-copy, dual CTAs. Optional: a single abstract geometric mark or thin rule — nothing more.
- **Tab module:** Icon set for process steps (line-drawn, not filled — Lucide or Phosphor icons at 1.5px stroke weight).
- **Why Metaskills pillars:** Small decorative marks or numbers — not illustration, not photography.
- **Social Proof:** Text cards only. Name + title + quote. No headshots (unless real client photos are provided).
- **Contact:** Clean form on a cream surface. No imagery.

**If imagery is used at all:** Abstract, textural — e.g., a close crop of woven fabric, paper texture, or architectural detail. Never handshakes, offices, or smiling professionals looking at laptops.

---

## Component Decisions

| Component | Decision |
|---|---|
| Nav | Transparent over bone, becomes surface-1 on scroll. Sticky. |
| Tab switcher | Two text labels, active state = terracotta underline + slightly deeper bg. No pill/button tabs — too bulky. |
| CTA buttons | Rounded rectangle. Primary: terracotta fill, white DM Sans 500. Secondary: transparent, terracotta border + text. |
| Process steps | Numbered (01, 02, 03) in DM Serif Display, large, muted. Label in DM Sans 500. Body in DM Sans 300. |
| Cards (testimonials) | Cream surface-1, 1px warm border, no shadow. Quote in DM Serif italic. Attribution in DM Sans caps. |
| Contact form | Surface-1 background. Full-width inputs, 1px border, terracotta focus ring. |

---

## 3 Visual Reference Anchors

**Reference 1 — Editorial Serif Confidence**
> Think: a boutique financial advisory or law firm that hired a top design studio. DM Serif Display headlines taking up 40% of the viewport. Bone background. Terracotta as the only point of colour. Maximum whitespace. The text IS the design.

**Reference 2 — Warm Precision Grid**
> Think: an architect's portfolio or a premium Indian design studio. Very tight, controlled grid. Everything snaps. But the surfaces are warm cream, not cold white. The serif creates personality within a precise system.

**Reference 3 — Tab UX done quietly**
> Think: a premium financial product's onboarding — two paths presented as quiet, typographic tabs. Not playful, not loud. The tab switch itself feels like turning a page. No animation theatrics. Just content, revealed.

---

## Design Tenets for Build

1. **Typography does the surprising.** Every other variable stays controlled.
2. **Terracotta once per section.** The accent is rare, which makes it mean something.
3. **Both tabs feel equally premium.** Neither audience should feel like the secondary option.
4. **Whitespace is content.** Empty space earns trust.
5. **No stock photo defaults.** If there's nothing real to show, show type and structure.
