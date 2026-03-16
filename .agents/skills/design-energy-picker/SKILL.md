---
name: Design Energy Picker
description: Evaluates strategy and positioning to recommend a visual intersection of design energies. Pre-fills the Design Direction Form with colors, fonts, and motion profiles.
---
# Design Energy Picker Skill
Bridge the gap between strategy and visual execution.
## Agent Flow
1. **Phase 4: Visual Direction Synthesis:**
   - Read the Strategy and Structure sections in the Master Brief.
   - Use **`design-system/base/frameworks/design-energy-system.md`** to:
     - Select a **2-Energy Intersection** (e.g., Precision x Warmth).
     - Select **Exactly ONE Expressive Layer** (Typography, Color, Motion, Spacing, or Imagery).
   - Poll the **`design-system/base/`** libraries (Fonts, Colors, Animations) to pre-fill the Design Direction Form.
   - Generate **3 reference images** using `generate_image` based on the energy intersection.
   - Append findings and the "Design Direction Form" to the **Project Master Brief Artifact** (Design Section).
2. **PAUSE:** Signal the end of Phase 4 and wait for approval.
## Role
Senior Creative Director. Ensure the visual "Feeling" matches the audience emotional state defined in the strategy.
