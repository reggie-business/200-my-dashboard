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
  background: #f4f6fb;
}
</style>
