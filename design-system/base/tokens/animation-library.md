# Animation Library — Base Design System
### Easing Curves, Duration Scales, and Trigger Systems
This document defines the motion language for all Antigravity projects. Motion is not an afterthought; it is a structural element used to guide focus, communicate hierarchy, and create a premium, "living" interface.
---
## ⏳ 1. Duration Scale (ms)
Use these tokens to maintain a consistent "tempo" across the application.
| Token | Duration | Use Case |
|---|---|---|
| `--duration-instant` | 50ms | Subtle hover state flickers |
| `--duration-fast` | 150ms | Button state changes, tooltips, checkboxes |
| `--duration-standard` | 300ms | Modals, dropdowns, page transitions |
| `--duration-slow` | 500ms | Large section entrances, image reveals |
| `--duration-hero` | 1000ms+ | Cinematic hero sequencing, complex GSAP timelines |
---
## 🌊 2. Easing Curves (The "Feel")
Easings define the personality of the motion. Avoid browser defaults (`ease-in-out`).
### 📐 Precision & Technical (Linear-leaning)
*Best for: Dashboards, data-rich UIs.*
- **Out:** `cubic-bezier(0, 0, 0, 1)` (Quart Out) — Sharp, mechanical stop.
- **In-Out:** `cubic-bezier(0.4, 0, 0.2, 1)` (Standard) — Clean and predictable.
### 🎭 Cinematic & Fluid (Dramatic)
*Best for: Landing pages, brand stories.*
- **Fluid Out:** `cubic-bezier(0.25, 1, 0.5, 1)` (Circ Out) — Fast start, very long smooth finish.
- **Exposure:** `cubic-bezier(0.7, 0, 0.3, 1)` (Expo In-Out) — High-drama, slow-fast-slow.
### 🎾 Bouncy & Playful (Elastic)
*Best for: Mobile menus, CTAs, success states.*
- **Soft Back:** `cubic-bezier(0.34, 1.56, 0.64, 1)` — Subtle overshoot.
- **Snappy:** `cubic-bezier(0.175, 0.885, 0.32, 1.275)` — Energetic pop.
---
## ⚡ 3. Animation Triggers
Animations should only fire when intentional.
| Type | Implementation | Best Practice |
|---|---|---|
| **Entrance (On-View)** | Intersection Observer / GSAP ScrollTrigger | Use `--duration-slow` with a stagger for list items. |
| **Micro-Interaction** | `:hover`, `:active`, `:focus` | Keep it under 150ms. Use "Soft Back" for a premium feel. |
| **Implicit State** | React Transition Group / Keyframes | Use for mounting/unmounting components (sidebar, modals). |
| **Scroll-Driven** | GSAP `scrub: true` | Map properties (opacity, scale, y) directly to scroll progress. |
---
## 🧩 4. Motion Guidelines by "Design Energy"
When building in Phase 5, map your motion to the selected **Design Energy**:
| Energy | Motion Profile |
|---|---|
| **Precision** | Fast, linear-leaning eases. Stagger items from top-left to bottom-right. No overshoot. |
| **Warmth** | Slower durations. Soft fades and "Fluid Out" eases. Y-axis shifts are small (8-16px). |
| **Momentum** | Fast, "Expo" eases. High-contrast motion (large scale changes or X-axis slides). |
| **Depth** | Layered parallax. Stagger items based on their Z-index (visual depth). |
| **Edge** | Asymmetrical staggers. Unexpected easing curves (e.g., fast deceleration). |
| **Craft** | "Human" timing. Subtle imperfections or slightly offset starts for grouped elements. |
---
## 🛠️ 5. Implementation Example (CSS Tokens)
```css
/* tokens/animation.css */
:root {
  /* Durations */
  --duration-fast: 150ms;
  --duration-std: 300ms;
  --duration-slow: 500ms;
  /* Easings */
  --ease-out-quart: cubic-bezier(0.25, 1, 0.5, 1);
  --ease-in-out-expo: cubic-bezier(0.7, 0, 0.3, 1);
  --ease-back-out: cubic-bezier(0.34, 1.56, 0.64, 1);
}
.card-entrance {
  opacity: 0;
  transform: translateY(20px);
  transition:
    opacity var(--duration-slow) var(--ease-out-quart),
    transform var(--duration-slow) var(--ease-out-quart);
}
.card-entrance.is-visible {
  opacity: 1;
  transform: translateY(0);
}
```
