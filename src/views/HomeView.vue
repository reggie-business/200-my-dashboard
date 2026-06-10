<template>
  <main class="dashboard">
    <header class="dashboard__header">
      <div>
        <p class="eyebrow">FastForward Logistics</p>
        <h1>Executive Operations Dashboard</h1>
      </div>
      <div class="header-meta">
        <p>Last updated: Today</p>
      </div>
    </header>

    <section class="metrics-grid">
      <article class="metric-card">
        <p class="metric-label">Shipments Today</p>
        <p class="metric-value">1,248</p>
        <p class="metric-note">+4.2% vs yesterday</p>
      </article>
      <article class="metric-card">
        <p class="metric-label">On-Time Delivery</p>
        <p class="metric-value">92.7%</p>
        <p class="metric-note">Stable week-over-week</p>
      </article>
      <article class="metric-card">
        <p class="metric-label">Regional Exceptions</p>
        <p class="metric-value">18</p>
        <p class="metric-note">3 new issues</p>
      </article>
      <article class="metric-card">
        <p class="metric-label">Carrier Capacity</p>
        <p class="metric-value">78%</p>
        <p class="metric-note">Near target</p>
      </article>
    </section>

    <section class="dashboard-layout">
      <div class="chart-card">
        <h2>Shipment Volume</h2>
        <div class="placeholder">Chart placeholder</div>
      </div>
      <div class="exception-card">
        <h2>Open Exceptions</h2>
        <div class="placeholder">Table placeholder</div>
      </div>
      <div class="regional-card">
        <h2>Regional Performance</h2>
        <div class="placeholder">Map / summary placeholder</div>
      </div>
      <div class="trend-card">
        <h2>On-Time Delivery Trend</h2>
        <div class="placeholder">Trend chart placeholder</div>
      </div>
    </section>
  </main>
</template>

<script setup lang="ts"></script>

<style scoped>
.dashboard {
  padding: 2rem;
}

.dashboard__header {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  gap: 1rem;
  margin-bottom: 2rem;
}

.eyebrow {
  margin: 0;
  text-transform: uppercase;
  letter-spacing: 0.16em;
  color: #5f6d7a;
  font-size: 0.85rem;
}

h1 {
  margin: 0.25rem 0 0;
  font-size: 2.1rem;
}

.header-meta {
  color: #5f6d7a;
}

.metrics-grid {
  display: grid;
  grid-template-columns: repeat(4, minmax(0, 1fr));
  gap: 1rem;
  margin-bottom: 1.75rem;
}

.metric-card {
  padding: 1.2rem;
  border-radius: 1rem;
  background: white;
  box-shadow: 0 1px 2px rgba(15, 23, 42, 0.08);
}

.metric-label {
  margin: 0 0 0.5rem;
  color: #6b7280;
  font-size: 0.9rem;
}

.metric-value {
  margin: 0;
  font-size: 2rem;
  font-weight: 700;
}

.metric-note {
  margin: 0.75rem 0 0;
  color: #475569;
}

.dashboard-layout {
  display: grid;
  grid-template-columns: 2fr 1fr;
  grid-template-rows: repeat(2, minmax(0, auto));
  gap: 1rem;
}

.chart-card,
.exception-card,
.regional-card,
.trend-card {
  padding: 1.5rem;
  border-radius: 1rem;
  background: white;
  box-shadow: 0 1px 2px rgba(15, 23, 42, 0.08);
}

.chart-card {
  grid-column: 1 / 2;
}

.exception-card {
  grid-column: 2 / 3;
}

.regional-card {
  grid-column: 1 / 2;
}

.trend-card {
  grid-column: 2 / 3;
}

h2 {
  margin: 0 0 1rem;
  font-size: 1.1rem;
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

@media (max-width: 1100px) {
  .metrics-grid,
  .dashboard-layout {
    grid-template-columns: 1fr;
  }
}
</style>
