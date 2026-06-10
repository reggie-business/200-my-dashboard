<template>
  <v-main class="dashboard">
    <v-container fluid>
      <v-sheet class="header-sheet mb-10" elevation="2" rounded>
        <div class="header-content">
          <div>
            <p class="eyebrow">FastForward Logistics</p>
            <h1>Executive Operations Dashboard</h1>
          </div>
          <div class="header-meta">
            <p>Last updated: Today</p>
          </div>
        </div>
      </v-sheet>

      <v-row class="metrics-row" dense>
        <v-col cols="12" md="3" v-for="metric in metrics" :key="metric.label">
          <v-card elevation="1" rounded>
            <v-card-text>
              <p class="metric-label">{{ metric.label }}</p>
              <p class="metric-value">{{ metric.value }}</p>
              <p class="metric-note">{{ metric.note }}</p>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>

      <v-row dense>
        <v-col cols="12" md="8">
          <v-card elevation="1" rounded class="section-card">
            <v-card-title>Shipment Volume</v-card-title>
            <v-card-text>
              <div class="placeholder">Chart placeholder</div>
            </v-card-text>
          </v-card>
        </v-col>
        <v-col cols="12" md="4">
          <v-card elevation="1" rounded class="section-card">
            <v-card-title>Open Exceptions</v-card-title>
            <v-card-text>
              <div class="placeholder">Table placeholder</div>
            </v-card-text>
          </v-card>
        </v-col>
        <v-col cols="12" md="8">
          <v-card elevation="1" rounded class="section-card">
            <v-card-title>Regional Performance</v-card-title>
            <v-card-text>
              <div class="placeholder">Map / summary placeholder</div>
            </v-card-text>
          </v-card>
        </v-col>
        <v-col cols="12" md="4">
          <v-card elevation="1" rounded class="section-card">
            <v-card-title>On-Time Delivery Trend</v-card-title>
            <v-card-text>
              <div class="placeholder">Trend chart placeholder</div>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </v-main>
</template>

<script setup lang="ts">
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
