<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { useGsap } from '../../composables/useGsap'

const categories = [
  { label: 'Web', skills: 'HTML • CSS • JS • TS • Vue • Angular • PHP • Symfony' },
  { label: 'DevOps', skills: 'Docker • Git • CLI • Linux • CI/CD' },
  { label: 'Logiciel', skills: 'Java • Python • C • Android' },
  { label: 'Bases de données', skills: 'MySQL • PostgreSQL • MongoDB • Cassandra' },

]

const displayedLabel  = ref('')
const displayedSkills = ref('')
let timeoutId = null
let catIndex  = 0

function schedule(fn, delay) {
  timeoutId = setTimeout(fn, delay)
}

function typeText(target, full, speed, onDone) {
  let i = target.value.length
  function step() {
    if (i < full.length) {
      target.value = full.slice(0, ++i)
      schedule(step, speed)
    } else {
      onDone()
    }
  }
  schedule(step, speed)
}

function eraseText(target, speed, onDone) {
  function step() {
    if (target.value.length > 0) {
      target.value = target.value.slice(0, -1)
      schedule(step, speed)
    } else {
      onDone()
    }
  }
  schedule(step, speed)
}

function runCycle() {
  const { label, skills } = categories[catIndex]
  typeText(displayedLabel, label, 80, () => {
    typeText(displayedSkills, skills, 40, () => {
      schedule(() => {
        eraseText(displayedSkills, 25, () => {
          eraseText(displayedLabel, 25, () => {
            catIndex = (catIndex + 1) % categories.length
            runCycle()
          })
        })
      }, 2500)
    })
  })
}

onMounted(() => runCycle())
onUnmounted(() => clearTimeout(timeoutId))

useGsap(({ gsap, ScrollTrigger }) => {
  const h1 = document.querySelector('.hero h1')
  const others = document.querySelectorAll('.hero p, .hero .btn')

  if (h1) {
    gsap.from(h1, {
      y: 30,
      opacity: 0,
      duration: 0.8,
      ease: 'power3.out'
    })
  }

  if (others.length) {
    gsap.from(others, {
      y: 16,
      opacity: 0,
      stagger: 0.08,
      delay: 0.2,
      duration: 0.7
    })
  }

  gsap.to('.scroll-indicator', {
    opacity: 0,
    ease: 'none',
    scrollTrigger: {
      trigger: '.hero',
      start: 'top top',
      end: '+=120',
      scrub: true
    }
  })
})
</script>

<template>
  <section class="hero">
    <div class="container">
      <div class="row align-items-center">
        <div class="col-lg-6 mb-4">
          <h1 class="display-5 fw-bold">
            Salut, je m'appelle <span style="color: var(--accent)">Evan</span>
          </h1>
          <p class="lead">
            Étudiant en <strong>3e année de BUT Informatique</strong> — parcours <em>RACDV</em>.
            Passionné par le web, les apps et les animations modernes.
            Objectif : intégrer une école d'ingénieur.
          </p>

          <p class="skills-typewriter">
            Compétences <span class="tw-label">{{ displayedLabel }}</span><span v-if="displayedLabel"> : </span><span class="tw-skills">{{ displayedSkills }}</span><span class="tw-cursor">|</span>
          </p>

          <div class="mt-3">
            <a class="btn btn-primary me-2" href="#projects-carousel">Voir mes projets</a>
            <a class="btn btn-outline-primary" href="#repos">Mes dépôts GitHub</a>
          </div>
        </div>

        <div class="col-lg-6 text-center">
          <img src="/img/evan.png" alt="moi" class="avatar">
        </div>
      </div>
    </div>

    <div class="scroll-indicator" aria-hidden="true">
      <div class="scroll-indicator__chevron"></div>
    </div>
  </section>
</template>

<style scoped>
.tw-label { color: var(--accent); font-weight: 600; }
.tw-cursor {
  display: inline-block;
  animation: blink 0.7s step-end infinite;
  color: var(--accent);
  margin-left: 1px;
}
@keyframes blink {
  0%, 100% { opacity: 1; }
  50%       { opacity: 0; }
}
</style>
