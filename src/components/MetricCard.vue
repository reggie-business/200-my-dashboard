<template>
  <v-card elevation="1" rounded class="metric-card">
    <v-card-text>
      <p class="metric-label">{{ label }}</p>
      <p class="metric-value">{{ value }}</p>
      <p v-if="note" class="metric-note">{{ note }}</p>
    </v-card-text>
  </v-card>
</template>

<script setup lang="ts">
const props = defineProps<{
  label: string;
  value: string;
  note?: string;
}>();

const { label, value, note } = props;
</script>

<style scoped>
.metric-card {
  padding: 1rem;
  background: linear-gradient(180deg, rgba(255,255,255,0.03), rgba(255,255,255,0.01));
  border: 1px solid rgba(255,0,150,0.12);
  box-shadow: 0 6px 20px rgba(255,0,150,0.06), 0 0 18px rgba(0,200,255,0.04) inset;
}
.metric-label {
  margin: 0;
  color: #f3eaff;
  font-size: 0.95rem;
  letter-spacing: 0.06em;
}
.metric-value {
  margin: 0.5rem 0 0;
  font-size: 2.1rem;
  font-weight: 800;
  color: #fff;
  text-shadow: 0 2px 8px rgba(255,0,150,0.12);
  font-family: 'Metal Mania', 'Orbitron', sans-serif;
}
.metric-note {
  margin: 0.5rem 0 0;
  color: #cbd5e1;
  font-size: 0.85rem;
}
</style>
