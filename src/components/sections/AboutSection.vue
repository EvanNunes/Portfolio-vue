<script setup>
import { useGsap } from '../../composables/useGsap'

useGsap(({ gsap, ScrollTrigger }) => {
  const section = document.querySelector('.about-section')
  if (!section) return

  gsap.set('.about-title span', { opacity: 0, y: 30 })
  gsap.set('.about-text', { opacity: 0, y: 20 })
  gsap.set('.about-line', { width: '0px' })

  gsap.timeline({
    scrollTrigger: {
      trigger: '.about-section',
      start: 'top 70%',
      end: 'top 20%',
      scrub: 0.8
    }
  })
    .to('.about-title span', { opacity: 1, y: 0, stagger: 0.15, ease: 'power2.out' })
    .to('.about-line', { width: '120px', ease: 'power2.out' }, '-=0.3')
    .to('.about-text', { opacity: 1, y: 0, ease: 'power2.out' }, '-=0.2')
})
</script>

<template>
  <section class="about-section" id="about">
    <div class="about-container">
      <h2 class="about-title">
        <span>Un développeur</span>&#32;<span class="highlight">curieux</span>&#32;<span>rigoureux</span>&#32;<span>et passionné</span>
      </h2>

      <div class="about-line"></div>

      <p class="about-text">
        J'aime comprendre comment les choses fonctionnent en profondeur,
        concevoir des solutions propres et efficaces, et transformer des idées
        en applications concrètes.
        <br /><br />
        Que ce soit en developpement web, en backend ou sur des projets plus
        techniques, je travaille avec serieux, autonomie et une vraie envie
        de progresser en permanence.
      </p>
    </div>
  </section>
</template>
