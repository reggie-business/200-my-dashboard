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
  background: linear-gradient(180deg, #1c2028 0%, #151922 100%);
  border: 1px solid #2d3442;
  border-radius: calc(var(--radius) - 4px);
  box-shadow: 0 6px 18px rgba(17, 26, 43, 0.2);
}

.metric-card :deep(.v-card) {
  background: transparent;
  color: #f7fbff;
}
.metric-label {
  margin: 0;
  color: #c7d3e8;
  font-size: 0.9rem;
  letter-spacing: 0.03em;
  font-weight: 600;
}
.metric-value {
  margin: 0.5rem 0 0;
  font-size: 1.75rem;
  font-weight: 700;
  color: #f7fbff;
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
  color: #d3ddef;
  font-size: 0.88rem;
}

.metric-empty {
  margin: 0.5rem 0 0;
  color: #d3ddef;
  font-size: 0.84rem;
}

.metric-card:focus-visible {
  outline: 3px solid #1565c0;
  outline-offset: 3px;
}
</style>
