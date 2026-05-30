<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import HomeView from './views/HomeView.vue'
import AboutView from './views/AboutView.vue'
import SkillsView from './views/SkillsView.vue'
import ProjectsView from './views/ProjectsView.vue'
import ExperienceView from './views/ExperienceView.vue'
import ContactView from './views/ContactView.vue'

const isMenuOpen = ref(false)
const closeMenu = () => {
  isMenuOpen.value = false
}

const activeSection = ref('home')

onMounted(() => {
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        activeSection.value = entry.target.id
      }
    })
  }, {
    rootMargin: '-30% 0px -70% 0px',
    root: document.querySelector('.app-container')
  })

  const sections = document.querySelectorAll('.scroll-section')
  sections.forEach(section => observer.observe(section))

  onUnmounted(() => {
    sections.forEach(section => observer.unobserve(section))
  })
})
</script>

<template>
  <div class="global-bg-wrapper">
    <video autoplay loop muted playsinline class="global-bg-video">
      <source src="./assets/bg-2.mp4" type="video/mp4">
    </video>
    <div class="global-video-overlay"></div>
  </div>

  <div class="app-container">
    <nav class="navbar">
      <div class="nav-brand">Krisna.<span>Data</span></div>
      
      <div class="hamburger" @click="isMenuOpen = !isMenuOpen" :class="{ active: isMenuOpen }">
        <span></span>
        <span></span>
        <span></span>
      </div>

      <div class="nav-links" :class="{ 'nav-active': isMenuOpen }">
        <a href="#home" @click="closeMenu" :class="{ 'active-link': activeSection === 'home' }">Home</a>
        <a href="#about" @click="closeMenu" :class="{ 'active-link': activeSection === 'about' }">About</a>
        <a href="#skills" @click="closeMenu" :class="{ 'active-link': activeSection === 'skills' }">Skills</a>
        <a href="#projects" @click="closeMenu" :class="{ 'active-link': activeSection === 'projects' }">Projects</a>
        <a href="#experience" @click="closeMenu" :class="{ 'active-link': activeSection === 'experience' }">Experience</a>
        <a href="#contact" @click="closeMenu" :class="{ 'active-link': activeSection === 'contact' }">Contact</a>
      </div>
    </nav>

    <main class="content-wrapper">
      <div id="home" class="scroll-section"><HomeView /></div>
      <div id="about" class="scroll-section"><AboutView /></div>
      <div id="skills" class="scroll-section"><SkillsView /></div>
      <div id="projects" class="scroll-section"><ProjectsView /></div>
      <div id="experience" class="scroll-section"><ExperienceView /></div>
      <div id="contact" class="scroll-section"><ContactView /></div>
    </main>

    <footer class="footer">
      <p>&copy; 2026 Krisna Dwipayana. All rights reserved.</p>
      <p class="footer-sub">Designed & Built with Vue.js</p>
    </footer>
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Fira+Code:wght@400;500&family=Inter:wght@300;400;500;600;700&display=swap');

