---
description: Run the end-to-end Antigravity Website Design Workflow (/website-designer) with Framer MCP Export
---
This workflow guides the agent through the complete design and build process: **Audit → Research → Strategy → Structure → Visuals → Local Build (Pass 1-2) → Framer Export (Pass 3) → Deployment.**
### Phase 1: Initialization & Audit
1. **Directory Isolation:** Create a new folder for the project: `/projects/[brand-name]/`.
2. **Master Brief:** Initialize the `[brand-name]_master_brief.md` as an **Assistant Artifact** (IsArtifact: true).
3. **Brand & Content Audit:** Use **Firecrawl MCP** or **Apify MCP** to crawl the existing site's main pages.
4. **Synthesis:** Document core content mapping, positioning, and narrative in the Master Brief.
5. **PAUSE:** Wait for user approval of the Audit stage.
### Phase 2: Behavioral Research
1. Identify 5 competitors (Global Aspirational, Direct, Local/Better Rated, Domain Best, Country Best).
2. Use **Firecrawl MCP** to extract Hero, CTA, Narrative, and Visual Tone signals from competitor sites.
3. Synthesize a "Forced Decision" for differentiation in the Master Brief.
4. **PAUSE:** Wait for user approval of the Research Brief.
### Phase 3: Strategy & Blueprinting
1. Define the Site Goal (Lead Gen, Brand, etc.).
2. Lock the Positioning, Audience, and Messaging Pillars.
3. Map Design Tenets to the narrative.
4. Select a Structural Template (Authority, Product, etc.) and map Audit content to sections in the `site_blueprint.md`.
5. **PAUSE:** Wait for user approval of the Strategy & Blueprint.
### Phase 4: Visual Direction
1. Intersect 2 Design Energies (e.g., Precision × Warmth).
2. Define the Expressive Layer (Typography, Color, Motion, Spacing, or Imagery).
3. Pre-fill and edit the Design Direction Form.
4. Generate 3 reference images for visual anchoring in the Master Brief.
5. **PAUSE:** Wait for user approval of the Design Direction.
### Phase 5: The Build + Framer Export
**Pass 1 — Skeleton (Local Build):**
- Scaffold project in `/projects/[brand-name]/`.
- Build sections in order using semantic HTML.
- Apply structure and repackaged copy (locked). No color/motion yet.
- **Gate Review.**
**Pass 2 — Fidelity (Local Build):**
- Apply CSS/React tokens for the energy intersection defined.
- Apply design tokens, colors, fonts from the Design Direction.
- Generate/source assets. Ensure High-Contrast CTAs.
- **Gate Review.**
**Pass 3 — Framer Migration:**
- Use **Framer MCP** to recreate the Pass 1 + Pass 2 build in Framer.
- Transfer all design tokens, components, and content to Framer.
- Apply motion profiles and micro-interactions within Framer.
- Ensure responsive behavior across breakpoints (375px, 768px, 1280px, 1440px).
- **PAUSE** for final sign-off on the Framer design.
### Phase 6: Final Review & Deploy
1. User performs manual review of the Framer build.
2. Publish the Framer site directly, or export code and push to **GitHub MCP** for deployment to Vercel/Netlify.
