<script setup>
import CompetenceSection from '../components/learning/CompetenceSection.vue'
import SynthesisTable from '../components/learning/SynthesisTable.vue'

const competences = [
  {
    id: 'realiser',
    color: '#dc2626',
    shortName: 'Réaliser',
    name: 'Adapter des applications sur un ensemble de supports (embarqué, web, mobile, IoT…)',
    summary: "Concevoir et faire évoluer des applications adaptées à différents supports, en intégrant les contraintes de production.",
    description: "Le niveau 3 de la compétence Réaliser dans le parcours RACDV demande de savoir choisir une architecture adaptée à un contexte, faire évoluer une application existante, et intégrer une solution dans un environnement de production réel. Mes projets web full-stack et le déploiement automatisé de ce portfolio en sont les preuves principales.",
    globalStatus: 'acquis',
    componentsList: [
      { code: 'CE1.01', label: 'en respectant les besoins décrits par le client' },
      { code: 'CE1.03', label: 'en appliquant les principes algorithmiques' },
      { code: 'CE1.04', label: 'en veillant à la qualité du code et à sa documentation' },
      { code: 'CE1.06', label: 'en choisissant les ressources techniques appropriées' }
    ],
    apprentissages: [
      {
        code: 'AC1',
        title: 'Choisir et implémenter les architectures adaptées',
        status: 'acquis',
        ce: ['CE1.01', 'CE1.06'],
        traces: [
          { label: 'Critik Anime', to: '/animeCritik', context: "API REST Symfony + SPA Vue/TypeScript découplées" },
          { label: 'MyAvatar', to: '/myavatar', context: "Symfony server-side rendering avec stockage hors public/" },
          { label: "SAÉ Agents intelligents (BUT 3, S5/S6)", context: "agents de RL sur environnements Gymnasium et IA d'échecs alpha-beta negamax" }
        ],
        argument: "Sur <strong>Critik Anime</strong>, j'ai volontairement séparé un backend Symfony exposant une API REST via API Platform et une SPA Vue 3 + TypeScript en frontend, avec authentification JWT à refresh token. J'ai choisi cette architecture client/serveur car elle permet de faire évoluer chaque côté indépendamment et d'envisager plus tard une application mobile consommant la même API. Sur <strong>MyAvatar</strong>, j'ai au contraire opté pour un rendu server-side avec Twig, plus adapté à un service léger d'images dont l'enjeu était la performance d'accès via hash SHA-256 et non l'interactivité. Sur la <strong>SAÉ Agents intelligents</strong>, l'architecture était d'un autre type : structurer un agent de Q-learning ou de MCTS avec une boucle d'interaction agent/environnement, séparer la politique, la fonction de valeur et l'environnement Gymnasium, puis pour l'IA d'échecs construire un moteur alpha-beta negamax avec table de transposition. Choisir la bonne architecture en fonction du besoin, et non par habitude, est ce qui me semble le plus important dans cet apprentissage."
      },
      {
        code: 'AC2',
        title: 'Faire évoluer une application existante',
        status: 'acquis',
        ce: ['CE1.04'],
        traces: [
          { label: 'Ce portfolio', context: "refonte d'une version statique HTML/CSS vers Vue 3 + Vite" },
          { label: 'Critik Anime', to: '/animeCritik', context: "intégration des avatars MyAvatar via SHA-256" }
        ],
        argument: "Le portfolio actuel est <strong>l'évolution d'une version statique antérieure</strong> que j'ai entièrement réécrite en Vue 3 + Vite. La motivation venait d'un besoin pratique : ajouter des sections (parcours, projets, et aujourd'hui ce portfolio d'apprentissage) devenait coûteux en HTML brut. La refonte m'a obligé à réfléchir au composant comme unité de réutilisation, à scinder le CSS global en variables thématiques, et à organiser le code dans <code>src/components/</code> par responsabilité (layout, sections, ui, project, learning). Sur <strong>Critik Anime</strong>, j'ai aussi fait évoluer une application existante en y intégrant le service MyAvatar plutôt que de redévelopper la gestion d'images. C'est la première fois que j'ai pris au sérieux la documentation et la qualité du code comme un coût d'évolution futur, pas comme un bonus."
      },
      {
        code: 'AC3',
        title: 'Intégrer des solutions dans un environnement de production',
        status: 'acquis',
        ce: ['CE1.06'],
        traces: [
          { label: "Pipeline CI/CD GitHub Actions", context: "build Vite → rsync → VPS Apache + .htaccess SPA" }
        ],
        argument: "Le portfolio que vous lisez est déployé en production sur un VPS Apache via une <strong>pipeline GitHub Actions</strong> que j'ai écrite et corrigée incrémentalement (gestion de la clé SSH, exclusion sélective du dossier <code>pdf/</code> pour préserver les CV mis à jour manuellement, redirection des routes inconnues vers l'accueil via <code>.htaccess</code> pour faire fonctionner le routing SPA). Cette mise en production m'a confronté à des problèmes que les TP académiques évitent : permissions d'écriture sur le serveur, mod_rewrite à activer, cache navigateur entre déploiements. Chaque correctif est traçable dans l'historique git du projet, ce qui me sert aussi de retour d'expérience."
      }
    ],
    reflection: "Cette compétence est celle où je me sens le plus à l'aise, parce qu'elle est au cœur de mes projets personnels comme académiques. Le point que je veux encore consolider est l'<strong>adaptation à des supports non-web</strong> (mobile natif, embarqué) : mon expérience est aujourd'hui essentiellement web, et le stage de fin de BUT sera l'occasion de l'élargir."
  },
  {
    id: 'optimiser',
    color: '#ea580c',
    shortName: 'Optimiser',
    name: 'Analyser et optimiser des applications',
    summary: "Mesurer, analyser et justifier le comportement d'un code existant pour en améliorer les performances et la qualité.",
    description: "Le niveau 3 de la compétence Optimiser ne demande pas seulement de produire du code performant, mais de savoir l'analyser et justifier les choix techniques. La SAÉ Agents intelligents et l'IA d'échecs alpha-beta negamax sont mes traces les plus solides, complétées par l'audit éco-conception du portfolio et les choix de bibliothèques sur Critik Anime.",
    globalStatus: 'acquis',
    componentsList: [
      { code: 'CE2.01', label: 'en formalisant et modélisant des situations complexes' },
      { code: 'CE2.02', label: 'en recensant les algorithmes et structures de données usuels' },
      { code: 'CE2.03', label: 'en s\'appuyant sur des schémas de raisonnement' },
      { code: 'CE2.04', label: 'en justifiant les choix et en validant les résultats' }
    ],
    apprentissages: [
      {
        code: 'AC1',
        title: "Anticiper les résultats de diverses métriques (temps d'exécution, occupation mémoire…)",
        status: 'acquis',
        ce: ['CE2.04'],
        traces: [
          { label: "SAÉ Agents intelligents (BUT 3, S5/S6)", context: "comparaison de performances entre Q-learning et MCTS sur Cliff Walking, Frozen Lake, CartPole, Blackjack" },
          { label: "IA d'échecs alpha-beta negamax", context: "moteur optimisé atteignant ~2500 elo, mesure de profondeur et de temps de calcul" },
          { label: "Lazy-loading des routes du portfolio", context: "import dynamique dans router/index.js pour scinder le bundle initial" }
        ],
        argument: "La <strong>SAÉ Agents intelligents</strong> est l'expérience la plus formatrice sur ce point : nous avons comparé plusieurs algorithmes (Q-learning, MCTS) sur quatre environnements Gymnasium très différents (Cliff Walking, Frozen Lake, CartPole, Blackjack) en mesurant systématiquement la récompense moyenne, le taux de réussite et la vitesse de convergence selon les hyperparamètres (taux d'apprentissage, facteur d'exploration epsilon, profondeur de simulation). Pour l'<strong>IA d'échecs</strong> le travail d'optimisation a été plus poussé encore : à partir d'un negamax alpha-beta de base, chaque amélioration (ordonnancement des coups, table de transposition, killer moves) était évaluée en mesurant à la fois la profondeur atteinte dans un temps donné et le niveau elo final, qui a fini autour de 2500. Cette pratique de mesurer pour valider un choix, je l'applique aussi en plus petit sur le portfolio (lazy-loading des routes pour réduire le bundle initial)."
      },
      {
        code: 'AC2',
        title: "Profiler, analyser et justifier le comportement d'un code existant",
        status: 'acquis',
        ce: ['CE2.03', 'CE2.04'],
        traces: [
          { label: "Rapport éco-conception R6.05", context: "audit RGESN du portfolio, 4 bonnes pratiques respectées et 4 à corriger" }
        ],
        argument: "Dans le module <strong>R6.05 (éco-conception du web)</strong> j'ai produit un audit du portfolio que je suis en train de présenter. Le rapport confronte le code à des règles du <strong>RGESN</strong> et identifie 4 bonnes pratiques respectées (génération statique RWEB0018, limitation des carrousels RWEB0010, langages à jour RWEB0029, design sobre RWEB0012) et 4 à améliorer (compression de la pièce jointe CV RWEB0108, configuration AllowOverride RWEB0089, méta description RWEB0011, media queries mobile-first RWEB0004). C'est exactement le type d'analyse que demande l'AC2 : <em>partir d'un code existant, le confronter à un référentiel, justifier des points positifs et critiquer des points négatifs sans complaisance</em>. Ce travail m'a appris qu'analyser est plus difficile qu'optimiser à l'aveugle."
      },
      {
        code: 'AC3',
        title: "Choisir et utiliser des bibliothèques et méthodes dédiées au domaine d'application",
        status: 'acquis',
        ce: ['CE2.02', 'CE2.04'],
        traces: [
          { label: "SAÉ Agents intelligents (BUT 3, S5/S6)", context: "Gymnasium pour les environnements de RL, Q-learning et MCTS implémentés à la main, IA d'échecs avec alpha-beta negamax optimisé (~2500 elo)" },
          { label: 'Critik Anime', to: '/animeCritik', context: "API Platform pour exposer l'API, JWT + refresh tokens pour l'authentification" },
          { label: "Ce portfolio", context: "GSAP + ScrollTrigger pour animations complexes au scroll" }
        ],
        argument: "C'est l'apprentissage critique où je me sens le plus aligné avec les exemples du référentiel (qui cite l'intelligence artificielle et les jeux vidéo). Sur la <strong>SAÉ Agents intelligents</strong>, nous avons utilisé <strong>Gymnasium</strong> comme environnement standard de RL, mais nous avons volontairement implémenté nous-mêmes les agents (Q-learning, MCTS) sans réutiliser de solutions toutes faites pour comprendre les mécanismes internes. L'<strong>IA d'échecs</strong> est un exemple parfait de méthode dédiée à un domaine : alpha-beta negamax, ordonnancement des coups, élagage par table de transposition, killer moves, autant de techniques classiques de l'intelligence artificielle de jeu, choisies parce qu'elles sont les plus efficaces sur ce problème précis. Sur <strong>Critik Anime</strong> j'ai choisi <strong>API Platform</strong> pour générer la couche de sérialisation et la documentation OpenAPI, ce qui m'a libéré pour me concentrer sur les voters de sécurité et les state processors métier. Pour l'authentification j'ai pris <strong>JWT avec refresh token</strong> plutôt que des sessions classiques, parce que le frontend est une SPA séparée. À chaque fois la question était la même : le standard couvre-t-il le besoin, ou la bibliothèque dédiée se justifie-t-elle ?"
      }
    ],
    reflection: "Je situe cette compétence comme <strong>acquise</strong> au global. La SAÉ Agents intelligents et l'IA d'échecs ont été le déclic : je n'ai jamais autant mesuré, comparé et justifié des choix algorithmiques. Le rapport éco-conception du portfolio applique la même démarche à un autre objet (le code lui-même), et le choix de bibliothèques dédiées est pour moi devenu un réflexe. Il me reste à étendre cette rigueur au profiling fin (mémoire, tests de charge), notamment dans un cadre web de production."
  },
  {
    id: 'collaborer',
    color: '#6366f1',
    shortName: 'Collaborer',
    name: 'Manager une équipe informatique',
    summary: "Coordonner une équipe, organiser une veille, comprendre les enjeux économiques et juridiques du numérique.",
    description: "Le niveau 3 de la compétence Collaborer dépasse le simple travail en équipe : il vise à manager. Mes preuves les plus solides viennent de la SAÉ Poursuite d'études en BUT 2 où j'ai appliqué Scrum avec un rôle ponctuel de Scrum Master, de la SAÉ Agents intelligents (équipe de 6 sur un projet long) et de la Nuit de l'Info 2024 (équipe sous contrainte). Les autres apprentissages critiques sont en cours de construction.",
    globalStatus: 'en-cours',
    componentsList: [
      { code: 'CE6.01', label: "en inscrivant sa démarche au sein d'une équipe pluridisciplinaire" },
      { code: 'CE6.02', label: "en accompagnant la mise en œuvre des évolutions informatiques" },
      { code: 'CE6.03', label: "en veillant au respect des contraintes juridiques" },
      { code: 'CE6.04', label: "en développant une communication efficace et collaborative" }
    ],
    apprentissages: [
      {
        code: 'AC1',
        title: 'Organiser et partager une veille numérique',
        status: 'en-cours',
        ce: ['CE6.02'],
        traces: [
          { label: "Profil GitHub actif", context: "suivi de dépôts Vue, Symfony, API Platform" },
          { label: "Adoption de stack récente", context: "Vue 3 Composition API, Vite, TypeScript, GSAP 3" },
          { label: "Veille IA pour la SAÉ Agents intelligents", context: "techniques d'optimisation alpha-beta (ordering, transposition tables, killer moves) recensées et choisies à partir de la littérature classique" }
        ],
        argument: "Ma veille est aujourd'hui <strong>individuelle et passive</strong> : abonnements GitHub, lecture de la documentation officielle quand une techno évolue, suivi des release notes des frameworks que j'utilise. Le résultat est tangible : j'ai migré le portfolio vers Vue 3 Composition API et TypeScript dès leur stabilisation. Sur la SAÉ Agents intelligents, j'ai aussi pratiqué une veille plus pointue pour aller chercher les optimisations classiques d'un moteur d'échecs (ordonnancement des coups, table de transposition, killer moves), ce qui a permis à l'IA d'atteindre 2500 elo. Mais je <em>ne partage pas formellement</em> cette veille (pas de blog, pas de canal d'équipe), c'est pourquoi je me place en cours d'acquisition : la veille existe, l'organisation et le partage restent à structurer."
      },
      {
        code: 'AC2',
        title: "Identifier les enjeux de l'économie de l'innovation numérique",
        status: 'en-cours',
        ce: ['CE6.02', 'CE6.03'],
        traces: [
          { label: "Rapport éco-conception R6.05", context: "impact environnemental, sobriété numérique, RGESN" },
          { label: "Choix open source systématique", context: "Vue, Symfony, Bootstrap, GSAP (licences et écosystème)" }
        ],
        argument: "Deux enjeux m'ont marqué concrètement. <strong>L'éco-conception</strong> d'abord : le rapport R6.05 m'a fait comprendre que la performance et l'impact environnemental sont liés (un site statique léger consomme moins), ce qui croise enjeux techniques et enjeux sociétaux. <strong>L'open source</strong> ensuite : les briques que j'utilise sont toutes libres, ce qui me confronte à des questions de licence et de gouvernance, par exemple le passage de certaines bibliothèques vers des modèles commerciaux. Je ne maîtrise pas encore les aspects économiques (modèles d'affaires, financements, marché), mais la dimension juridique et environnementale m'est devenue familière."
      },
      {
        code: 'AC3',
        title: "Guider la conduite du changement informatique au sein d'une organisation",
        status: 'non-applicable',
        ce: [],
        traces: [
          { label: "Stage de fin de cursus chez Free", context: "développeur full-stack, terrain en cours d'observation au moment de la rédaction" }
        ],
        argument: "Je marque cet apprentissage critique comme <strong>non applicable</strong> à la date de rédaction, de manière transparente : je n'ai pas encore de trace exploitable de conduite du changement informatique au sein d'une organisation (changement d'outil métier, accompagnement des utilisateurs, formation). C'est précisément une des raisons pour lesquelles je suis <strong>actuellement en stage chez Free comme développeur full-stack</strong> : le contexte professionnel est le bon terrain pour observer, puis pour participer, à ce type de démarche. Je préfère assumer un statut honnête aujourd'hui plutôt que de surjouer un projet de groupe qui n'en relève pas, et mettre cette page à jour quand j'aurai vécu une mission concrète de ce type."
      },
      {
        code: 'AC4',
        title: 'Accompagner le management de projet informatique',
        status: 'acquis',
        ce: ['CE6.01', 'CE6.04'],
        traces: [
          { label: "SAÉ Poursuite d'études (BUT 2, S3)", context: "équipe de 5, Scrum, Trello, daily, sprint reviews avec prof-client, rôle de Scrum Master sur 1 sprint" },
          { label: "SAÉ Agents intelligents (BUT 3, S5/S6)", context: "équipe de 6 sur projet long durée, répartition des agents et environnements à étudier" },
          { label: 'Nuit de l\'Info 2024', to: '/NDI', context: "équipe de 5 sous contrainte de 24h, répartition front/back/vidéo" }
        ],
        argument: "C'est mon apprentissage critique le plus solide sur cette compétence, parce que j'ai vécu plusieurs formats d'équipe très différents. Sur la <strong>SAÉ Poursuite d'études</strong> en BUT 2 (S3), nous étions cinq, organisés en <strong>Scrum</strong> avec un Product Owner et un Scrum Master, un enseignant jouant le rôle de client. <strong>J'ai assumé le rôle de Scrum Master sur un sprint complet</strong> : organisation des daily meetings, suivi du board Trello, animation de la sprint review avec le client et de la rétrospective interne. J'ai participé à l'estimation des tâches en planning poker pour évaluer leur difficulté. Sur la <strong>SAÉ Agents intelligents</strong> (BUT 3) nous étions six, sur un projet bien plus long, où il a fallu se répartir les algorithmes (Q-learning, MCTS) et les environnements (Cliff Walking, Frozen Lake, CartPole, Blackjack) puis converger pour comparer les résultats. Sur la <strong>Nuit de l'Info 2024</strong>, j'ai vécu un autre format encore : 24 heures de contrainte forte, cinq personnes avec rôles techniques distribués (front, back, vidéo), zéro temps pour des cérémonies, la communication devait être quasi-synchrone et la priorisation continue. Ces trois expériences m'ont appris qu'<em>il n'y a pas un seul mode de management</em> : Scrum est lourd mais lisible, le projet long demande de la coordination régulière, le mode hackathon est léger mais épuisant. Bien choisir, c'est déjà manager."
      }
    ],
    reflection: "Je place cette compétence en <strong>cours d'acquisition</strong> au global. L'AC4 (management de projet) est solide grâce à la SAÉ et à NDI ; l'AC1 et l'AC2 progressent ; l'AC3 (conduite du changement) reste à acquérir en stage. Je préfère assumer un \"non applicable\" honnête plutôt que de surjouer une compétence d'organisation que je n'ai pas encore vécue en entreprise."
  }
]

