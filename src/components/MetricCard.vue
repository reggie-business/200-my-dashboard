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
        <div class="metric-trend" v-if="trendText">
          <v-icon
            :icon="trendIcon"
            :color="trendColor"
            size="18"
            class="metric-trend-icon"
            aria-hidden="true"
          />
          <p class="metric-note">{{ trendText }}</p>
        </div>
        <p v-else class="metric-empty">No trend data available</p>
      </v-card-text>
    </v-card>
  </section>
</template>

<script setup lang="ts">
import { computed } from 'vue';

const props = defineProps<{
  label: string;
  value: string;
  trendValue?: string;
  trendDirection?: 'up' | 'down' | 'flat';
  headingId?: string;
}>();

const {
  label,
  value,
  trendValue,
  trendDirection = 'flat',
  headingId = `metric-${Math.random().toString(36).slice(2, 8)}`
} = props;

const trendText = computed(() => {
  if (!trendValue) return '';

  if (trendDirection === 'up') return `${trendValue} increase`;
  if (trendDirection === 'down') return `${trendValue} decrease`;
  return `${trendValue} unchanged`;
});

const trendColor = computed(() => {
  if (trendDirection === 'up') return 'success';
  if (trendDirection === 'down') return 'error';
  return 'info';
});

const trendIcon = computed(() => {
  if (trendDirection === 'up') return 'mdi-arrow-up-thin';
  if (trendDirection === 'down') return 'mdi-arrow-down-thin';
  return 'mdi-arrow-right-thin';
});
</script>

<style scoped>
.metric-card {
  padding: 0;
  background: #ffffff;
  border: 1px solid #dde5ee;
  border-radius: calc(var(--radius) - 4px);
  box-shadow: 0 4px 14px rgba(17, 26, 43, 0.08);
}
.metric-label {
  margin: 0;
  color: #5a6880;
  font-size: 0.9rem;
  letter-spacing: 0.03em;
  font-weight: 600;
}
.metric-value {
  margin: 0.5rem 0 0;
  font-size: 1.75rem;
  font-weight: 700;
  color: #0d223d;
  font-family: 'IBM Plex Sans', 'Segoe UI', sans-serif;
}

.metric-trend {
  margin-top: 0.5rem;
  display: flex;
  align-items: center;
  gap: 0.25rem;
}
.metric-note {
  margin: 0;
  color: #5a6880;
  font-size: 0.88rem;
}

.metric-empty {
  margin: 0.5rem 0 0;
  color: #7c8aa0;
  font-size: 0.84rem;
}

.metric-card:focus-visible {
  outline: 3px solid #1565c0;
  outline-offset: 3px;
}
</style>
