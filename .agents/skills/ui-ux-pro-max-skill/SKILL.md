---
name: UI/UX Pro Max
description: AI-powered design intelligence toolkit providing searchable databases of UI styles, color palettes, font pairings, chart types, and UX guidelines for building professional web interfaces.
---
# UI/UX Pro Max Skill
AI-powered design intelligence toolkit providing searchable databases of UI styles, color palettes, font pairings, chart types, and UX guidelines. Use this skill whenever designing or building any web UI.
## Prerequisites
Python 3.x (no external dependencies required).
## How to Use
### Step 1: Analyze User Requirements
Extract from user request:
- **Product type**: SaaS, e-commerce, portfolio, dashboard, landing page, etc.
- **Style keywords**: minimal, playful, professional, elegant, dark mode, etc.
- **Industry**: healthcare, fintech, gaming, education, etc.
- **Stack**: React, Vue, Next.js, or default to `html-tailwind`
### Step 2: Generate Design System (REQUIRED)
Always start with `--design-system` to get comprehensive recommendations:
```bash
python3 src/ui-ux-pro-max/scripts/search.py "<product_type> <industry> <keywords>" --design-system [-p "Project Name"]
```
**Example:**
```bash
python3 src/ui-ux-pro-max/scripts/search.py "beauty spa wellness service" --design-system -p "Serenity Spa"
```
### Step 3: Supplement with Detailed Searches (as needed)
```bash
python3 src/ui-ux-pro-max/scripts/search.py "<keyword>" --domain <domain> [-n <max_results>]
```
Available domains: `product`, `style`, `typography`, `color`, `landing`, `chart`, `ux`, `react`, `web`, `prompt`
### Step 4: Stack Guidelines
```bash
python3 src/ui-ux-pro-max/scripts/search.py "<keyword>" --stack html-tailwind
```
Available stacks: `html-tailwind`, `react`, `nextjs`, `vue`, `svelte`, `swiftui`, `react-native`, `flutter`, `shadcn`, `jetpack-compose`
## Common Rules for Professional UI
- **No emoji icons** — Use SVG icons (Heroicons, Lucide, Simple Icons)
- **Cursor pointer** on all clickable elements
- **Smooth transitions** — 150-300ms duration
- **Proper contrast** — 4.5:1 minimum for text
- **Responsive** — Test at 375px, 768px, 1024px, 1440px