::selection { background-color: rgba(16, 185, 129, 0.3); color: #fff; }

:root {
  --bg-color: transparent;
  --card-bg: rgba(18, 43, 32, 0.5);
  --accent-color: #10b981;
  --text-primary: #f8fafc;
  --text-secondary: #94a3b8;
}

* { margin: 0; padding: 0; box-sizing: border-box; }

/* KUNCI FIX GLITCH: body tidak scroll, scroll dipindah ke .app-container */
html, body {
  background-color: #05100c; 
  color: var(--text-primary);
  font-family: 'Inter', sans-serif; 
  -webkit-font-smoothing: antialiased;
  
  /* --- TAMBAHAN KUNCI ANTI-SCROLL SAMPING --- */
  overflow-x: hidden; 
  width: 100%;
}

/* Video benar-benar diam, tidak perlu di-composite ulang saat scroll */
.global-bg-wrapper {
  position: fixed;
  inset: 0;
  z-index: 0;
  overflow: hidden;
  transform: translateZ(0);
}

.global-bg-video {
  position: absolute;
  top: 50%;
  left: 50%;
  min-width: 100%;
  min-height: 100%;
  width: auto;
  height: auto;
  transform: translate(-50%, -50%);
  object-fit: cover;
  pointer-events: none;
}

/* Overlay digabung ke dalam wrapper, tidak perlu fixed terpisah */
.global-video-overlay {
  position: absolute;
  inset: 0;
  background: rgba(10, 15, 25, 0.6);
  pointer-events: none;
}

.section-subtitle, .typing-text, code { font-family: 'Fira Code', monospace; }

/* app-container yang scroll, bukan body */
.app-container {
  position: fixed;
  inset: 0;
  z-index: 2;
  overflow-y: auto;
  overflow-x: hidden; /* ← FIX: mencegah scroll ke samping */
  display: flex;
  flex-direction: column;
  scroll-behavior: smooth;
}

/* Scrollbar custom di app-container */
.app-container::-webkit-scrollbar { width: 10px; }
.app-container::-webkit-scrollbar-track { background: #07130f; }
.app-container::-webkit-scrollbar-thumb { background: rgba(16, 185, 129, 0.3); border-radius: 10px; }
.app-container::-webkit-scrollbar-thumb:hover { background: rgba(16, 185, 129, 0.8); }

/* NAVBAR */
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1.2rem 10%;
  background-color: rgba(5, 16, 12, 0.4);
  backdrop-filter: blur(12px);
  position: sticky;
  top: 0;
  z-index: 1000;
  border-bottom: 1px solid rgba(16, 185, 129, 0.1);
}

.nav-brand { font-size: 1.6rem; font-weight: 700; }
.nav-brand span { color: var(--accent-color); }

/* MENU HAMBURGER (Selalu Tampil) */
.hamburger {
  display: flex; 
  flex-direction: column;
  cursor: pointer;
  gap: 5px;
  z-index: 1001;
}
.hamburger span {
  width: 25px; height: 3px; background-color: var(--text-primary);
  border-radius: 5px; transition: all 0.3s ease;
}

/* Animasi Hamburger -> X (Dikeluarkan dari @media agar jalan di laptop) */
.hamburger.active span:nth-child(1) { transform: translateY(8px) rotate(45deg); }
.hamburger.active span:nth-child(2) { opacity: 0; }
.hamburger.active span:nth-child(3) { transform: translateY(-8px) rotate(-45deg); }

/* SLIDE-IN MENU UNTUK LAPTOP & HP */
.nav-links {
  position: fixed; 
  top: 0; 
  right: -100%; /* Sembunyi di kanan */
  width: 350px; /* Lebar menu di laptop */
  height: 100vh;
  background-color: rgba(5, 16, 12, 0.98);
  backdrop-filter: blur(15px);
  display: flex;
  flex-direction: column; 
  justify-content: center; 
  align-items: center;
  gap: 2.5rem;
  transition: right 0.4s ease; 
  box-shadow: -5px 0 15px rgba(0,0,0,0.5);
  z-index: 1000;
}

.nav-links.nav-active { right: 0; } /* Muncul saat aktif */

.nav-links a {
  text-decoration: none;
  color: var(--text-secondary);
  font-weight: 500;
  font-size: 1.2rem;
  transition: all 0.3s ease;
  position: relative;
}
.nav-links a:hover { color: var(--accent-color); }
.nav-links a::after {
  content: ''; position: absolute; width: 0; height: 2px;
  bottom: -4px; left: 0; background-color: var(--accent-color);
  transition: width 0.3s ease;
}
.nav-links a:hover::after { width: 100%; }

.nav-links a.active-link { color: var(--accent-color); font-weight: 600; }
.nav-links a.active-link::after { width: 100%; }

.content-wrapper { padding: 0 10%; flex-grow: 1; }
.scroll-section { scroll-margin-top: 80px; padding-bottom: 6rem; }

.footer {
  text-align: center; padding: 2rem 10%;
  border-top: 1px solid rgba(16, 185, 129, 0.1);
  background-color: rgba(5, 16, 12, 0.4);
  margin-top: auto;
}
.footer p { color: var(--text-secondary); font-size: 0.9rem; }
.footer .footer-sub { font-size: 0.8rem; margin-top: 0.5rem; opacity: 0.7; }

/* RESPONSIVITAS KHUSUS HP */
@media (max-width: 768px) {
  .navbar { padding: 1.2rem 5%; }
  .content-wrapper { padding: 0 5%; }

  /* Di HP, sidebar dibikin lebih sempit menyesuaikan layar */
  .nav-links {
    width: 70vw; 
  }
}
</style>