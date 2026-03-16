# Icon Libraries — Base Design System
> **Status:** Draft · Last updated: 2026-03-02
> **Scope:** Defines the approved icon libraries, their roles, usage rules, sizing tokens, and implementation guidelines for all product surfaces.
---
## 1. Library Overview
| Library | Style family | License | CDN / Package | Best for |
|---|---|---|---|---|
| [Lucide](https://lucide.dev) | Outline (2px stroke) | ISC | `lucide-react` / `lucide` | App UI, dashboards, navigation |
| [Heroicons](https://heroicons.com) | Outline + Solid | MIT | `@heroicons/react` | Tailwind-based UIs, CTA buttons |
| [Phosphor](https://phosphoricons.com) | Thin / Light / Regular / Bold / Fill / Duotone | MIT | `@phosphor-icons/react` | Marketing pages, expressive UI |
| [Google Material Symbols](https://fonts.google.com/icons) | Outlined / Rounded / Sharp · Variable font | Apache 2.0 | Google Fonts CDN / `material-symbols` npm | Data-dense apps, Android-adjacent surfaces |
---
## 2. Role Assignment
Each library has a **primary role** to prevent visual inconsistency from mixing styles arbitrarily.
| Role | Library | Rationale |
|---|---|---|
| **Primary UI icons** | Lucide | Clean, consistent 2 px stroke; works at 16–24 px; minimal visual noise |
| **CTA & button icons** | Heroicons (Solid) | Filled style reads better at small sizes inside interactive elements |
| **Illustrative / expressive** | Phosphor (Duotone or Bold) | Two-tone weight gives flexibility for hero sections and empty states |
| **Data & system status** | Google Material Symbols | Variable weight + optical sizing match dense information layouts |
> **Rule:** Do not mix roles within the same component. An icon used for navigation should be Lucide; an icon used as a section illustration should be Phosphor.
---
## 3. Size Tokens
```css
/* tokens/icon-size.css */
--icon-xs:  12px;   /* Badges, inline tags */
--icon-sm:  16px;   /* Compact UI, table cells */
--icon-md:  20px;   /* Default — body text level */
--icon-lg:  24px;   /* Navigation, buttons */
--icon-xl:  32px;   /* Card headers, feature tiles */
--icon-2xl: 48px;   /* Empty states, section headers */
--icon-3xl: 64px;   /* Hero / illustrative use only */
```
### Library-specific sizing notes
| Library | Optimal range | Avoid below |
|---|---|---|
| Lucide | 16–32 px | 12 px |
| Heroicons | 16–24 px | 14 px |
| Phosphor | 20–64 px | 16 px (Thin weight) |
| Material Symbols | 20–48 px | 20 px (use `optical-size` axis) |
---
## 4. Color Tokens
Icons inherit text color by default (`currentColor`). Only override with semantic color tokens.
```css
/* tokens/icon-color.css */
--icon-primary:    var(--color-foreground);       /* Default */
--icon-secondary:  var(--color-muted-foreground); /* Supportive / decorative */
--icon-accent:     var(--color-accent);           /* Highlighted, active state */
--icon-danger:     var(--color-destructive);      /* Error, warning */
--icon-success:    var(--color-success);          /* Confirm, complete */
--icon-disabled:   var(--color-disabled);         /* Non-interactive */
```
> **Never** use raw hex values on icons. Always reference design tokens.
---
## 5. Stroke Weight Rules
| Library | Rule |
|---|---|
| Lucide | Always 2 px stroke. Do not alter `stroke-width`. |
| Heroicons | Use **Outline** (1.5 px) for nav; **Solid** for buttons and status chips. |
| Phosphor | Match weight to context: **Regular** for UI, **Bold/Fill** for CTAs, **Duotone** for illustrations. |
| Material Symbols | Use CSS font-variation-settings: `'wght' 300–700`, `'opsz' 20–48`, `'FILL' 0–1`, `'GRAD' -25–200`. |
Material Symbols variable font example:
```css
.icon-material {
  font-family: 'Material Symbols Outlined';
  font-variation-settings:
    'FILL' 0,
    'wght' 400,
    'GRAD' 0,
    'opsz' 24;
}
```
---
## 6. Implementation
### 6.1 Lucide (React)
```tsx
import { Search, ChevronRight, X } from 'lucide-react';
// Usage
<Search size={20} strokeWidth={2} className="text-foreground" />
```
### 6.2 Heroicons (React)
```tsx
import { MagnifyingGlassIcon } from '@heroicons/react/24/outline';
import { CheckCircleIcon } from '@heroicons/react/24/solid';
// Outline for nav; Solid for status
<MagnifyingGlassIcon className="w-5 h-5 text-foreground" />
<CheckCircleIcon className="w-5 h-5 text-success" />
```
### 6.3 Phosphor (React)
```tsx
import { Lightning, Star } from '@phosphor-icons/react';
// Duotone for illustrative use
<Lightning size={48} weight="duotone" color="var(--icon-accent)" />
```
### 6.4 Material Symbols (Web / HTML)
```html
<!-- Load via Google Fonts CDN -->
<link href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:opsz,wght,FILL,GRAD@20..48,100..700,0..1,-50..200" rel="stylesheet" />
<!-- Usage -->
<span class="material-symbols-outlined" style="font-size: 24px;">search</span>
```
---
## 7. Accessibility
- Always pair icons with a label or `aria-label` when used as interactive controls.
- Decorative icons must have `aria-hidden="true"`.
- Icon-only buttons require a visible tooltip or `title` attribute.
```tsx
/* Decorative */
<Star weight="fill" aria-hidden="true" />
/* Interactive */
<button aria-label="Search">
  <MagnifyingGlassIcon className="w-5 h-5" aria-hidden="true" />
</button>
```
---
## 8. Do / Don't
| ✅ Do | ❌ Don't |
|---|---|
| Use `currentColor` so icons respond to theme changes | Hardcode hex colors on icons |
| Pick one library per component/context | Mix Lucide and Phosphor inside the same card |
| Use size tokens (`--icon-md`) | Use arbitrary px values inline |
| Use Solid Heroicons inside filled buttons | Use Outline Heroicons inside solid-filled CTAs |
| Set `aria-hidden="true"` on decorative icons | Leave decorative icons without aria attributes |
| Use `optical-size` axis on Material Symbols | Render Material Symbols below 20 px without adjusting `opsz` |
---
## 9. Updating This Document
- New icon libraries must be evaluated against: license, style compatibility, bundle size, and accessibility support before being added.
- Any role reassignment must be reviewed with the design lead.
- Tokens defined here should be kept in sync with `tokens/icon-size.css` and `tokens/icon-color.css`.
