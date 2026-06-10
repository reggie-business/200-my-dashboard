<template>
  <v-app>
    <router-view />
  </v-app>
</template>

<script setup lang="ts"></script>

<style>
html,
body,
#app {
  margin: 0;
  min-height: 100%;
  font-family: Inter, system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial;
  background: radial-gradient(ellipse at top left, #071022 0%, #0b1224 35%, #061021 100%);
  color: var(--text);
}
body {
  background: radial-gradient(ellipse at top left, #071022 0%, #0b1224 35%, #061021 100%);
}

:root {
  --bg: #071022;
  --card-bg: #0b1224;
  --text: #E6EEF8;
  --muted: #9fb3c8;
  --accent: #ff4fa3;
  --focus: #00e5ff;
  --surface-contrast: rgba(255,255,255,0.06);
  --card-border: rgba(255,255,255,0.06);
  --radius: 12px;
  --base-line-height: 1.45;
  --base-font-size: 16px;
}

.skip-link {
  position: absolute;
  left: -999px;
  top: auto;
  width: 1px;
  height: 1px;
  overflow: hidden;
}
.skip-link:focus {
  left: 1rem;
  top: 1rem;
  width: auto;
  height: auto;
  padding: 0.5rem 1rem;
  background: var(--accent);
  color: var(--bg);
  z-index: 9999;
  border-radius: 4px;
}

/* Accessible reduced motion */
@media (prefers-reduced-motion: reduce) {
  * {
    transition: none !important;
    animation: none !important;
  }
}
</style>
