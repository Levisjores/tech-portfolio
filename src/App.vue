<template>
  <div id="app">
    <!-- NAVBAR -->
    <nav class="navbar">
      <div class="nav-inner">
        <div class="logo">Genie Levis's Portfolio</div>

        <div class="hamburger" @click="menuOpen = !menuOpen">☰</div>

        <ul :class="['nav-links', { show: menuOpen }]">
          <li class="" @click="changeTab('about')">À propos</li>
          <li @click="changeTab('skills')">Compétences</li>
          <li @click="changeTab('education')">Formation</li>
          <li @click="changeTab('projects')">Projets</li>
          <li @click="changeTab('contact')">Contact</li>
        </ul>
      </div>
    </nav>

    <!-- CONTENU -->
    <main class="main">
      <section v-if="activeTab==='about'" class="section">
        <div class="content-box fade-in">
          <h1>Salut, moi c’est NJIMI NJEUMEN Levis Jores</h1>
          <p class="subtitle">Développeur Web • Ingénieur Réseau</p>
          <div class="skills-container">
            <div class="skills-left">
            <div class="card">
              <h1>
                Profil
              </h1>
              <p style="font-family: 'Times New Roman', Times, serif; font-weight: bold; color: black; ">
                Jeune dynamique et passionné par les nouvelles technologies, la programmation, 
                les Réseaux et l'intelligence artificielle
              </p>
            </div>
            </div>
            <div class="skills-right">
              <div class="skills">
                <img src="../src/assets/soutenance.jpg" alt="ma photo" height="550" width="500" class="photopresentation">
              </div>
            </div>
          </div>

        </div>
      </section>

      <section v-if="activeTab==='skills'" class="section">
        <div class="content-box fade-in">
          <h1>Compétences</h1>
          <div class="skills-container">
            <div class="skills-left">
              <div class="card skill" v-for="skill in skills" @click="selectSkill(skill)" :class="{ active: selectedSkill?.name === skill.name }">
                <div class="skill-name">{{ skill.name }}</div>

                <!-- Inline details shown on mobile under the clicked skill -->
                <div class="skill-inline-details" v-if="selectedSkill?.name === skill.name" :key="animationKey">
                  <div class="skill-details">
                    <h3>{{ selectedSkill.name }}</h3>
                    <p class="description">{{ selectedSkill.details }}</p>
                    <div class="level">
                      <div class="level-bar">
                        <div class="level-fill" :style="{ width: selectedSkill.level + '%' }"></div>
                      </div>
                      <p class="level-text">Niveau: {{ selectedSkill.level }}%</p>
                    </div>
                  </div>
                </div>
              </div>
            </div>

            <div class="skills-right">
              <div class="skill-details" v-if="selectedSkill" :key="animationKey">
                <h3>{{ selectedSkill.name }}</h3>
                <p class="description">{{ selectedSkill.details }}</p>
                <div class="level">
                  <div class="level-bar">
                    <div class="level-fill" :style="{ width: selectedSkill.level + '%' }"></div>
                  </div>
                  <p class="level-text">Niveau: {{ selectedSkill.level }}%</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <section v-if="activeTab==='education'" class="section">
        <div class="content-box fade-in">
          <h1>Formation</h1>
          <div class="card">Licence Informatique – Réseaux & Systèmes</div>
        </div>
      </section>

      <section v-if="activeTab==='projects'" class="section">
        <div class="content-box fade-in">
          <h1>Projets</h1>
          <div class="projects-container">
            <div class="projects-left">
              <div class="card project" v-for="project in projects" @click="selectProject(project)" :class="{ active: selectedProject?.name === project.name }">
                <div class="project-name">{{ project.name }}</div>

                <!-- Inline project details shown on mobile under the clicked project -->
                <div class="project-inline-details" v-if="selectedProject?.name === project.name" :key="animationKey">
                  <div class="project-details">
                    <h3>{{ selectedProject.name }}</h3>
                    <p class="description">{{ selectedProject.description }}</p>
                    <div class="technologies">
                      <span v-for="tech in selectedProject.technologies" :key="tech" class="tech-tag">{{ tech }}</span>
                    </div>
                    <p class="date">{{ selectedProject.date }}</p>
                  </div>
                </div>
              </div>
            </div>

            <div class="projects-right">
              <div class="project-details" v-if="selectedProject" :key="animationKey">
                <h3>{{ selectedProject.name }}</h3>
                <p class="description">{{ selectedProject.description }}</p>
                <div class="technologies">
                  <span v-for="tech in selectedProject.technologies" :key="tech" class="tech-tag">{{ tech }}</span>
                </div>
                <p class="date">{{ selectedProject.date }}</p>
              </div>
            </div>
          </div>
        </div>
      </section>

      <section v-if="activeTab==='contact'" class="section">
        <div class="content-box fade-in" style="display: inline;">
          <h1> Contact</h1>
          <div class="skills" >
            WhatsApp: <a href="">+237 653710473 </a>
          </div>
          <div class="skills">
            Email / WhatsApp
          </div>
          <div class="card">Email / WhatsApp</div>
          <div class="card">Email / WhatsApp</div>
        </div>
      </section>
    </main>
  </div>
