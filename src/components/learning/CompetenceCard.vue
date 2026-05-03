<script setup>
import StatusBadge from './StatusBadge.vue'

defineProps({
  ac: {
    type: Object,
    required: true
  }
})
</script>

<template>
  <article class="ac-card" :class="['ac-card--' + ac.status]">
    <header class="ac-head">
      <div class="ac-title-wrap">
        <span class="ac-tag">{{ ac.code }}</span>
        <h4 class="ac-title">{{ ac.title }}</h4>
      </div>
      <StatusBadge :status="ac.status" size="sm" />
    </header>

    <div v-if="ac.ce && ac.ce.length" class="ac-ce">
      <span class="ac-ce-label">Composantes&nbsp;:</span>
      <span v-for="ce in ac.ce" :key="ce" class="ac-ce-chip">{{ ce }}</span>
    </div>

    <div v-if="ac.traces && ac.traces.length" class="ac-traces">
      <span class="ac-traces-label">Traces&nbsp;:</span>
      <ul class="ac-traces-list">
        <li v-for="(trace, idx) in ac.traces" :key="idx">
          <router-link v-if="trace.to" :to="trace.to" class="ac-trace-link">
            {{ trace.label }}
          </router-link>
          <span v-else>{{ trace.label }}</span>
          <span v-if="trace.context" class="ac-trace-context"> · {{ trace.context }}</span>
        </li>
      </ul>
    </div>

    <p class="ac-argument" v-html="ac.argument"></p>
  </article>
</template>

<style scoped>
.ac-card {
  background: var(--card);
  border-radius: 18px;
  padding: 1.4rem 1.5rem 1.5rem;
  box-shadow: var(--shadow-sm);
  border: 1px solid var(--border-color);
  display: flex;
  flex-direction: column;
  gap: 0.85rem;
  height: 100%;
}

.ac-head {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  gap: 0.8rem;
  flex-wrap: wrap;
}

.ac-title-wrap {
  display: flex;
  flex-direction: column;
  gap: 0.25rem;
  flex: 1;
  min-width: 0;
}

.ac-tag {
  font-size: 0.72rem;
  font-weight: 700;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--text-accent);
}

.ac-title {
  margin: 0;
  font-size: 1.05rem;
  font-weight: 700;
  color: var(--text-primary);
  line-height: 1.4;
}

.ac-ce {
  font-size: 0.85rem;
  color: var(--text-secondary);
  display: flex;
  flex-wrap: wrap;
  gap: 0.4rem;
  align-items: center;
}

.ac-ce-label {
  font-weight: 600;
}

.ac-ce-chip {
  background: rgba(13, 110, 253, 0.1);
  color: var(--text-accent);
  padding: 0.15rem 0.55rem;
  border-radius: 999px;
  font-size: 0.78rem;
  font-weight: 600;
}

[data-theme="dark"] .ac-ce-chip {
  background: rgba(96, 165, 250, 0.18);
  color: #93c5fd;
}

.ac-traces {
  font-size: 0.9rem;
  color: var(--text-secondary);
}

.ac-traces-label {
  font-weight: 600;
  display: block;
  margin-bottom: 0.3rem;
}

.ac-traces-list {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  gap: 0.25rem;
}

.ac-traces-list li::before {
  content: '▸';
  color: var(--text-accent);
  margin-right: 0.4rem;
  font-weight: 700;
}

.ac-trace-link {
  color: var(--text-accent);
  font-weight: 600;
  text-decoration: none;
  border-bottom: 1px solid transparent;
  transition: border-color 0.2s ease;
}

.ac-trace-link:hover {
  border-color: var(--text-accent);
}

.ac-trace-context {
  color: var(--text-muted);
}

.ac-argument {
  margin: 0;
  color: var(--text-secondary);
  line-height: 1.7;
  font-size: 0.95rem;
}

.ac-argument :deep(strong) {
  color: var(--text-primary);
}
</style>
