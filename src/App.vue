<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import HomeView from './views/HomeView.vue'
import AboutView from './views/AboutView.vue'
import SkillsView from './views/SkillsView.vue'
import ProjectsView from './views/ProjectsView.vue'
import ExperienceView from './views/ExperienceView.vue'
import ContactView from './views/ContactView.vue'

// Fitur untuk buka-tutup menu di layar HP
const isMenuOpen = ref(false)
const closeMenu = () => {
  isMenuOpen.value = false
}

// Fitur untuk mendeteksi section yang sedang aktif di layar
const activeSection = ref('home')

onMounted(() => {
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        activeSection.value = entry.target.id
      }
    })
  }, {
    rootMargin: '-30% 0px -70% 0px' 
  })

  const sections = document.querySelectorAll('.scroll-section')
  sections.forEach(section => observer.observe(section))

  onUnmounted(() => {
    sections.forEach(section => observer.unobserve(section))
  })
})
</script>

<template>
  <!-- Jadi ini — video dibungkus wrapper -->
<div class="global-bg-wrapper">
  <video autoplay loop muted playsinline class="global-bg-video">
    <source src="./assets/bg-91.mp4" type="video/mp4">
  </video>
</div>
<div class="global-video-overlay"></div>

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

html { scroll-behavior: smooth; }

::-webkit-scrollbar { width: 10px; }
::-webkit-scrollbar-track { background: #07130f; }
::-webkit-scrollbar-thumb { background: rgba(16, 185, 129, 0.3); border-radius: 10px; }
::-webkit-scrollbar-thumb:hover { background: rgba(16, 185, 129, 0.8); }

::selection { background-color: rgba(16, 185, 129, 0.3); color: #fff; }

:root {
  --bg-color: transparent; 
  --card-bg: rgba(18, 43, 32, 0.5); 
  --accent-color: #10b981;
  --text-primary: #f8fafc;
  --text-secondary: #94a3b8;
}

* { margin: 0; padding: 0; box-sizing: border-box; }

html, body {
  background-color: #05100c; 
  color: var(--text-primary);
  font-family: 'Inter', sans-serif; 
  -webkit-font-smoothing: antialiased;
}

/* ========================================================= */
/* --- KODE VIDEO BACKGROUND GLOBAL (REVISI GPU + 110%) --- */
/* ========================================================= */
/* ========================================================= */
/* --- KODE VIDEO BACKGROUND GLOBAL (UKURAN NORMAL) --- */
/* ========================================================= */
/* ========================================================= */
/* --- KODE VIDEO BACKGROUND GLOBAL (BALIK KE 110% ANTI-BUG) --- */
/* ========================================================= */
/* ========================================================= */
/* --- KODE VIDEO BACKGROUND GLOBAL (UKURAN NORMAL) --- */
/* ========================================================= */
/* ========================================================= */
/* --- KODE VIDEO BACKGROUND GLOBAL (BATAS TOLERANSI 108%) --- */
/* ========================================================= */
/* ========================================================= */
/* --- REVISI TOTAL: KODE VIDEO GLOBAL ANTI-TV BUTUT --- */
/* ========================================================= */
.global-bg-wrapper {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 0;
  overflow: hidden;           /* ini yang kunci — clip di wrapper */
  transform: translateZ(0);   /* GPU layer di wrapper, bukan video */
}

.global-bg-video {
  position: absolute;
  top: 50%;
  left: 50%;
  min-width: 100%;
  min-height: 100%;
  width: auto;
  height: auto;
  transform: translate(-50%, -50%);  /* centering tanpa GPU trick */
  object-fit: cover;
  pointer-events: none;
}

.global-video-overlay {
  position: fixed;
  inset: 0;
  background: rgba(10, 15, 25, 0.6);
  z-index: 1;
  pointer-events: none;
}


.section-subtitle, .typing-text, code { font-family: 'Fira Code', monospace; }

.app-container { min-height: 100vh; display: flex; flex-direction: column; position: relative; z-index: 2; }

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

.nav-links { display: flex; gap: 2.5rem; }
.nav-links a {
  text-decoration: none;
  color: var(--text-secondary);
  font-weight: 500;
  font-size: 0.95rem;
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

/* --- EFEK MENU AKTIF SAAT DI-SCROLL --- */
.nav-links a.active-link {
  color: var(--accent-color); 
  font-weight: 600; 
}
.nav-links a.active-link::after {
  width: 100%;
}

/* HAMBURGER MENU (Sembunyi di Laptop) */
.hamburger {
  display: none;
  flex-direction: column;
  cursor: pointer;
  gap: 5px;
  z-index: 1001;
}
.hamburger span {
  width: 25px; height: 3px; background-color: var(--text-primary);
  border-radius: 5px; transition: all 0.3s ease;
}

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

/* KODE RESPONSIVITAS UNTUK HP / TABLET */
@media (max-width: 768px) {
  .navbar { padding: 1.2rem 5%; }
  .content-wrapper { padding: 0 5%; }
  
  /* Munculkan tombol Hamburger */
  .hamburger { display: flex; }
  
  /* Animasi Tombol Hamburger jadi X */
  .hamburger.active span:nth-child(1) { transform: translateY(8px) rotate(45deg); }
  .hamburger.active span:nth-child(2) { opacity: 0; }
  .hamburger.active span:nth-child(3) { transform: translateY(-8px) rotate(-45deg); }

  /* Navbar menyamping (Slide-in Menu) */
  .nav-links {
    position: fixed; top: 0; right: -100%; width: 70vw; height: 100vh;
    background-color: rgba(5, 16, 12, 0.95);
    flex-direction: column; justify-content: center; align-items: center;
    transition: right 0.4s ease; box-shadow: -5px 0 15px rgba(0,0,0,0.5);
  }
  .nav-links.nav-active { right: 0; }
  .nav-links a { font-size: 1.2rem; }
}
</style>