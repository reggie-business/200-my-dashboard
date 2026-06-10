<template>
  <section
    class="metric-card"
    role="region"
    :aria-labelledby="headingId"
    tabindex="0"
  >
    <v-card elevation="0" flat>
      <v-card-text>
        <h3 :id="headingId" class="metric-label">{{ label }}</h3>
        <p class="metric-value">{{ value }}</p>
        <p v-if="note" class="metric-note">{{ note }}</p>
      </v-card-text>
    </v-card>
  </section>
</template>

<script setup lang="ts">
const props = defineProps<{
  label: string;
  value: string;
  note?: string;
  headingId?: string;
}>();

const { label, value, note, headingId = `metric-${Math.random().toString(36).substr(2,6)}` } = props;
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
