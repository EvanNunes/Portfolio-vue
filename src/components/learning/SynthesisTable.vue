<script setup>
import StatusBadge from './StatusBadge.vue'

defineProps({
  competences: {
    type: Array,
    required: true
  }
})
</script>

<template>
  <div class="synthesis">
    <h2 class="synthesis-title">Synthèse</h2>
    <p class="synthesis-intro">
      Vue d'ensemble de mon auto-évaluation sur les trois compétences de niveau 3
      du parcours RACDV. Le détail et l'argumentation sont présentés plus bas.
    </p>

    <div class="synthesis-grid">
      <div
        v-for="comp in competences"
        :key="comp.id"
        class="synthesis-card"
        :style="{ '--comp-color': comp.color }"
      >
        <div class="synthesis-header">
          <span class="synthesis-tag">{{ comp.shortName }}</span>
          <span class="synthesis-level">Niveau 3</span>
        </div>
        <h3 class="synthesis-name">{{ comp.name }}</h3>
        <p class="synthesis-desc">{{ comp.summary }}</p>
        <div class="synthesis-status">
          <StatusBadge :status="comp.globalStatus" />
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.synthesis {
  max-width: 1100px;
  margin: 0 auto;
}

.synthesis-title {
  font-size: clamp(1.8rem, 3vw, 2.4rem);
  font-weight: 800;
  color: var(--text-primary);
  margin-bottom: 0.6rem;
}

.synthesis-intro {
  color: var(--text-secondary);
  line-height: 1.7;
  max-width: 760px;
  margin-bottom: 2.2rem;
}

.synthesis-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 1.2rem;
}

.synthesis-card {
  background: var(--card);
  border-radius: 18px;
  padding: 1.4rem 1.4rem 1.5rem;
  box-shadow: var(--shadow-sm);
  border-top: 4px solid var(--comp-color, var(--accent));
  display: flex;
  flex-direction: column;
  gap: 0.6rem;
}

.synthesis-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 0.78rem;
  text-transform: uppercase;
  letter-spacing: 0.08em;
}

.synthesis-tag {
  color: var(--comp-color, var(--accent));
  font-weight: 700;
}

.synthesis-level {
  color: var(--text-muted);
  font-weight: 600;
}

.synthesis-name {
  margin: 0;
  font-size: 1.1rem;
  font-weight: 700;
  color: var(--text-primary);
  line-height: 1.35;
}

.synthesis-desc {
  margin: 0;
  color: var(--text-secondary);
  font-size: 0.92rem;
  line-height: 1.55;
  flex: 1;
}

.synthesis-status {
  margin-top: 0.4rem;
}

@media (max-width: 900px) {
  .synthesis-grid {
    grid-template-columns: 1fr;
  }
}
</style>
