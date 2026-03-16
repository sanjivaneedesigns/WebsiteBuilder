# Color System Rules — Base Design System
### Building Semantic, Accessible, and Themesable Palettes
This document defines the **structure** and **logic** of the Antigravity color system. We do not define specific brand colors here; we define how those colors are mapped to UI tokens to ensure a "1:1 Pixel Perfect" implementation that works across themes.
---
## 🏗️ 1. Token Architecture
Every palette must map to these semantic tokens. Avoid using raw hex codes in code.
### Base Tokens (Brand)
| Token | Role | Description |
|---|---|---|
| `--color-primary` | Brand Identity | Main action color (primary buttons, links, active states). |
| `--color-secondary` | Supportive | Secondary actions, subtle branding moments. |
| `--color-accent` | Highlights | Purely decorative or attention-grabbing (badges, underlines). |
### Surface Tokens (Backgrounds)
| Token | Role | Description |
|---|---|---|
| `--color-background` | Global Base | Page background. Usually off-white or deep charcoal. |
| `--color-surface-1` | Container Base | Card backgrounds, modals, navbars. |
| `--color-surface-2` | Raised Container | Elevated components (popovers, nested cards). |
| `--color-border` | Separation | Rules, card borders, dividers. |
### Content Tokens (Foregrounds)
| Token | Role | Description |
|---|---|---|
| `--color-foreground` | High Emphasis | Primary text, headings (max contrast). |
| `--color-muted-fg` | Medium Emphasis | Body copy, secondary labels (reduced contrast). |
| `--color-disabled-fg` | Low Emphasis | Placeholder text, non-interactive elements. |
---
## ⚡ 2. Mapping by Design Energy
Each Energy profile dictates how you weight the color system:
| Energy | Palette Weights |
|---|---|
| **Precision** | Cool neutrals (grays/blues). High contrast between borders and backgrounds. Sparse accent use. |
| **Warmth** | Warm neutrals (beiges/creams). Low contrast borders. Earthy, organic accents. |
| **Momentum** | Very high contrast. Pure black/white with one vibrant, saturated primary accent. |
| **Depth** | Layered shadows and gradients. Deep, moody palettes with subtle accent pops. |
| **Clarity** | Max whitespace. Single accent color used only for interaction (CTAs). |
| **Edge** | Clashing or neon colors. Rule-breaking contrast. Unexpected accent pairings. |
| **Craft** | Earthy, desaturated tones (terracotta, slate, olive). High value contrast for legibility. Tactile, "ink-like" neutrals. |
| **Trust** | Traditional "Institutional" colors (navy, forest green, burgundy). Stable, expected neutral pairings (slate gray). |
---
## ⚡ 3. Handling Energy Intersections
When two energies are selected (e.g., `Precision × Warmth`), follow this **Dominance Rule**:
1.  **Energy A (Structural):** Determines the **Surface** and **Content** tokens (60% of the UI). This sets the "Grounding" of the site.
2.  **Energy B (Expressive):** Determines the **Primary** and **Accent** tokens (40% of the UI). This provides the "Personality" pop.
**Example: `Momentum (Expressive)` × `Precision (Structural)`**
- Site uses high-precision grid lines and cool gray surfaces (`Precision`).
- Action buttons and scroll-triggered highlights use electric, high-saturation colors (`Momentum`).
---
## 🏗️ 4. Handling Pre-defined Branding
If a brand has fixed colors that clash with the desired Energy (e.g., a Neon Green brand wanting a "Trust" feel), we use **Contextual Framing**:
1.  **Ratio Control:** Do not change the brand color, change its **frequency**.
    - If the color is "Too Loud" for the energy: Use it only for micro-accents (tooltips, cursor dots, hover underlines).
    - If the color is "Too Dull" for the energy: Use it as a background texture or border color.
2.  **Neutral Counterweights:**
    - To make a bright color feel **"Trustworthy"** or **"Precise"**: Pair it with deep Navy or Slate and 1px hard borders.
    - To make a dull color feel **"Edge"** or **"Momentum"**: Pair it with high-contrast Black, use it in large typography, or add a glow/blur effect.
3.  **The "Desaturation" Leak:** Use technical neutrals (Grays with a 2-5% tint of the brand color) to "pull" the brand into the surfaces, making the palette feel cohesive even if the accent is a "clash."
---
## 🎨 3. Palette Generation Guidelines
When constructing a palette for a project:
1.  **The 60-30-10 Rule:**
    - 60% Secondary/Background (Neutral).
    - 30% Primary (Brand flavor).
    - 10% Accent (Call to actions).
2.  **Accessibility First:**
    - Always verify contrast ratios using WCAG 2.1 guidelines.
    - All paragraph text (`--color-muted-fg`) must maintain at least **4.5:1** contrast against `--color-background`.
    - Headings (`--color-foreground`) should target **7:1** when possible.
3.  **The Theme Flip (Dark Mode Logic):**
    - Do not simply invert values.
    - Surfaces should become **darker** as they elevate in light mode (shadows).
    - Surfaces should become **lighter** as they elevate in dark mode (inner glows/highlights).
---
## 🛠️ 4. Implementation Example (CSS)
```css
/* Example Project Palette: "Boutique Craft" */
:root {
  /* Brand */
  --color-primary:    hsl(28, 48%, 20%);   /* Earthy Brown */
  --color-accent:     hsl(12, 100%, 60%);  /* Terracotta */
  /* Surface */
  --color-background: hsl(30, 20%, 98%);   /* Off-white Cream */
  --color-surface-1:  hsl(30, 20%, 94%);
  --color-border:     hsl(30, 10%, 88%);
  /* Content */
  --color-foreground: hsl(0, 0%, 12%);     /* Deep Black/Gray */
  --color-muted-fg:   hsl(0, 0%, 45%);     /* Readable Gray */
}
/* Dark Mode Override */
@media (prefers-color-scheme: dark) {
  :root {
    --color-background: hsl(0, 0%, 8%);
    --color-surface-1:  hsl(0, 0%, 12%);
    --color-border:     hsl(0, 0%, 18%);
    --color-foreground: hsl(0, 0%, 96%);
    --color-muted-fg:   hsl(0, 0%, 70%);
  }
}
```
