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
  font-family: 'IBM Plex Sans', 'Segoe UI', Tahoma, sans-serif;
  background: #f3f6fb;
  color: var(--text);
}
body {
  background: #f3f6fb;
}

:root {
  --bg: #f3f6fb;
  --card-bg: #ffffff;
  --text: #102743;
  --muted: #5f6f88;
  --accent: #1565c0;
  --focus: #1565c0;
  --on-dark-text: #f8fbff;
  --surface-contrast: rgba(16, 39, 67, 0.06);
  --card-border: #dbe3ee;
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
  color: #ffffff;
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
