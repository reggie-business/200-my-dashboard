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
  font-family: 'Orbitron', system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial;
  background: radial-gradient(ellipse at top left, #0f0326 0%, #1b052f 35%, #120824 100%);
  color: #f3f0ff;
}
body {
  background: radial-gradient(ellipse at top left, #0f0326 0%, #1b052f 35%, #120824 100%);
}

:root {
  --bg: #0f0326;
  --card-bg: #0b0a12;
  --text: #ffffff;
  --muted: #cbd5e1;
  --accent: #ff0080;
  --focus: #00fff0;
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