const lastUpdate = '3 mai 2026'
</script>

<template>
  <div class="learning-portfolio">
    <header class="lp-hero">
      <div class="lp-hero-container">
        <p class="lp-hero-eyebrow">BUT Informatique · 3<sup>e</sup> année · Parcours RACDV</p>
        <h1 class="lp-hero-title">Portfolio d'apprentissage</h1>
        <p class="lp-hero-subtitle">
          Une posture réflexive et critique sur les trois compétences de niveau 3 du parcours RACDV
          (Réaliser, Optimiser, Collaborer), documentée et argumentée à partir de mes projets, SAÉ
          et expériences académiques.
        </p>

        <div class="lp-hero-meta">
          <div class="lp-meta-item">
            <span class="lp-meta-label">Étudiant</span>
            <span class="lp-meta-value">Evan Nunes</span>
          </div>
          <div class="lp-meta-item">
            <span class="lp-meta-label">Parcours</span>
            <span class="lp-meta-value">RACDV</span>
          </div>
          <div class="lp-meta-item">
            <span class="lp-meta-label">Stage en cours</span>
            <span class="lp-meta-value">Free, dev full-stack</span>
          </div>
          <div class="lp-meta-item">
            <span class="lp-meta-label">Mise à jour</span>
            <span class="lp-meta-value">{{ lastUpdate }}</span>
          </div>
        </div>
      </div>
    </header>

    <section class="lp-intro">
      <div class="lp-intro-container">
        <h2 class="lp-intro-title">Démarche</h2>
        <p class="lp-intro-text">
          Le portfolio d'apprentissage est, selon le programme national du BUT Informatique,
          l'espace dans lequel l'étudiant <strong>documente et argumente</strong> sa trajectoire
          de développement, en s'appuyant sur des <strong>traces</strong> issues de ses mises
          en situation professionnelle.
        </p>
        <p class="lp-intro-text">
          Pour chacune des trois compétences de niveau 3 du parcours RACDV, je présente ci-dessous :
          la description officielle, les composantes essentielles concernées, puis pour chaque
          apprentissage critique une <strong>auto-évaluation</strong> (Acquis / En cours d'acquisition /
          Non applicable), les <strong>traces</strong> mobilisées (projets accessibles depuis ce site,
          SAÉ, rapports), et une argumentation réflexive de quelques lignes.
        </p>
        <p class="lp-intro-text">
          L'objectif n'est pas de m'auto-féliciter, mais de prendre du recul. J'assume donc
          quelques statuts «&nbsp;En cours&nbsp;» et un «&nbsp;Non applicable&nbsp;» plutôt
          que de tout marquer comme acquis : c'est ce qui rend l'exercice utile pour la suite
          (stage, école d'ingénieur).
        </p>

        <SynthesisTable :competences="competences" />
      </div>
    </section>

    <CompetenceSection
      v-for="comp in competences"
      :key="comp.id"
      :competence="comp"
    />

    <section class="lp-conclusion">
      <div class="lp-conclusion-container">
        <h2>Conclusion</h2>
        <p>
          Trois ans de BUT Informatique m'ont fait basculer du statut d'« étudiant qui code »
          à celui de <strong>développeur capable de justifier ses choix</strong>. La compétence
          que j'ai sentie évoluer le plus est l'analyse critique : entre la première version
          statique de ce portfolio et celle que vous lisez aujourd'hui, ce n'est pas seulement
          le code qui a changé, c'est ma capacité à argumenter <em>pourquoi</em> un choix
          plutôt qu'un autre.
        </p>
        <p>
          Les zones de progression sont claires : <strong>la conduite du changement en
          organisation</strong> (Collaborer N3, AC3), <strong>la veille partagée et
          formalisée</strong> (Collaborer N3, AC1), et <strong>le travail sur des supports
          non-web</strong> comme le mobile ou l'embarqué. Le stage de fin de cursus et la suite
          en école d'ingénieur sont les terrains où ces points seront travaillés.
        </p>
        <p class="lp-signature">
          Evan Nunes · {{ lastUpdate }}
        </p>
      </div>
    </section>
  </div>
</template>

<style scoped>
.learning-portfolio {
  background: var(--bg);
}

/* Hero */
.lp-hero {
  background: var(--gradient-hero);
  padding: 140px 8% 90px;
}

.lp-hero-container {
  max-width: 1100px;
  margin: 0 auto;
}

.lp-hero-eyebrow {
  margin: 0 0 0.8rem;
  font-size: 0.85rem;
  text-transform: uppercase;
  letter-spacing: 0.15em;
  color: var(--accent);
  font-weight: 700;
}

.lp-hero-title {
  margin: 0 0 1rem;
  font-size: clamp(2.4rem, 5vw, 3.8rem);
  font-weight: 800;
  color: var(--text-primary);
  line-height: 1.1;
}

.lp-hero-subtitle {
  margin: 0 0 2.4rem;
  max-width: 780px;
  color: var(--text-secondary);
  font-size: 1.15rem;
  line-height: 1.65;
}

.lp-hero-meta {
  display: grid;
  grid-template-columns: repeat(4, minmax(0, 1fr));
  gap: 1rem;
  border-top: 1px solid var(--border-color);
  padding-top: 1.4rem;
}

.lp-meta-item {
  display: flex;
  flex-direction: column;
  gap: 0.2rem;
}

.lp-meta-label {
  font-size: 0.72rem;
  text-transform: uppercase;
  letter-spacing: 0.1em;
  color: var(--text-muted);
  font-weight: 700;
}

.lp-meta-value {
  font-size: 0.95rem;
  font-weight: 600;
  color: var(--text-primary);
}

/* Intro */
.lp-intro {
  padding: 90px 8%;
  background: var(--gradient-section);
}

.lp-intro-container {
  max-width: 1100px;
  margin: 0 auto;
}

.lp-intro-title {
  font-size: clamp(1.8rem, 3vw, 2.4rem);
  font-weight: 800;
  color: var(--text-primary);
  margin-bottom: 1rem;
}

.lp-intro-text {
  color: var(--text-secondary);
  line-height: 1.75;
  font-size: 1rem;
  max-width: 820px;
  margin-bottom: 1rem;
}

.lp-intro-text:last-of-type {
  margin-bottom: 2.5rem;
}

.lp-intro-text :deep(strong),
.lp-intro-text strong {
  color: var(--text-primary);
}

/* Conclusion */
.lp-conclusion {
  padding: 90px 8% 110px;
  background: var(--gradient-section);
}

.lp-conclusion-container {
  max-width: 900px;
  margin: 0 auto;
}

.lp-conclusion h2 {
  font-size: clamp(1.8rem, 3vw, 2.4rem);
  font-weight: 800;
  color: var(--text-primary);
  margin-bottom: 1.4rem;
}

.lp-conclusion p {
  color: var(--text-secondary);
  line-height: 1.8;
  margin-bottom: 1.1rem;
}

.lp-conclusion strong {
  color: var(--text-primary);
}

.lp-signature {
  margin-top: 2.5rem;
  padding-top: 1.4rem;
  border-top: 1px solid var(--border-color);
  font-style: italic;
  color: var(--text-muted);
}

@media (max-width: 900px) {
  .lp-hero {
    padding: 120px 6% 70px;
  }

  .lp-hero-meta {
    grid-template-columns: repeat(2, 1fr);
  }

  .lp-intro,
  .lp-conclusion {
    padding: 70px 6%;
  }
}

@media (max-width: 540px) {
  .lp-hero-meta {
    grid-template-columns: 1fr;
  }
}
</style>
