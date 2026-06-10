<template>
  <v-main id="main-content" class="dashboard">
    <v-container fluid>
      <v-sheet class="header-sheet mb-10" elevation="2" rounded role="banner" aria-label="Application header">
        <div class="header-content">
          <div>
            <p class="eyebrow">FastForward Logistics</p>
            <h1 class="brand">Executive Operations Dashboard</h1>
          </div>
          <div class="header-meta">
            <p>Last updated: Today</p>
          </div>
        </div>
      </v-sheet>

      <v-row class="metrics-row" dense>
        <v-col cols="12" md="3" v-for="(metric, index) in metrics" :key="metric.label">
          <MetricCard :label="metric.label" :value="metric.value" :note="metric.note" :heading-id="`metric-${index}`" />
        </v-col>
      </v-row>

      <v-row dense>
        <v-col cols="12" md="8">
          <v-card elevation="1" rounded class="section-card" role="region" aria-labelledby="shipment-volume-title">
            <v-card-title id="shipment-volume-title">Shipment Volume</v-card-title>
            <v-card-text>
              <div class="placeholder" aria-hidden="true">Chart placeholder</div>
            </v-card-text>
          </v-card>
        </v-col>
        <v-col cols="12" md="4">
          <v-card elevation="1" rounded class="section-card" role="region" aria-labelledby="open-exceptions-title">
            <v-card-title id="open-exceptions-title">Open Exceptions</v-card-title>
            <v-card-text>
              <div class="placeholder" aria-hidden="true">Table placeholder</div>
            </v-card-text>
          </v-card>
        </v-col>
        <v-col cols="12" md="8">
          <v-card elevation="1" rounded class="section-card" role="region" aria-labelledby="regional-performance-title">
            <v-card-title id="regional-performance-title">Regional Performance</v-card-title>
            <v-card-text>
              <div class="placeholder" aria-hidden="true">Map / summary placeholder</div>
            </v-card-text>
          </v-card>
        </v-col>
        <v-col cols="12" md="4">
          <v-card elevation="1" rounded class="section-card" role="region" aria-labelledby="otd-trend-title">
            <v-card-title id="otd-trend-title">On-Time Delivery Trend</v-card-title>
            <v-card-text>
              <div class="placeholder" aria-hidden="true">Trend chart placeholder</div>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </v-main>
</template>

<script setup lang="ts">
import MetricCard from '../components/MetricCard.vue';

const metrics = [
  { label: 'Shipments Today', value: '1,248', note: '+4.2% vs yesterday' },
  { label: 'On-Time Delivery', value: '92.7%', note: 'Stable week-over-week' },
  { label: 'Regional Exceptions', value: '18', note: '3 new issues' },
  { label: 'Carrier Capacity', value: '78%', note: 'Near target' }
];
</script>

<style scoped>
.dashboard {
  padding: 2rem 1rem;
  min-height: 100vh;
  background: #f4f6fb;
}

.header-sheet {
  padding: 1.75rem;
}

.header-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  gap: 1rem;
}

.eyebrow {
  margin: 0;
  text-transform: uppercase;
  letter-spacing: 0.12em;
  color: var(--muted);
  font-size: 0.85rem;
  font-weight: 600;
}

h1.brand {
  margin: 0.25rem 0 0;
  font-size: 1.9rem;
  line-height: 1.05;
  font-weight: 700;
  color: var(--text);
  font-family: 'Orbitron', Inter, sans-serif;
  text-shadow: 0 1px 3px rgba(2,6,23,0.6);
}

.header-meta {
  color: #5f6d7a;
}

.metrics-row {
  margin-bottom: 1.75rem;
}

.metric-label {
  margin: 0;
  color: var(--muted);
  font-size: 0.95rem;
  font-weight: 600;
}

.metric-value {
  margin: 0.5rem 0 0;
  font-size: 1.9rem;
  font-weight: 700;
  color: var(--text);
}

.metric-note {
  margin: 0.5rem 0 0;
  color: var(--muted);
}

.section-card {
  min-height: 260px;
  background: linear-gradient(180deg, var(--card-bg), rgba(11,18,36,0.92));
  border-radius: var(--radius);
  border: 1px solid var(--card-border);
}
.header-sheet {
  background: linear-gradient(135deg, rgba(255,255,255,0.01), rgba(255,255,255,0.01));
  border: 1px solid var(--card-border);
}

.v-card.section-card {
  background: linear-gradient(180deg, var(--card-bg), rgba(11,18,36,0.92));
  border: 1px solid var(--card-border);
  box-shadow: 0 6px 20px rgba(2,6,23,0.4);
}

.header-meta {
  color: var(--muted);
}
.placeholder {
  min-height: 200px;
  border-radius: 0.5rem;
  background: rgba(255,255,255,0.02);
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--muted);
  font-weight: 600;
}

@media (max-width: 960px) {
  .dashboard {
    padding: 1rem;
  }
}
</style>
