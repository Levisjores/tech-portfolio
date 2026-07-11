<template>
  <div class="relative min-h-screen overflow-x-hidden bg-slate-950 text-slate-50">
    <div class="pointer-events-none absolute inset-0 overflow-hidden">
      <div class="absolute left-1/2 top-0 h-80 w-80 -translate-x-1/2 rounded-full bg-cyan-500/10 blur-3xl"></div>
      <div class="absolute right-0 top-1/3 h-64 w-64 rounded-full bg-violet-500/10 blur-3xl"></div>
    </div>

    <header class="sticky top-0 z-50 border-b border-white/10 bg-slate-950/75 backdrop-blur-xl">
      <nav class="mx-auto flex max-w-7xl items-center justify-between px-4 py-4 sm:px-6 lg:px-8">
        <button class="flex items-center gap-2 text-sm font-semibold tracking-[0.3em] text-cyan-200 uppercase" @click="changeTab('home')">
          <span class="inline-flex h-9 w-9 items-center justify-center rounded-xl bg-gradient-to-br from-cyan-400 to-violet-500">L</span>
          Levis
        </button>

        <button class="inline-flex items-center rounded-xl border border-white/10 p-2 text-slate-100 lg:hidden" @click="menuOpen = !menuOpen">
          <span class="text-xl">☰</span>
        </button>

        <ul :class="['absolute left-4 right-4 top-16 flex-col gap-2 rounded-2xl border border-white/10 bg-slate-900/95 p-3 shadow-2xl lg:static lg:flex lg:flex-row lg:items-center lg:gap-6 lg:border-0 lg:bg-transparent lg:p-0 lg:shadow-none', menuOpen ? 'flex' : 'hidden lg:flex']">
          <li v-for="item in navItems" :key="item.href">
            <button
              class="w-full rounded-xl px-4 py-2 text-sm text-slate-300 transition hover:bg-white/5 hover:text-white lg:w-auto"
              :class="activeTab === item.href ? 'bg-cyan-500/10 text-cyan-200' : ''"
              @click="changeTab(item.href)"
            >
              {{ item.label }}
            </button>
          </li>
        </ul>
      </nav>
    </header>

    <main>
      <section id="home" class="relative px-4 pb-20 pt-16 sm:px-6 lg:px-8 lg:pb-28 lg:pt-24">
        <div class="mx-auto grid max-w-7xl items-center gap-16 lg:grid-cols-[1.1fr_0.9fr]">
          <div class="animate-[fadeUp_0.8s_ease-out]">
            <span class="inline-flex rounded-full border border-cyan-400/30 bg-cyan-400/10 px-4 py-1 text-sm text-cyan-100">Développeur web • Réseaux • IA</span>
            <h1 class="mt-6 text-5xl font-black tracking-tight text-white sm:text-6xl">
              Bonjour, je suis <span class="bg-gradient-to-r from-cyan-300 via-sky-400 to-violet-400 bg-clip-text text-transparent">Levis Jores</span>
            </h1>
            <p class="mt-6 max-w-2xl text-lg leading-8 text-slate-300">
              Je conçois des solutions digitales modernes, performantes et intelligentes pour les entreprises, les projets éducatifs et les innovations technologiques.
            </p>
            <div class="mt-8 flex flex-col gap-3 sm:flex-row">
              <button class="rounded-2xl bg-gradient-to-r from-cyan-500 to-violet-500 px-6 py-3 font-semibold text-slate-950 transition hover:scale-[1.02]" @click="changeTab('projects')">Voir mes projets</button>
              <button class="rounded-2xl border border-white/15 px-6 py-3 font-semibold text-white transition hover:bg-white/5" @click="changeTab('contact')">Me contacter</button>
            </div>
            <div class="mt-10 grid max-w-2xl gap-4 sm:grid-cols-3">
              <div class="rounded-2xl border border-white/10 bg-white/5 p-4 backdrop-blur-sm">
                <p class="text-3xl font-bold text-white">1+</p>
                <p class="text-sm text-slate-400">années d'expérience</p>
              </div>
              <div class="rounded-2xl border border-white/10 bg-white/5 p-4 backdrop-blur-sm">
                <p class="text-3xl font-bold text-white">03+</p>
                <p class="text-sm text-slate-400">projets réalisés</p>
              </div>
              <div class="rounded-2xl border border-white/10 bg-white/5 p-4 backdrop-blur-sm">
                <p class="text-3xl font-bold text-white">100%</p>
                <p class="text-sm text-slate-400">passion & rigueur</p>
              </div>
            </div>
          </div>

          <div class="relative animate-[fadeUp_1s_ease-out]">
            <div class="absolute inset-0 rounded-[2rem] bg-gradient-to-br from-cyan-400/20 to-violet-500/20 blur-2xl"></div>
            <div class="relative overflow-hidden rounded-[2rem] border border-white/10 bg-slate-900/70 p-4 shadow-2xl shadow-cyan-500/5 backdrop-blur-xl">
              <img src="./assets/soutenance.jpg" alt="Levis Jores" class="h-[520px] w-full rounded-[1.5rem] object-cover object-center" />
              <div class="absolute bottom-8 left-8 rounded-2xl border border-white/10 bg-slate-900/80 p-4 backdrop-blur-md">
                <p class="text-xs uppercase tracking-[0.3em] text-cyan-200">Disponible</p>
                <p class="mt-1 text-sm text-slate-100">Freelance / projets innovants</p>
              </div>
            </div>
          </div>
        </div>
      </section>

      <section id="about" class="px-4 py-20 sm:px-6 lg:px-8">
        <div class="mx-auto max-w-7xl rounded-[2rem] border border-white/10 bg-white/5 p-8 shadow-2xl shadow-slate-950/20 backdrop-blur-xl">
          <div class="grid gap-10 lg:grid-cols-[1.2fr_0.8fr]">
            <div>
              <p class="text-sm uppercase tracking-[0.3em] text-cyan-200">À propos</p>
              <h2 class="mt-3 text-3xl font-bold text-white">Un profil hybride entre développement, Administration réseau et intelligence artificielle</h2>
              <p class="mt-5 text-base leading-7 text-slate-300">
                Jeune développeur dynamique et passionné, j’aime transformer des idées complexes en solutions utiles, simples et performantes. Mon parcours mêle programmation, administration réseau et exploration des applications de l’intelligence artificielle.
              </p>
              <p class="mt-4 text-base leading-7 text-slate-300">
                Je travaille chaque jour à améliorer mes compétences, à apprendre les technologies émergentes et à créer des expériences numériques qui marquent.
              </p>
            </div>
            <div class="grid gap-4 sm:grid-cols-2 lg:grid-cols-1">
              <div class="rounded-2xl border border-white/10 bg-slate-900/70 p-5">
                <p class="text-sm text-cyan-200">Profil</p>
                <p class="mt-2 text-sm leading-6 text-slate-300">Développeur web, passionné de logique, d’architecture applicative et de résolution de problèmes.</p>
              </div>
              <div class="rounded-2xl border border-white/10 bg-slate-900/70 p-5">
                <p class="text-sm text-cyan-200">Vision</p>
                <p class="mt-2 text-sm leading-6 text-slate-300">Créer des outils qui allient performance, sécurité, simplicité d’usage et impact réel.</p>
              </div>
            </div>
          </div>
        </div>
      </section>

      <section id="skills" class="px-4 py-20 sm:px-6 lg:px-8">
        <div class="mx-auto max-w-7xl">
          <div class="mb-8 flex items-end justify-between gap-4">
            <div>
              <p class="text-sm uppercase tracking-[0.3em] text-cyan-200">Compétences</p>
              <h2 class="mt-3 text-3xl font-bold text-white">Technologies maîtrisées</h2>
            </div>
          </div>
          <div class="space-y-4">
            <div v-for="skill in skills" :key="skill.name" class="space-y-3">
              <button
                class="w-full rounded-2xl border p-5 text-left transition duration-300"
                :class="selectedSkill?.name === skill.name ? 'border-cyan-400/50 bg-gradient-to-r from-cyan-500/15 to-violet-500/15' : 'border-white/10 bg-white/5 hover:border-white/20 hover:bg-white/8'"
                @click="selectSkill(skill)"
              >
                <div class="flex items-center justify-between">
                  <span class="font-semibold text-white">{{ skill.name }}</span>
                  <span class="text-sm text-cyan-200">{{ skill.level }}%</span>
                </div>
              </button>

              <transition name="detail-fade" appear>
                <div v-if="selectedSkill?.name === skill.name" :key="animationKey" class="rounded-2xl border border-white/10 bg-slate-900/70 p-6 shadow-xl shadow-slate-950/20">
                  <div class="flex items-center gap-3">
                    <span class="inline-flex h-12 w-12 items-center justify-center rounded-2xl bg-gradient-to-br from-cyan-500 to-violet-500 text-sm font-semibold text-slate-950">{{ skill.name.slice(0, 2) }}</span>
                    <div>
                      <p class="text-xs uppercase tracking-[0.3em] text-cyan-200">Expertise</p>
                      <h3 class="text-xl font-semibold text-white">{{ skill.name }}</h3>
                    </div>
                  </div>
                  <p class="mt-4 text-base leading-7 text-slate-300">{{ skill.details }}</p>
                  <div class="mt-5">
                    <div class="flex items-center justify-between text-sm text-slate-400">
                      <span>Niveau</span>
                      <span>{{ skill.level }}%</span>
                    </div>
                    <div class="mt-2 h-3 overflow-hidden rounded-full bg-white/5">
                      <div class="h-full rounded-full bg-gradient-to-r from-cyan-400 to-violet-500 transition-all duration-700" :style="{ width: skill.level + '%' }"></div>
                    </div>
                  </div>
                </div>
              </transition>

            </div>
          </div>
        </div>
      </section>

      <section id="experience" class="px-4 py-20 sm:px-6 lg:px-8">
        <div class="mx-auto max-w-7xl">
          <div class="mb-8">
            <p class="text-sm uppercase tracking-[0.3em] text-cyan-200">Expériences</p>
            <h2 class="mt-3 text-3xl font-bold text-white">Parcours professionnel</h2>
          </div>
          <div class="grid gap-6 md:grid-cols-3">
            <article v-for="item in experiences" :key="item.title" class="rounded-[1.75rem] border border-white/10 bg-white/5 p-6 backdrop-blur-sm transition duration-300 hover:-translate-y-1 hover:bg-white/8">
              <p class="text-sm text-cyan-200">{{ item.period }}</p>
              <h3 class="mt-2 text-xl font-semibold text-white">{{ item.title }}</h3>
              <p class="mt-3 text-sm leading-6 text-slate-300">{{ item.description }}</p>
            </article>
          </div>
        </div>
      </section>

      <section id="projects" class="px-4 py-20 sm:px-6 lg:px-8">
        <div class="mx-auto max-w-7xl">
          <div class="mb-8">
            <p class="text-sm uppercase tracking-[0.3em] text-cyan-200">Projets</p>
            <h2 class="mt-3 text-3xl font-bold text-white">Réalisations récentes</h2>
          </div>
          <div class="space-y-4">
            <div v-for="project in projects" :key="project.name" class="space-y-3">
              <button
                class="w-full rounded-2xl border p-5 text-left transition duration-300"
                :class="selectedProject?.name === project.name ? 'border-violet-400/50 bg-gradient-to-r from-violet-500/15 to-cyan-500/15' : 'border-white/10 bg-white/5 hover:border-white/20 hover:bg-white/8'"
                @click="selectProject(project)"
              >
                <div class="flex items-center justify-between">
                  <span class="font-semibold text-white">{{ project.name }}</span>
                  <span class="text-sm text-violet-200">{{ project.date }}</span>
                </div>
              </button>

              <transition name="detail-fade" appear>
                <article v-if="selectedProject?.name === project.name" :key="animationKey" class="rounded-2xl border border-white/10 bg-slate-900/70 p-6 shadow-xl shadow-slate-950/20">
                  <p class="text-sm uppercase tracking-[0.3em] text-violet-200">Projet sélectionné</p>
                  <h3 class="mt-2 text-2xl font-semibold text-white">{{ project.name }}</h3>
                  <p class="mt-5 text-base leading-7 text-slate-300">{{ project.description }}</p>
                  <div class="mt-6 flex flex-wrap gap-2">
                    <span v-for="tech in project.technologies" :key="tech" class="rounded-full bg-white/5 px-3 py-1 text-sm text-slate-200">{{ tech }}</span>
                  </div>
                </article>
              </transition>
            </div>
          </div>
        </div>
      </section>

      <section id="contact" class="px-4 pb-20 pt-10 sm:px-6 lg:px-8">
        <div class="mx-auto max-w-7xl rounded-[2rem] border border-white/10 bg-gradient-to-br from-cyan-500/10 to-violet-500/10 p-8 backdrop-blur-xl">
          <div class="grid gap-8 lg:grid-cols-[1fr_0.9fr]">
            <div>
              <p class="text-sm uppercase tracking-[0.3em] text-cyan-200">Contact</p>
              <h2 class="mt-3 text-3xl font-bold text-white">Prêt à lancer votre prochain projet ?</h2>
              <p class="mt-4 max-w-2xl text-base leading-7 text-slate-300">Discutons de vos besoins, de vos idées et de la meilleure manière de les transformer en réalité.</p>
            </div>
            <div class="grid gap-4">
              <a href="mailto:njiminjeumenlevis@gmail.com" class="flex items-center justify-between rounded-2xl border border-white/10 bg-slate-900/70 p-4 text-slate-100 transition hover:bg-slate-800">
                <span>Email</span>
                <span class="text-sm text-cyan-200">njiminjeumenlevis@gmail.com</span>
              </a>
              <a href="https://wa.me/237673713395?text=Bonjour%20Levis" class="flex items-center justify-between rounded-2xl border border-white/10 bg-slate-900/70 p-4 text-slate-100 transition hover:bg-slate-800">
                <span>WhatsApp</span>
                <span class="text-sm text-cyan-200">+237 673 713 395</span>
              </a>
              <a href="https://github.com/Levisjores" target="_blank" class="flex items-center justify-between rounded-2xl border border-white/10 bg-slate-900/70 p-4 text-slate-100 transition hover:bg-slate-800">
                <span>GitHub</span>
                <span class="text-sm text-cyan-200">Levisjores</span>
              </a>
            </div>
          </div>
        </div>
      </section>
    </main>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const activeTab = ref('home')
