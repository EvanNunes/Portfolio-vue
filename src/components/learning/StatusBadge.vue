<script setup>
import { computed } from 'vue'

const props = defineProps({
  status: {
    type: String,
    required: true,
    validator: (v) => ['acquis', 'en-cours', 'non-acquis', 'non-applicable'].includes(v)
  },
  size: {
    type: String,
    default: 'md',
    validator: (v) => ['sm', 'md'].includes(v)
  }
})

const meta = computed(() => {
  switch (props.status) {
    case 'acquis':
      return { label: 'Acquis', icon: '🟢' }
    case 'en-cours':
      return { label: "En cours d'acquisition", icon: '🟡' }
    case 'non-acquis':
      return { label: 'Non acquis', icon: '🔴' }
    case 'non-applicable':
      return { label: 'Non applicable', icon: '⚪' }
    default:
      return { label: '', icon: '' }
  }
})
</script>

<template>
  <span class="status-badge" :class="['status-' + status, 'size-' + size]">
    <span class="badge-icon" aria-hidden="true">{{ meta.icon }}</span>
    <span class="badge-label">{{ meta.label }}</span>
  </span>
</template>

<style scoped>
.status-badge {
  display: inline-flex;
  align-items: center;
  gap: 0.4rem;
  border-radius: 999px;
  font-weight: 600;
  white-space: nowrap;
  border: 1px solid var(--border-color);
  background: var(--card);
  color: var(--text-primary);
  line-height: 1;
}

.size-md {
  padding: 0.4rem 0.85rem;
  font-size: 0.85rem;
}

.size-sm {
  padding: 0.25rem 0.6rem;
  font-size: 0.75rem;
}

.status-acquis {
  background: rgba(34, 197, 94, 0.12);
  color: #15803d;
  border-color: rgba(34, 197, 94, 0.35);
}

.status-en-cours {
  background: rgba(234, 179, 8, 0.14);
  color: #a16207;
  border-color: rgba(234, 179, 8, 0.4);
}

.status-non-acquis {
  background: rgba(239, 68, 68, 0.12);
  color: #b91c1c;
  border-color: rgba(239, 68, 68, 0.35);
}

.status-non-applicable {
  background: rgba(100, 116, 139, 0.12);
  color: var(--text-secondary);
  border-color: rgba(100, 116, 139, 0.3);
}

[data-theme="dark"] .status-acquis {
  background: rgba(34, 197, 94, 0.18);
  color: #4ade80;
}

[data-theme="dark"] .status-en-cours {
  background: rgba(234, 179, 8, 0.2);
  color: #facc15;
}

[data-theme="dark"] .status-non-acquis {
  background: rgba(239, 68, 68, 0.2);
  color: #f87171;
}

[data-theme="dark"] .status-non-applicable {
  background: rgba(148, 163, 184, 0.18);
  color: #cbd5e1;
}
</style>
