# My Element Library
### Personal Collection of High-Fidelity Components, Patterns, and Textures
This directory serves as the personal "vault" of pre-built UI elements. These are not basic components; they are highly stylized, often animated, or uniquely textured elements that can be quickly deployed to Phase 5: Build.
---
## 📂 Library Structure
- `/hero/` — Unique hero section layouts (e.g., Split Screen, Video Background).
- `/cards/` — High-fidelity cards (e.g., Glassmorphic, Neumorphic, Floating Depth).
- `/interactions/` — Specialized CSS/GSAP interactions (e.g., Magnetic Buttons, Marquees).
- `/navigation/` — Advanced nav patterns (e.g., Sidebar drawers, full-screen overlays).
## 🛡️ Gatekeeper Protocol (Curation & Ingestion)
To prevent "Aesthetic Pollution" (patchwork designs that don't match the brand), all external elements from sites like **21st.dev** or **Aceternity** must follow these rules before entry:
1.  **Energy Fit:** Does it clearly support one of the **8 Design Energies**? Tag the component with its energy in the header: `// Energy: Edge, Momentum`.
2.  **Skeletonize:** Strip all hardcoded Tailwind/CSS colors and fonts. Replace them with system tokens (`--color-primary`, `--font-heading`, `var(--duration-md)`).
3.  **Strategy Check:** Elements must serve the **Site Goal** (Phase 2), not just look "cool."
---
## 🚀 Usage in Phase 5
When the **Site Builder Skill** is running:
1.  Check `design_direction.md` to see if `pull from my-element-library? Yes` is checked.
2.  Search this directory for matching patterns (e.g., if a "Story" template is chosen, pull from `/hero/story-scroller.tsx`).
3.  Copy and adapt the component to the project's specific brand colors.
