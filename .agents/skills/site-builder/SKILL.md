---
name: Site Builder
description: Builds locally (Pass 1-2), then migrates to Framer (Pass 3) using Framer MCP. Reads configuration from the Master Brief.
---
# Site Builder Skill
The execution engine. No aesthetic opinions.
## Agent Flow
1. **Pass 1: Skeleton (Local Build - Structure + Repackaged Copy):**
   - Read the **Structure** and **Strategy** sections in the Master Brief.
   - Scaffold the project in `/projects/[brand-name]/`.
   - Build sections in order using semantic HTML.
   - **Enforce Conversion Standards:** Apply **`design-system/base/frameworks/conversion-strategy.md`** (Writing & UX Standards). No Jargon. No Happy Talk.
   - PAUSE for review.
2. **Pass 2: Fidelity (Local Build - The Skin):**
   - Read the **Design** section in the Master Brief.
   - Apply CSS/React tokens for the energy intersection defined.
   - **Enforce Energy Hierarchy:** Apply **`design-system/base/frameworks/design-energy-system.md`** (Expressive Layer rule).
   - Generate/source assets. Ensure **High-Contrast CTAs** (Conversion Rule).
   - PAUSE for review.
3. **Pass 3: Framer Migration (The Soul):**
   - Use **Framer MCP** to recreate the Pass 1 + Pass 2 local build in Framer.
   - Transfer all:
     - HTML structure → Framer components
     - CSS tokens → Framer variables
     - Design system (colors, fonts, spacing) → Framer styles
     - Content and copy → Framer text layers
   - Apply the motion profile from the Design Direction within Framer.
   - Add scroll triggers and micro-interactions using Framer's native animation tools.
   - Ensure responsive breakpoints match the design system (375px, 768px, 1280px, 1440px).
   - **PAUSE** for final sign-off.
## Role
Lead Frontend Engineer and Framer Specialist. Strictly execute the specs provided in the Master Brief. Technical excellence and pixel-perfection are the only priorities.
