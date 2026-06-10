<template>
  <v-main id="main-content" class="dashboard">
    <v-container fluid>
      <v-sheet class="header-sheet mb-10" elevation="2" rounded role="banner" aria-label="Application header">
        <div class="header-content">
          <div>
            <p class="eyebrow">FastForward Logistics</p>
            <h1 class="chrome">Executive Operations Dashboard</h1>
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
  letter-spacing: 0.18em;
  color: #55607b;
  font-size: 0.85rem;
}

h1 {
  margin: 0.35rem 0 0;
  font-size: 2.2rem;
  font-weight: 700;
}

.chrome {
  font-family: 'Metal Mania', 'Orbitron', sans-serif;
  font-weight: 700;
  font-size: 2.6rem;
  background: linear-gradient(90deg, #fff, #ffd700, #ff0080, #7efff5);
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
  text-shadow: 0 2px 6px rgba(0,0,0,0.6), 0 0 12px rgba(255,0,150,0.35);
}

.header-meta {
  color: #5f6d7a;
}

.metrics-row {
  margin-bottom: 1.75rem;
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

.section-card {
  min-height: 280px;
}
.header-sheet {
  background: linear-gradient(135deg, rgba(255,0,150,0.08), rgba(0,200,255,0.06));
  border: 1px solid rgba(255,255,255,0.04);
}

.v-card.section-card {
  background: linear-gradient(180deg, rgba(20,8,40,0.6), rgba(10,6,25,0.6));
  border: 1px solid rgba(126,0,255,0.12);
  box-shadow: 0 6px 30px rgba(126,0,255,0.08);
}

.header-meta {
  color: #cbd5e1;
}
.placeholder {
  min-height: 220px;
  border-radius: 0.75rem;
  background: #eef2ff;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #4338ca;
  font-weight: 600;
}

@media (max-width: 960px) {
  .dashboard {
    padding: 1rem;
  }
}
</style>
