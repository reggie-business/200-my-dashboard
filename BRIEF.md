# FastForward Logistics - Executive Dashboard

## Background
I just got on a contract with FastForward Logistics.

FastForward (or "FF") is a mid-size freight and supply chain company. Their ops team is drowning in spreadsheets. The VP of Operations wants a single internal dashboard she can pull up in leadership meetings to see how the business is running: shipment volume, on-time delivery rates, regional performance, and open exceptions. They have no in-house dev team, and that's why I'm here.

I need to scope, plan, and build a working prototype. My objectives include:

- Apply structured planning practices to scope build
- Use component-based framework
- Use AI-assisted workflow from plan to working prototype. I am the reviewer and decision-maker. Keep the initial build simple, then ask me about design choices and functionality.

## Step 1: Set up Vue
Scaffold a new Vue project using Vite with TypeScript and Vue Router. Run the commands in the terminal.

- I need a header, a layout grid, and placeholder sections for cards and charts. 
- No pinia, testing, jsx, eslint, or prettifier.
- Do not scaffold within a subfolder.f
- Commit as "Scaffold Vue Project"

## Step 2: Begin Build
- Start the dev server.
- Replace Vue starter content with FastForward dashboard layout shell.
- Commit as "Add dashboard shell"

## Step 3: Add Component Library
Add Vuetify 3 to the project. Install the package, set up plugin in main.ts, and import styles and icons.

- Refactor dashboard shell using Vuetify components (i.e., an app bar for the header, cards for metric tiles, grid for overall layout)


## Step 4: Build Custom Component
Extract metric card into a reusable custom component called MetricCard with props for variable parts (eg., label, value, trend direction).

- Commit as "Built custom component"

## Run Check
- Site is live and accessible
- Core flow works end to end
- Reflects brief
- Working interactive elements
- No key flows are broken
- All edge cases and empty states handled with grace
- Experience works well across screen sizes
- AI scaffolding is present and organized: context docs in logical place, not scattered
- README.md included in root
- LICENSE included in root
- Context docs show updates across multiple sessions
- Dashboard looks and feels like internal ops tool - layout, data, and tone match brief
- First-time users should be able to orient themselves without help. BRIEF.md is present and connects to what was actually built. It is a plan, not a description.
- Design decisions are evident and intentional - hierarchy, spacing, and data presentation are considered.