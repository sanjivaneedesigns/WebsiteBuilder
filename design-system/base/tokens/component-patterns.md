# Component Patterns — Base Design System
### Standardized UI Architecture for Navbars, Cards, and CTAs
This document defines the structural patterns used for core website components. We separate **Structure** (HTML/React-scaffold) from **Aesthetic** (Design Energy tokens) to ensure rapid development without sacrificing original design.
---
## 🧭 1. Navigation Systems
### 1.1 The "Fixed Reveal" Navbar
*Best for: SaaS, Landing Pages.*
- **Structure:** Floating container with `backdrop-filter: blur()`.
- **Behavior:** Hidden on scroll-down; visible on scroll-up (sticky-reveal).
- **Rule:** Max height 72px (MD/LG screens), 64px (SM).
### 1.2 The "Split Nav"
*Best for: Brand Stories, Editorial.*
- **Structure:** Left (Brand), Center (Links), Right (CTA).
- **Behavior:** Transparent background on landing; solid surface on scroll.
---
## 📇 2. Information Containers (Cards)
Every card follows a **Head → Body → Foot** architecture.
| Use Case | Architecture | Best Practice |
|---|---|---|
| **Feature Card** | Icon → H3 → Body Copy | Icons should be --icon-xl (32px) from Lucide. |
| **Testimonial** | Quote → Divider → Avatar + Name | Quotes should use a --font-serif (if available) for "Warmth" or "Craft". |
| **Case Study** | Image (Ratio 16:9) → Title → CTA Link | Image hover should include a subtle scale-up (1.05) over 400ms. |
---
## ⚡ 3. Call-to-Action (CTA) Patterns
### 3.1 The "Hero CTA"
- **Style:** Primary button + secondary button (ghost).
- **Constraint:** Secondary button must not compete with primary in visual weight.
- **Micro-interaction:** Use `var(--ease-back-out)` for hover scaling.
### 3.2 The "Section Banner CTA"
- **Style:** Centered H2 + Paragraph + Primary Button.
- **Constraint:** Use `--color-surface-1` or a brand background color to separate from body content.
---
## 🎨 4. Design Energy Overrides (Section Pass 4)
When implementing these patterns, apply energy-specific styling:
| Energy | Styling Rule |
|---|---|
| **Precision** | Cards use sharp 0px borders. Grids are dense with thin hairline borders. |
| **Warmth** | Cards use soft `border-radius: 12px` or `16px`. Subtle shadows. |
| **Momentum** | Large, bold CTAs. Cards often use skewed/diagonal edges or hover shadows. |
| **Clarity** | Extreme padding within cards (48px+). No borders. |
| **Edge** | Asymmetrical paddings. Brash shadows (solid black, no blur). |
---
## 🛠️ 5. Implementation Reference (React Skeleton)
```tsx
/* Standard Feature Card Pattern */
export const FeatureCard = ({ icon: Icon, title, description }) => (
  <div className="group flex flex-col p-6 border border-border bg-surface-1 transition-all hover:bg-surface-2">
    <div className="mb-4 text-primary">
      <Icon size={32} />
    </div>
    <h3 className="font-heading text-lg font-semibold mb-2">{title}</h3>
    <p className="text-muted-fg leading-relaxed">{description}</p>
    <div className="mt-auto pt-4 group-hover:translate-x-1 transition-transform">
      <ArrowLink label="Learn More" />
    </div>
  </div>
);
```