const menuOpen = ref(false)
const animationKey = ref(0)

const navItems = [
  { label: 'Accueil', href: 'home' },
  { label: 'À propos', href: 'about' },
  { label: 'Compétences', href: 'skills' },
  { label: 'Expériences', href: 'experience' },
  { label: 'Projets', href: 'projects' },
  { label: 'Contact', href: 'contact' },
]

const skills = [
  { name: 'PHP natif', details: 'Maîtrise avancée du langage PHP natif pour le développement backend, la logique métier et l’intégration avec les bases de données.', level: 90 },
  { name: 'CodeIgniter', details: 'Création d’applications web robustes, maintenables et évolutives avec une architecture claire et performante.', level: 75 },
  { name: 'Laravel', details: 'Développement d’API REST, d’outils métier et d’applications sécurisées avec un backend moderne.', level: 60 },
  { name: 'JavaScript', details: 'Développement frontend interactif et optimisation des expériences utilisateur avec des bonnes pratiques solides.', level: 85 },
  { name: 'Vue.js', details: 'Conception d’interfaces dynamiques, réactives et modernes pour des applications web de qualité.', level: 70 },
  { name: 'Python', details: 'Scripts, automatisation, analyse de données et applications liées à l’intelligence artificielle.', level: 75 },
  { name: 'Flutter', details: 'Création d’interfaces mobiles modernes et performantes avec une approche cross-platform.', level: 60 },
]

