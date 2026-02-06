<script setup>
import { useGsap } from '../../composables/useGsap'
import InterestCard from '../ui/InterestCard.vue'

const interests = [
  {
    icon: '💻',
    title: 'Développement',
    description: "Création d'applications web modernes, optimisation des performances et exploration de nouvelles technologies."
  },
  {
    icon: '🎮',
    title: 'Gaming & Création',
    description: 'Développement de plugins Minecraft, game design et automatisation de systèmes complexes.'
  },
  {
    icon: '🚗',
    title: 'Automobile',
    description: 'Passion pour les véhicules, la mécanique et les innovations technologiques embarquées.'
  },
  {
    icon: '🎨',
    title: 'Design & UI',
    description: "Attention portée aux détails, aux animations et a l'expérience utilisateur."
  },
  {
    icon: '🚀',
    title: 'Innovation',
    description: 'Curieux et toujours motivé par les projets ambitieux et les défis techniques.'
  }
]

useGsap(({ gsap, ScrollTrigger }) => {
  const cards = gsap.utils.toArray('.interest-card')
  if (!cards.length) return

  gsap.set(cards, { opacity: 0, y: 40 })

  ScrollTrigger.batch(cards, {
    start: 'top 85%',
    onEnter: batch =>
      gsap.to(batch, {
        opacity: 1,
        y: 0,
        stagger: 0.12,
        duration: 0.6,
        ease: 'power3.out'
      }),
    onLeaveBack: batch =>
      gsap.to(batch, {
        opacity: 0,
        y: 40,
        stagger: 0.08,
        duration: 0.4
      })
  })
})
</script>

<template>
  <section class="interests-section">
    <div class="interests-container">
      <h2 class="interests-title">
        <span>Centres</span> <span>d'intéréts</span>
      </h2>

      <div class="interests-grid">
        <InterestCard
          v-for="interest in interests"
          :key="interest.title"
          :icon="interest.icon"
          :title="interest.title"
          :description="interest.description"
        />
      </div>
    </div>
  </section>
</template>