</template>

<script setup>
import { ref } from "vue"
const activeTab = ref("about")
const menuOpen = ref(false)

const skills = [
  { name: 'JavaScript', details: 'Maîtrise avancée de JavaScript. Expérience en développement côté client et serveur avec Node.js.', level: 90 },
  { name: 'Vue.js', details: 'Expertise en Vue 3 avec Composition API. Création de composants réutilisables et gestion d\'état complexe.', level: 85 },
  { name: 'CSS', details: 'Design responsive, animations CSS avancées, Flexbox et Grid. Création de interfaces modernes.', level: 88 },
  { name: 'Python', details: 'Développement backend, scripts d\'automatisation, et machine learning avec TensorFlow.', level: 80 },
  { name: 'React', details: 'Hooks, Context API, et gestion d\'état. Intégration d\'APIs et optimisation de performance.', level: 75 },
];

const selectedSkill = ref(null);
const animationKey = ref(0);

const projects = [
  { 
    name: 'Projet IA Réseau', 
    description: 'Une application intelligente pour l\'analyse et la visualisation des réseaux informatiques avec IA.',
    technologies: ['Python', 'TensorFlow', 'Vue.js', 'Node.js'],
    date: 'Janvier 2024'
  },
  { 
    name: 'Plateforme Scolaire', 
    description: 'Plateforme complète de gestion scolaire avec tableau de bord et suivi des étudiants.',
    technologies: ['Vue.js', 'Firebase', 'Tailwind CSS'],
    date: 'Novembre 2023'
  },
  { 
    name: 'Chat en Temps Réel', 
    description: 'Application de messagerie instantanée avec support des vidéos et partage de fichiers.',
    technologies: ['WebSocket', 'React', 'Express.js'],
    date: 'Septembre 2023'
  },
];

const selectedProject = ref(null);

function changeTab(tab) {
  activeTab.value = tab
  menuOpen.value = false
}

const selectSkill = (skill) => {
  selectedSkill.value = skill;
  animationKey.value++;
};

const selectProject = (project) => {
  selectedProject.value = project;
  animationKey.value++;
};
</script>

<style>
.photopresentation
{
  border-radius: 8%;
  box-shadow: 0 15px 35px rgba(6, 148, 243, 0.5);
  border-style: inset;

}
/* RESET IMPORTANT */
* {
  box-sizing: border-box;
}

#app {

  margin: 0;
  padding: 0;
  font-family: 'Segoe UI', sans-serif;
}

/* FOND GLOBAL */
#app {
  background: linear-gradient(130deg, #667eea 50%, #764ba2 100%);
  min-height: 100vh;
  min-width: 100%;
}

