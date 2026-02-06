<script setup>
import { useGsap } from '../composables/useGsap'
import ProjectHero from '../components/project/ProjectHero.vue'
import FlowSection from '../components/project/FlowSection.vue'
import FeatureGrid from '../components/project/FeatureGrid.vue'
import PhotoGallery from '../components/project/PhotoGallery.vue'

const flowSteps = [
  { key: 'api', title: 'API REST', subtitle: 'Symfony + API Platform' },
  { key: 'front', title: 'Front Vue', subtitle: 'SPA + TypeScript' },
  { key: 'avatar', title: 'MyAvatar', subtitle: 'SHA-256 email → photo' }
]

const flowPanels = [
  {
    key: 'api',
    title: 'Back-end : API REST (API Platform)',
    list: [
      'Ressources : utilisateurs, animes, critiques, favoris',
      'Groupes de sérialisation / validation',
      'Permissions (security), rôles & voters',
      'StateProcessors / StateProviders',
      'JWT + refresh token'
    ]
  },
  {
    key: 'front',
    title: 'Front : Vue.js + TypeScript',
    list: [
      'Routes nommées + vues & composants',
      'Connexion / déconnexion / refresh token',
      'Gestion erreurs API + notifications',
      'CRUD : animes & critiques selon permissions',
      'Favoris + feed "dernières critiques"'
    ]
  },
  {
    key: 'avatar',
    title: 'Intégration MyAvatar',
    content: `<p>
      Les avatars des utilisateurs sont chargés depuis <strong>MyAvatar</strong> :
      on récupère l'email depuis l'API, on le chiffre en <strong>SHA-256</strong>,
      puis on affiche l'image via une URL de type :
    </p>
    <div class="ca-code">
      <code>https://mon-myavatar.fr/avatar/{hashSHA256}</code>
    </div>
    <p class="mt">
      Résultat : aucune image stockée côté client, et une photo de profil
      réutilisable partout.
    </p>`
  }
]

const features = [
  { title: 'Rôles & permissions', description: 'Users et admins : création, validation, suppression contrôlées via security/voters.' },
  { title: 'Critiques (1 par anime)', description: "Note, texte + critères spécifiques ; modification/suppréssion par l'auteur, modération admin." },
  { title: 'Validation des contenus', description: "Les users soumettent un anime, l'admin valide avant publication publique." },
  { title: 'Favoris & feed privé', description: 'Liste des favoris + dernières critiques des favoris triées de la plus récente à la plus ancienne.' },
  { title: 'JWT + refresh', description: 'Authentification sécurisée avec cookies JWT + rafraichissement automatique.' },
  { title: 'UX & robustesse', description: 'Gestion des erreurs API, notifications, typage TypeScript, composants Vue bien découpés.' }
]

const photos = [
  '/img/animeCritik/1.png',
  '/img/animeCritik/2.png',
  '/img/animeCritik/3.png',
  '/img/animeCritik/4.png',
  '/img/animeCritik/5.png',
  '/img/animeCritik/6.png',
  '/img/animeCritik/7.png',
  '/img/animeCritik/8.png'
]

useGsap(({ gsap, ScrollTrigger }) => {
  // Feature cards stagger
  gsap.utils.toArray('[data-ca-stagger]').forEach(block => {
    gsap.fromTo(block.querySelectorAll('.ca-card'),
      { y: 26, opacity: 0 },
      {
        y: 0,
        opacity: 1,
        duration: 0.7,
        stagger: 0.08,
        ease: 'power3.out',
        scrollTrigger: { trigger: block, start: 'top 80%' }
      }
    )
  })

  // Section titles reveal
  gsap.utils.toArray('.ca-section .ca-h2').forEach(el => {
    gsap.fromTo(el,
      { y: 18, opacity: 0 },
      {
        y: 0, opacity: 1, duration: 0.6, ease: 'power2.out',
        scrollTrigger: { trigger: el, start: 'top 85%' }
      }
    )
  })
})
</script>

<template>
  <div class="animecritik-view">
    <ProjectHero
      badge="Projet client / serveur — API REST + Vue.js"
      title="Critik Anime"
      description="Développement d'une <strong>API REST</strong> avec <strong>Symfony + API Platform</strong>, et d'une application <strong>Vue.js + TypeScript</strong> consommant l'API pour permettre de publier et consulter des <strong>critiques d'anime</strong>, gérer les favoris et les rôles (user/admin)."
      :technologies="['Symfony', 'API Platform', 'Vue.js', 'TypeScript', 'JWT', 'MyAvatar']"
      image="/img/animeCritik/onePiece.jpg"
      image-alt="Critik Anime"
      extra-class="ca-hero"
    />

    <FlowSection
      title="Architecture"
      subtitle="Un système complet <strong>client / serveur</strong> avec sécurité, permissions, et un front réactif."
      :steps="flowSteps"
      :panels="flowPanels"
    />

    <section class="ca-section">
      <div class="container narrow">
        <h2 class="ca-h2">Fonctionnalités clés</h2>

        <div class="ca-grid" data-ca-stagger>
          <div v-for="feature in features" :key="feature.title" class="ca-card">
            <h3>{{ feature.title }}</h3>
            <p>{{ feature.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <section class="ca-section alt">
      <div class="container narrow">
        <h2 class="ca-h2">Modèle de données</h2>
        <div class="ca-model">
          <div class="pill">User</div>
          <div class="arrow">→</div>
          <div class="pill">Anime</div>
          <div class="arrow">→</div>
          <div class="pill">Critique</div>
          <div class="arrow">→</div>
          <div class="pill">Favoris</div>
        </div>
        <p class="ca-muted">
          Relations + sous-ressources (ex: publications, critiques par utilisateur, favoris d'un utilisateur, etc.).
        </p>
      </div>
    </section>

    <PhotoGallery :photos="photos" />
  </div>
</template>
