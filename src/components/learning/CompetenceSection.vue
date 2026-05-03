<script setup>
import CompetenceCard from './CompetenceCard.vue'
import StatusBadge from './StatusBadge.vue'

defineProps({
  competence: {
    type: Object,
    required: true
  }
})
</script>

<template>
  <section
    class="competence-section"
    :id="'comp-' + competence.id"
    :style="{ '--comp-color': competence.color }"
  >
    <div class="competence-container">
      <header class="competence-header">
        <div class="competence-title-row">
          <span class="competence-bar"></span>
          <div>
            <p class="competence-eyebrow">
              Compétence · Niveau 3 · Parcours RACDV
            </p>
            <h2 class="competence-name">{{ competence.shortName }}</h2>
            <p class="competence-mission">{{ competence.name }}</p>
          </div>
          <div class="competence-status">
            <StatusBadge :status="competence.globalStatus" />
          </div>
        </div>

        <p class="competence-description">{{ competence.description }}</p>

        <div class="competence-ce">
          <h3 class="competence-ce-title">Composantes essentielles évaluées</h3>
          <ul class="competence-ce-list">
            <li v-for="ce in competence.componentsList" :key="ce.code">
              <strong>{{ ce.code }}</strong> : {{ ce.label }}
            </li>
          </ul>
        </div>
      </header>

      <div class="competence-grid">
        <CompetenceCard
          v-for="ac in competence.apprentissages"
          :key="ac.code"
          :ac="ac"
        />
      </div>

      <aside v-if="competence.reflection" class="competence-reflection">
        <h3>Posture réflexive</h3>
        <p v-html="competence.reflection"></p>
      </aside>
    </div>
  </section>
</template>

<style scoped>
.competence-section {
  padding: 90px 8%;
  background: var(--gradient-section);
}

.competence-section:nth-of-type(even) {
  background: var(--gradient-section-alt);
}

.competence-container {
  max-width: 1100px;
  margin: 0 auto;
}

.competence-header {
  margin-bottom: 2.5rem;
}

.competence-title-row {
  display: flex;
  align-items: center;
  gap: 1.2rem;
  flex-wrap: wrap;
  margin-bottom: 1.4rem;
}

.competence-bar {
  width: 8px;
  height: 64px;
  border-radius: 4px;
  background: var(--comp-color, var(--accent));
  flex-shrink: 0;
}

.competence-eyebrow {
  margin: 0 0 0.3rem;
  font-size: 0.78rem;
  text-transform: uppercase;
  letter-spacing: 0.1em;
  color: var(--comp-color, var(--accent));
  font-weight: 700;
}

.competence-name {
  margin: 0;
  font-size: clamp(2rem, 4vw, 2.6rem);
  font-weight: 800;
  color: var(--text-primary);
  line-height: 1.15;
}

.competence-mission {
  margin: 0.4rem 0 0;
  font-size: 1.05rem;
  color: var(--text-secondary);
  font-style: italic;
}

.competence-status {
  margin-left: auto;
}

.competence-description {
  color: var(--text-secondary);
  line-height: 1.7;
  font-size: 1rem;
  max-width: 820px;
  margin-bottom: 1.6rem;
}

.competence-ce {
  background: var(--card-bg);
  border-radius: 14px;
  padding: 1.1rem 1.4rem;
  border-left: 4px solid var(--comp-color, var(--accent));
}

.competence-ce-title {
  font-size: 0.95rem;
  font-weight: 700;
  color: var(--text-primary);
  margin: 0 0 0.6rem;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

.competence-ce-list {
  list-style: none;
  padding: 0;
  margin: 0;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 0.4rem 1.4rem;
  color: var(--text-secondary);
  font-size: 0.92rem;
  line-height: 1.55;
}

.competence-ce-list strong {
  color: var(--text-accent);
  font-weight: 700;
}

.competence-grid {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 1.2rem;
}

.competence-reflection {
  margin-top: 2rem;
  background: var(--card);
  border-radius: 18px;
  padding: 1.5rem 1.8rem;
  box-shadow: var(--shadow-sm);
  border-left: 4px solid var(--comp-color, var(--accent));
}

.competence-reflection h3 {
  margin: 0 0 0.6rem;
  font-size: 1.1rem;
  font-weight: 700;
  color: var(--text-primary);
}

.competence-reflection p {
  margin: 0;
  color: var(--text-secondary);
  line-height: 1.7;
}

.competence-reflection :deep(strong) {
  color: var(--text-primary);
}

@media (max-width: 900px) {
  .competence-section {
    padding: 70px 6%;
  }

  .competence-grid {
    grid-template-columns: 1fr;
  }

  .competence-ce-list {
    grid-template-columns: 1fr;
  }

  .competence-status {
    margin-left: 0;
  }
}
</style>