/* NAVBAR */
.navbar {
  width: 100%;
  position: fixed;
  top: 0;
  background: rgba(0,0,0,0.25);
  backdrop-filter: blur(8px);
  z-index: 1000;
}

.nav-inner {
  width: 100%;
  padding: 15px 5%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  color: white;
}


.logo {
  font-weight: bold;
  font-size: 1.2em;
}

.nav-links {
  list-style: none;
  display: flex;
  gap: 25px;
}

.nav-links li {
  cursor: pointer;
  padding: 6px 10px;
  border-radius: 6px;
  transition: 0.3s;
}

.nav-links li:hover {
  background: linear-gradient(135deg, #4facfe, #00f2fe);
}

.hamburger {
  display: none;
  font-size: 1.6em;
  cursor: pointer;
}

/* MAIN */
.main {
  padding-top: 100px;
  width: 100%;
}

/* SECTION PREND TOUTE LA LARGEUR */
.section {
  width: 100%;
  padding: 0px 0%;
  display: flex;
  justify-content: center;
}


/* CONTENU CENTRÉ */
.content-box {
  width: 100%;
  text-align: center;
  color: rgb(255, 255, 255);
}


.subtitle {
  opacity: 0.9;
  margin-bottom: 20px;
}

/* CARDS */
.card {
  background: white;
  color: #333;
  padding: 25px;
  border-radius: 18px;
  box-shadow: 0 15px 35px rgba(0,0,0,0.1);
  margin-top: 20px;
}

/* GRID */
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 20px;
  margin-top: 20px;
}

/* COMPETENCES CONTAINER */
.skills-container {
  display: flex;
  /*gap: 30px;*/
  margin-top: 30px;
}


.skills-left {
  width: 50%;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 20px;

}

.skills-right {
  width: 50%;
  display: flex;
  align-items: flex-start;
  padding-left: 20px;
}

