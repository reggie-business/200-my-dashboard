# 200-my-dashboard

FastForward Logistics — Executive Operations Dashboard (prototype)

Overview
- Simple Vue 3 + Vite prototype showing an executive dashboard layout for FastForward Logistics.
- Built with TypeScript, Vue Router and Vuetify 3.

Run locally

```bash
npm install
npm run dev  # open http://localhost:5173
```

Build

```bash
npm run build
npm run preview
```

Project structure
- `BRIEF.md` — project brief and run-check list (source of truth for scope and decisions).
- `src/` — app source. Main view is `src/views/HomeView.vue` and reusable `MetricCard` is in `src/components/MetricCard.vue`.

Accessibility & Design
- Colors, spacing, landmarks and keyboard skip link were applied to meet WCAG best practices.

Notes
- This is a prototype for internal use. Replace placeholders (`Chart placeholder`, `Table placeholder`) with real data/components for production.
