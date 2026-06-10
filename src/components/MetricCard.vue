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
}
.metric-label {
  margin: 0;
  color: #6b7280;
  font-size: 0.95rem;
}
.metric-value {
  margin: 0.75rem 0 0;
  font-size: 2rem;
  font-weight: 700;
}
.metric-note {
  margin: 0.75rem 0 0;
  color: #475569;
}
</style>