.skill {
  background: linear-gradient(135deg, #4facfe 50%, #1db6a9);
  color: white;
  font-weight: bold;
  cursor: pointer;
  transition: all 0.3s ease;
  border: 3px solid transparent;
}

.skill:hover {
background: linear-gradient(135deg, #2cb681 50%, #51f704);
  transform: translateY(-5px);
  box-shadow: 0 20px 40px rgba(0,0,0,0.2);
}

.skill.active {
background: linear-gradient(135deg, #2cb681 50%, #51f704);
  border-color: white;
  box-shadow: 0 25px 50px rgba(79, 172, 254, 0.4);
}

.skill-details {
  background: rgba(255, 255, 255, 0.95);
  color: #333;
  padding: 20px;
  border-radius: 18px;
  box-shadow: 0 20px 50px rgba(0,0,0,0.15);
  animation: slideIn 0.5s ease;
  width: 100%;
  
}

/* Inline details hidden by default (desktop) — shown on mobile via media query */
.skill-inline-details {
  display: none;
}

/* Inline project details hidden by default (desktop) */
.project-inline-details {
  display: none;
}

.skill-details h3 {
  font-size: 1.8em;
  color: #667eea;
  margin-bottom: 15px;
}

.skill-details .description {
  font-size: 1.1em;
  line-height: 1.6;
  color: #555;
  margin-bottom: 30px;
}

.level {
  margin-top: 30px;
}

.level-bar {
  background: #e0e0e0;
  border-radius: 10px;
  height: 12px;
  overflow: hidden;
  margin-bottom: 12px;
}

.level-fill {
  background: linear-gradient(90deg, #4facfe, #00f2fe);
  height: 100%;
  transition: width 0.6s ease;
}

.level-text {
  font-size: 0.95em;
  color: #999;
  font-weight: 600;
}

/* PROJETS CONTAINER */
.projects-container {
  display: flex;
  gap: 30px;
  margin-top: 30px;
  width: 100%;
  max-width: 1200px;
  margin-left: auto;
  margin-right: auto;
}

.projects-left {
  width: 50%;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 20px;
}

.projects-right {
  width: 50%;
}

.project {
  background: linear-gradient(135deg, #f093fb, #f5576c);
  color: white;
  font-weight: bold;
  cursor: pointer;
  transition: all 0.3s ease;
  border: 3px solid transparent;
}

.project:hover {
  transform: translateY(-5px);
  box-shadow: 0 20px 40px rgba(0,0,0,0.2);
}

.project.active {
  border-color: white;
  box-shadow: 0 25px 50px rgba(245, 87, 108, 0.4);
}

.project-details {
  background: rgba(255, 255, 255, 0.95);
  color: #333;
  padding: 40px;
  border-radius: 18px;
  box-shadow: 0 20px 50px rgba(0,0,0,0.15);
  animation: slideIn 0.5s ease;
  width: 100%;
}

.project-details h3 {
  font-size: 1.8em;
  color: #667eea;
  margin-bottom: 15px;
}

.project-details .description {
  font-size: 1.1em;
  line-height: 1.6;
  color: #555;
  margin-bottom: 25px;
}

.technologies {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin-bottom: 20px;
}

.tech-tag {
  background: linear-gradient(135deg, #667eea, #764ba2);
  color: white;
  padding: 8px 16px;
  border-radius: 20px;
  font-size: 0.9em;
  font-weight: 600;
}

.project-details .date {
  color: #999;
  font-size: 0.95em;
  margin-top: 20px;
}

@keyframes slideIn {
  from {
    opacity: 0;
    transform: translateX(30px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

/* ANIMATION */
.fade-in {
  animation: fadeIn 0.5s ease-in;
}

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}

/* MOBILE */
@media (max-width: 768px) {
  .hamburger {
    display: block;
  }

  .nav-links {
    position: absolute;
    right: 20px;
    top: 65px;
    flex-direction: column;
    background: rgba(0,0,0,0.9);
    padding: 15px;
    border-radius: 10px;
    display: none;
  }

  .nav-links.show {
    display: flex;
  }

  .skills-container,
  .projects-container {
    flex-direction: column;
  }

  .skills-left,
  .projects-left,
  .skills-right,
  .projects-right {
    width: 100%;
  }

  /* Remove left margin and add inner padding so items fit the screen */
  .skills-left,
  .projects-left {
    margin-left: 0;
    padding: 0 5%;
  }

  /* Add some horizontal padding to the content box on small screens */
  .content-box {
    padding-left: 5%;
    padding-right: 5%;
  }

  /* Hide the right-side details on mobile — we'll show inline details instead */
  .skills-right {
    display: none;
  }

  /* Hide right-side details for skills and projects on mobile */
  .skills-right {
    display: none;
  }

  .projects-right {
    display: none;
  }

  /* Inline details placed under each skill / project card on mobile */
  .skill-inline-details,
  .project-inline-details {
    display: block;
    margin-top: 12px;
  }
}
.content {
  display: flex;
}

/* DESKTOP: ensure skills/projects take full available width */
@media (min-width: 769px) {
  .projects-container {
    max-width: none;
    margin-left: 0;
    margin-right: 0;
    width: 100%;
    gap: 40px;
  }

  .skills-container {
    width: 100vw;
    gap: 40px;
  }

  /* Make content use full width on desktop and keep small horizontal padding */
  .content-box {
    
    width: 100vw;
    margin-left: 0;
    margin-right: 0;
    padding-left: 3%;
    padding-right: 3%;
  }

  /* Ensure the two-column layout fills the row and is centered */
  .skills-container,
  .projects-container {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    width: 100%;
  }

  .skills-left,
  .projects-left {
    flex: 0 0 48%;
    width: 48%;
    margin-left: 0;
    display: block;
    grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
    gap: 20px;
  }

  .skills-right,
  .projects-right {
    flex: 0 0 48%;
    width: 48%;
    margin-left: 0;
    display: block;
  }
}
</style>