const experiences = [
  {
    title: 'Développeur Full-Stack',
    period: 'Février 2026 — Aujourd’hui',
    description: 'Maintenance, amélioration et déploiement des mises à jour d\'une application de gestion d\'une agence de voyage.',
  },
  {
    title: 'Stagiaire réseau',
    period: 'Juillet 2025 — Septembre 2025',
    description: 'Assistance technique et support aux utilisateurs dans le cadre de l\'exploitation et de la maintenance des infrastructures réseau. étude et proposition d\'une solution d\'optimisation du routage réseau basé sur un algorithme d\intélligence artificielle.',
  },
  {
    title: 'Stagiaire en Développement Web',
    period: 'Juillet 2024 — Septembre 2024',
    description: 'Analyse et développement d\'une solution web de gestion d\'un établissement universitaire, incluant un dashboard de suivi, la gestion des étudiants, des notes j\'usqu\'à la génération des borderaux de notes et d\'autres documents pédagogiques.',
  },
]

const projects = [
  {
    name: 'Projet IA Réseau',
    description: 'Un système intelligent visant à optimiser le choix des chemins dans un réseau grâce à des mécanismes d’analyse et de décision automatisés et guidé par un agent d’intélligence artificielle, se basant sur le flux réseau en temps réel.',
    technologies: ['Python', 'Matplotlib', 'Numpy', 'Pandas', 'Scikit-learn', 'Tkinter'],
    date: '2025',
  },
  {
    name: 'Big Data Hadoop & Spark',
    description: 'Déploiement d’un cluster de trois nœuds pour le traitement et l’analyse de données massives avec une approche orientée apprentissage pratique.',
    technologies: ['Hadoop', 'Spark', 'YARN'],
    date: '2025',
  },
    {
    name: 'Plateforme Scolaire',
    description: 'Une solution complète de gestion universitaire incluant tableau de bord, gestion des étudiants, suivi des ressources pédagogiques.',
    technologies: ['HTML/CSS', 'MySQL', 'PHP', 'CodeIgniter'],
    date: '2024',
  },
]

const selectedSkill = ref(skills[0])
const selectedProject = ref(projects[0])

function changeTab(tab) {
  activeTab.value = tab
  menuOpen.value = false
  setTimeout(() => {
    const element = document.getElementById(tab)
    if (element) {
      element.scrollIntoView({ behavior: 'smooth', block: 'start' })
    }
  }, 100)
}

const selectSkill = (skill) => {
  selectedSkill.value = skill
  animationKey.value++
}

const selectProject = (project) => {
  selectedProject.value = project
  animationKey.value++
}
</script>

