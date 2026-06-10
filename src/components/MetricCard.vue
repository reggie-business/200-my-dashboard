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
  background: linear-gradient(180deg, var(--card-bg), rgba(11,18,36,0.92));
  border: 1px solid var(--card-border);
  border-radius: calc(var(--radius) - 4px);
  box-shadow: 0 6px 18px rgba(2,6,23,0.35);
}
.metric-label {
  margin: 0;
  color: var(--muted);
  font-size: 0.95rem;
  letter-spacing: 0.04em;
}
.metric-value {
  margin: 0.5rem 0 0;
  font-size: 1.9rem;
  font-weight: 700;
  color: var(--text);
  text-shadow: none;
  font-family: Inter, 'Orbitron', sans-serif;
}
.metric-note {
  margin: 0.5rem 0 0;
  color: var(--muted);
  font-size: 0.88rem;
}

.metric-card:focus-visible {
  outline: 3px solid var(--focus);
  outline-offset: 3px;
}
</style>
