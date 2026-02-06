<script setup>
import { RouterLink } from 'vue-router'

const projects = [
  {
    path: '/myavatar',
    img: 'https://ps.w.org/gravatar-enhanced/assets/icon-256x256.png?rev=3133133',
    title: 'MyAvatar',
    description: "Application web en <strong>server-side rendering</strong> (Symfony + Twig) inspirée de <strong>Gravatar</strong> : associer une adresse email à une photo de profil, récupérable via une URL basée sur un <strong>hash SHA-256</strong>."
  },
  {
    path: '/NDI',
    img: 'https://iutrs.unistra.fr/websites/iutrs/actus-agenda/2024-2025/ACTU_SITE.jpg',
    title: "Nuit de l'Info 2024",
    description: "Lors de la <strong>Nuit de l'Info 2024</strong>, j'ai participé à un événement collaboratif réunissant des étudiants et des proféssionnels du développement informatique. Le défi de cette édition était de créer une <strong>application web intéractive et éducative</strong> mettant en avant les <strong>parallèles entre les systèmes du corps humain</strong> et les <strong>systèmes océaniques</strong>."
  },
  {
    path: '/animeCritik',
    img: '/img/animeCritik/onePiece.jpg',
    title: 'Critik Anime',
    description: "Développement d'une <strong>API REST</strong> avec <strong>Symfony + API Platform</strong>, et d'une application <strong>Vue.js + TypeScript</strong> consommant l'API pour permettre de publier et consulter des <strong>critiques d'anime</strong>, gérer les favoris et les rôles (user/admin)."
  }
]
</script>

<template>
  <section id="projects-carousel" class="projects-carousel">
    <h2 class="projects-title">Mes projets</h2>

    <div class="row g-4" id="projectsGrid">
      <div
        v-for="project in projects"
        :key="project.path"
        class="col-md-6 col-lg-4"
      >
        <div class="repo-card p-0">
          <img class="project-img" :src="project.img" :alt="project.title">
          <div class="p-3">
            <h5>{{ project.title }}</h5>
            <p class="mb-1" v-html="project.description"></p>
            <RouterLink class="btn btn-sm btn-outline-primary" :to="project.path">
              Voir
            </RouterLink>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
