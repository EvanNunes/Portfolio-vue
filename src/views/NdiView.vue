<script setup>
import { useGsap } from '../composables/useGsap'
import ProjectHero from '../components/project/ProjectHero.vue'
import TeamSection from '../components/project/TeamSection.vue'
import PhotoGallery from '../components/project/PhotoGallery.vue'
import InterestCard from '../components/ui/InterestCard.vue'

const teamMembers = [
  { name: 'Evan Nunes', role: 'Front & Back', img: '/img/ndi/Evan.png' },
  { name: 'Damien Rostaing', role: 'Front & Back', img: '/img/ndi/Damien.jpg' },
  { name: 'Marc Haye', role: 'Front & Back', img: '/img/ndi/Marc.jpg' },
  { name: 'Paulo Moreira-Pereira', role: 'Front & Video', img: '/img/ndi/Paulo.jpg' },
  { name: 'Matteo Benhalima', role: 'Front & Back', img: '/img/ndi/Matteo.jpg' }
]

const skills = [
  {
    icon: '🎨',
    title: 'Interactivité JavaScript',
    description: "Développement d'animations fluides et d'interactions utilisateur intuitives pour une expérience immersive."
  },
  {
    icon: '⚡',
    title: 'Backend Node.js',
    description: 'Gestion performante des données avec un backend léger et efficace pour des temps de réponse optimaux.'
  },
  {
    icon: '👥',
    title: "Travail d'Équipe",
    description: 'Collaboration efficace et résolution de problèmes dans un environnement de développement rapide.'
  },
  {
    icon: '🚀',
    title: 'Innovation',
    description: 'Approche créative combinant sciences marines et anatomie humaine de manière originale.'
  },
  {
    icon: '⏱️',
    title: 'Performance',
    description: "Conception et déploiement d'une application complète en temps limite lors de l'événement."
  }
]

const photos = [
  '/img/ndi/photo1.JPG',
  '/img/ndi/photo2.JPG',
  '/img/ndi/photo3.JPG',
  '/img/ndi/photo4.JPG',
  '/img/ndi/photo5.JPG',
  '/img/ndi/photo6.JPG',
  '/img/ndi/photo7.JPG',
  '/img/ndi/photo8.JPG'
]

useGsap(({ gsap, ScrollTrigger }) => {
  // About section animation
  const aboutSection = document.querySelector('.about-section')
  if (aboutSection) {
    gsap.timeline({
      scrollTrigger: {
        trigger: '.about-section',
        start: 'top top',
        end: '+=600',
        scrub: true,
        pin: true,
        pinSpacing: true
      }
    })
      .to('.about-title span', {
        opacity: 1,
        y: 0,
        stagger: 0.15
      })
      .to('.about-line', {
        width: '120px'
      }, '-=0.3')
      .to('.about-text', {
        opacity: 1,
        y: 0
      }, '-=0.2')
  }

  // Interest cards animation
  const cards = gsap.utils.toArray('.interest-card')
  if (cards.length) {
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
  }
})
</script>

<template>
  <div class="ndi-view">
    <ProjectHero
      badge="Projet académique"
      title="Nuit de l'info"
      description="Lors de la <strong>Nuit de l'Info 2024</strong>, j'ai participé a un événement collaboratif reunissant des étudiants et des professionnels du développement informatique. Le défi de cette édition etait de créer une <strong>application web intéractive et éducative</strong> mettant en avant les <strong>parallèles entre les systèmes du corps humain</strong> et les <strong>systèmes océaniques</strong>."
      :technologies="['Html', 'CSS', 'NodeJs']"
      image="https://iutrs.unistra.fr/websites/iutrs/actus-agenda/2024-2025/ACTU_SITE.jpg"
      image-alt="Nuit de l'info"
    />

    <section class="about-section" id="about">
      <div class="about-container">
        <h2 class="about-title">
          <span>Le </span>
          <span class="highlight">Projet</span>
        </h2>

        <div class="about-line"></div>

        <p class="about-text">
          La Nuit de l'Info 2024 a réuni étudiants et professionnels autour d'un défi ambitieux : créer une application web interactive établissant des parallèles entre les systèmes du corps humain et les écosystèmes océaniques.
          <br /><br />
          Notre équipe a conçu une exploration interactive d'un océan virtuel ou chaque élément marin révèle les secrets d'un organe humain. Les utilisateurs découvrent ainsi les fonctions vitales de notre corps a travers des analogies marines captivantes.
          <br /><br />
          Cette expérience immersive combine pédagogie et innovation technologique, offrant une nouvelle facon de comprendre la biologie humaine a travers le prisme de l'océan.
        </p>
      </div>
    </section>

    <section class="interests-section">
      <div class="interests-container">
        <h2 class="interests-title">
          <span>Technologies</span> <span>& Compétences</span>
        </h2>

        <div class="interests-grid">
          <InterestCard
            v-for="skill in skills"
            :key="skill.title"
            :icon="skill.icon"
            :title="skill.title"
            :description="skill.description"
          />
        </div>
      </div>
    </section>

    <TeamSection :members="teamMembers" />

    <PhotoGallery :photos="photos" />
  </div>
</template>
