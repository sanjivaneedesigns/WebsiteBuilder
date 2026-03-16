---
name: QA Checklist Skill
description: Runs the full pre-launch checklist automatically via browser_subagent, flags failures with fixes. Output a pass/fail report with recommended fixes.
---
# QA Checklist Skill
Ensure the website is technically sound, high-performing, accessible, and conversion-optimized before it goes live. This skill acts as the final gatekeeper, using a rigorous automated and manual-emulated audit process.
## Role
Act as a **Senior QA Engineer and Performance Specialist**. Your job is to break the site—or try to. You check for technical hygiene, responsiveness across devices, accessibility compliance, and conversion clarity. You don't just find bugs; you provide the exact code or layout fix needed to resolve them.
---
## Agent Flow — MUST FOLLOW
When this skill is invoked, follow this sequence:
### Step 1: Automated Technical & Performance Audit
If the site is running locally or deployed, use the `browser_subagent` to run a Lighthouse audit (or emulate its checks). Focus on:
- **Lighthouse Scores:** Aim for ≥ 90 in Performance, Accessibility, Best Practices, and SEO.
- **Asset Optimization:** Verify images are WebP and lazy-loaded. Check font loading strategies (font-display: swap).
- **Console Hygiene:** Check for any errors or broken resource links.
### Step 2: Visual & Responsive Verification
Use the `browser_subagent` to view the site at four critical breakpoints:
1. **Mobile:** 375px
2. **Tablet:** 768px
3. **Laptop:** 1280px
4. **Desktop:** 1440px
Flag any overflow issues, layout shifts (CLS), or unreadable text.
### Step 3: Accessibility & Interaction Audit
Perform a structural check for:
- **Contrast:** Ensure text contrast is at least 4.5:1.
- **Alt Text:** Verify every image has descriptive alt text.
- **Keyboard Nav:** Can you navigate the entire site and trigger all CTAs using only the `tab` and `enter` keys?
- **Forms:** If forms exist, ensure they have proper labels and clear success/error states.
### Step 4: Conversion & Copy Validation
Compare the rendered site against `strategy_brief.md` and `site_blueprint.md`:
- **Above the Fold:** Is the primary CTA visible immediately?
- **CTA Clarity:** Is the CTA text outcome-oriented (e.g., "Get the Guide" vs "Submit")?
- **Friction:** Are there competing CTAs in the same viewport that dilute the primary action?
---
## Output — `qa_report.md`
Every run must produce a `qa_report.md` containing:
1. **Overall Status:** RED (Critical Bugs), AMBER (Needs Improvement), or GREEN (Ready for Launch).
2. **Category Scores:**
   - **Performance:** [Score/Pass]
   - **Responsiveness:** [Score/Pass]
   - **Accessibility:** [Score/Pass]
   - **Conversion:** [Score/Pass]
   - **Technical:** [Score/Pass]
3. **Detailed Failures & Fixes:** For every failed check, provide:
   - **The Issue:** What is wrong and where.
   - **The Fix:** The specific CSS/HTML/Config change required to fix it.
4. **Final Recommendation:** "Proceed to Deploy" or "Hold for Fixes."
---
## Resource Files
| File | Purpose |
|------|---------|
| `resources/checklist-specs.md` | Detailed success criteria for every check item |
| `resources/fix-library.md` | Common fixes for Lighthouse, layout shifts, and accessibility issues |
| `resources/browser-test-plan.md` | Specific prompts and steps for the `browser_subagent` to follow |
