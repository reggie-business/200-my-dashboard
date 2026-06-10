<template>
  <v-layout class="dashboard-layout">
    <v-app-bar elevation="1" height="72" color="white" class="dashboard-bar" role="banner">
      <v-container class="bar-content">
        <div>
          <p class="eyebrow">FastForward Logistics</p>
          <h1 class="brand">Executive Operations Dashboard</h1>
        </div>
        <div class="bar-actions">
          <span class="last-updated">Last updated: {{ updatedAt }}</span>
          <v-btn size="small" variant="outlined" color="primary" prepend-icon="mdi-refresh" @click="refreshSnapshot">
            Refresh Snapshot
          </v-btn>
        </div>
      </v-container>
    </v-app-bar>

    <v-main id="main-content" class="dashboard-main">
      <v-container fluid class="py-6">
        <v-row class="metrics-row" dense>
          <v-col cols="12" sm="6" lg="3" v-for="(metric, index) in metrics" :key="metric.label">
            <MetricCard
              :label="metric.label"
              :value="metric.value"
              :trend-value="metric.trendValue"
              :trend-direction="metric.trendDirection"
              :heading-id="`metric-${index}`"
            />
          </v-col>
        </v-row>

        <v-row dense>
          <v-col cols="12" lg="8">
            <v-card class="section-card" role="region" aria-labelledby="shipment-volume-title">
              <v-card-title id="shipment-volume-title" class="section-title">Shipment Volume</v-card-title>
              <v-card-text>
                <div class="placeholder-block" aria-hidden="true">
                  <div class="bar" v-for="value in shipmentBars" :key="value" :style="{ width: `${value}%` }"></div>
                </div>
              </v-card-text>
            </v-card>
          </v-col>

          <v-col cols="12" lg="4">
            <v-card class="section-card" role="region" aria-labelledby="open-exceptions-title">
              <v-card-title id="open-exceptions-title" class="section-title">Open Exceptions</v-card-title>
              <v-card-text>
                <template v-if="exceptions.length">
                  <v-list class="exception-list" density="compact">
                    <v-list-item v-for="item in exceptions" :key="item.id" :subtitle="item.owner">
                      <template #prepend>
                        <v-icon color="warning" icon="mdi-alert-circle-outline" />
                      </template>
                      <v-list-item-title>{{ item.summary }}</v-list-item-title>
                    </v-list-item>
                  </v-list>
                </template>
                <div v-else class="empty-state">No active exceptions. Operations are running clean.</div>
              </v-card-text>
            </v-card>
          </v-col>

          <v-col cols="12" lg="8">
            <v-card class="section-card" role="region" aria-labelledby="regional-performance-title">
              <v-card-title id="regional-performance-title" class="section-title">Regional Performance</v-card-title>
              <v-card-text>
                <v-table density="compact" class="region-table">
                  <thead>
                    <tr>
                      <th>Region</th>
                      <th>On-time</th>
                      <th>Shipments</th>
                    </tr>
                  </thead>
                  <tbody>
                    <tr v-for="region in regions" :key="region.name">
                      <td>{{ region.name }}</td>
                      <td>{{ region.onTime }}</td>
                      <td>{{ region.shipments }}</td>
                    </tr>
                  </tbody>
                </v-table>
              </v-card-text>
            </v-card>
          </v-col>

          <v-col cols="12" lg="4">
            <v-card class="section-card" role="region" aria-labelledby="otd-trend-title">
              <v-card-title id="otd-trend-title" class="section-title">On-Time Delivery Trend</v-card-title>
              <v-card-text>
                <v-btn-toggle v-model="trendWindow" mandatory color="primary" density="compact" class="mb-4">
                  <v-btn value="7d">7D</v-btn>
                  <v-btn value="30d">30D</v-btn>
                  <v-btn value="90d">90D</v-btn>
                </v-btn-toggle>
                <div class="trend-text">Current window: {{ trendWindow.toUpperCase() }} average at {{ trendAverage }}</div>
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-layout>
</template>

<script setup lang="ts">
import { computed, ref } from 'vue';
import MetricCard from '../components/MetricCard.vue';

const metrics = [
  { label: 'Shipments Today', value: '1,248', trendValue: '4.2%', trendDirection: 'up' as const },
  { label: 'On-Time Delivery', value: '92.7%', trendValue: '0.3%', trendDirection: 'down' as const },
  { label: 'Regional Exceptions', value: '18', trendValue: '3', trendDirection: 'up' as const },
  { label: 'Carrier Capacity', value: '78%', trendValue: 'steady', trendDirection: 'flat' as const }
];

const regions = [
  { name: 'Northeast', onTime: '94.1%', shipments: 284 },
  { name: 'Midwest', onTime: '91.3%', shipments: 336 },
  { name: 'South', onTime: '93.0%', shipments: 402 },
  { name: 'West', onTime: '92.4%', shipments: 226 }
];

const exceptions = ref([
  { id: 1, summary: 'Late unload - Dallas DC', owner: 'Owner: Dispatch' },
  { id: 2, summary: 'Customs hold - Vancouver lane', owner: 'Owner: International Ops' },
  { id: 3, summary: 'Temperature alert - Pharma route', owner: 'Owner: QA Ops' }
]);

const shipmentBars = [92, 78, 88, 66, 74, 95, 83];
const trendWindow = ref<'7d' | '30d' | '90d'>('30d');
const updatedAt = ref('Today');

const trendAverage = computed(() => {
  if (trendWindow.value === '7d') return '93.4%';
  if (trendWindow.value === '30d') return '92.7%';
  return '92.1%';
});

const refreshSnapshot = () => {
  updatedAt.value = new Date().toLocaleTimeString([], { hour: '2-digit', minute: '2-digit' });
};
</script>

<style scoped>
.dashboard-layout {
  min-height: 100vh;
  background: #f3f6fb;
}

.dashboard-bar {
  border-bottom: 1px solid #e0e6f0;
}

.bar-content {
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 1rem;
}

.eyebrow {
  margin: 0;
  text-transform: uppercase;
  letter-spacing: 0.11em;
  color: #5f6f88;
  font-size: 0.78rem;
  font-weight: 600;
}

h1.brand {
  margin: 0.25rem 0 0;
  font-size: 1.5rem;
  line-height: 1.1;
  font-weight: 700;
  color: #11253f;
  font-family: 'IBM Plex Sans', 'Segoe UI', sans-serif;
}

.bar-actions {
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.last-updated {
  color: #5f6f88;
  font-size: 0.9rem;
}

.metrics-row {
  margin-bottom: 1rem;
}

.section-card {
  min-height: 250px;
  border-radius: var(--radius);
  border: 1px solid #dbe3ee;
  box-shadow: 0 6px 18px rgba(17, 26, 43, 0.08);
}

.section-title {
  color: #102743;
  font-weight: 700;
  font-size: 1rem;
}

.placeholder-block {
  min-height: 200px;
  border-radius: 10px;
  background: linear-gradient(180deg, #f8fbff 0%, #edf3fc 100%);
  border: 1px solid #e1e9f4;
  display: flex;
  flex-direction: column;
  justify-content: center;
  gap: 8px;
  padding: 18px;
}

.bar {
  height: 12px;
  border-radius: 8px;
  background: linear-gradient(90deg, #1565c0 0%, #1e88e5 100%);
}

.exception-list {
  background: transparent;
}

.empty-state {
  min-height: 120px;
  border: 1px dashed #c8d5e7;
  border-radius: 8px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #6c7e96;
  font-size: 0.9rem;
}

.region-table {
  border: 1px solid #e3eaf5;
  border-radius: 8px;
}

.trend-text {
  color: #4c5e79;
  font-size: 0.92rem;
}

@media (max-width: 960px) {
  .bar-content {
    align-items: flex-start;
    flex-direction: column;
  }

  .bar-actions {
    width: 100%;
    justify-content: space-between;
  }
}
</style>
