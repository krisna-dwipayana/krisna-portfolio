<script setup>
import { ref, onMounted } from 'vue'

// Teks lengkap yang ingin diketik
const textToType = "Data Enthusiast & Business Intelligence"

// Variabel penampung teks yang sedang tampil
const typedText = ref('')

// Kecepatan ngetik (ms)
const typeSpeed = 100 

// Fungsi pengetikan
const type = (index = 0) => {
  if (index < textToType.length) {
    typedText.value += textToType.charAt(index)
    setTimeout(() => type(index + 1), typeSpeed)
  }
}

// Mulai ngetik pas halaman dibuka
onMounted(() => {
  setTimeout(() => {
    type()
  }, 500)
})
</script>

<template>
  <section class="home-hero">
    <div class="hero-text">
      <p class="greeting">Hello, I'm</p>
      <h1>Krisna <span>Dwipayana</span></h1>
      
      <h2 class="typing-text">
        {{ typedText }}<span class="cursor">|</span>
      </h2>
      
      <p class="description">
        An enthusiastic Information Technology student passionate about turning raw data into meaningful insights. Currently exploring the world of data analytics, machine learning, and data visualization through academic projects and self-learning. Eager to grow, collaborate, and contribute as a future data professional.
      </p>
      <div class="hero-buttons">
        <a href="#projects" class="hero-btn btn-primary">View Projects</a>
        <a href="/Freshgrad_KRISNA DWIPAYANA.pdf" download class="hero-btn btn-secondary">Download CV</a>
      </div>
    </div>

    <div class="hero-image">
      <div class="image-border">
        <img src="../assets/profile.jpeg" alt="Krisna Dwipayana" />
      </div>
    </div>
  </section>
</template>

<style scoped>
.home-hero {
  display: flex;
  align-items: center;
  justify-content: space-between;
  min-height: 80vh;
  gap: 2rem;
  position: relative;
  z-index: 1;
}

.hero-text {
  flex: 1;
}

.greeting {
  color: var(--accent-color);
  font-weight: 600;
  font-size: 1.2rem;
}

.hero-text h1 {
  font-size: 4rem;
  margin: 0.5rem 0;
}

.hero-text h1 span {
  color: var(--accent-color);
}

/* --- STYLE UNTUK EFEK NGETIK --- */
.hero-text h2 {
  font-size: 1.5rem;
  color: var(--text-secondary);
  margin-bottom: 1.5rem;
  min-height: 1.6em; /* Biar layout gak lompat pas teks masih kosong */
}

.typing-text { 
  font-family: 'Fira Code', monospace; 
  display: inline-block;
  position: relative;
}

.typing-text .cursor {
  color: var(--accent-color);
  margin-left: 2px;
  animation: blink 1s step-end infinite;
}

@keyframes blink {
  50% { opacity: 0; }
}
/* ------------------------------- */

.description {
  max-width: 500px;
  line-height: 1.6;
  color: var(--text-secondary);
  margin-bottom: 2rem;
  text-align: justify;
}

/* ========================================= */
/* --- STYLE TOMBOL ELEGAN (BARU) --- */
/* ========================================= */
.hero-buttons {
  display: flex;
  gap: 1.2rem;
  margin-top: 2rem;
  flex-wrap: wrap;
}

.hero-btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 12px 32px;
  font-size: 1rem;
  font-weight: 600;
  border-radius: 50px; 
  text-decoration: none;
  font-family: 'Inter', sans-serif;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  cursor: pointer;
  letter-spacing: 0.5px;
}

.btn-primary {
  background: linear-gradient(135deg, #10b981 0%, #059669 100%);
  color: #ffffff;
  border: none;
  box-shadow: 0 4px 15px rgba(16, 185, 129, 0.25);
}

.btn-primary:hover {
  transform: translateY(-3px);
  box-shadow: 0 8px 25px rgba(16, 185, 129, 0.45);
}

.btn-secondary {
  background: rgba(255, 255, 255, 0.03); 
  color: #10b981;
  border: 1.5px solid rgba(16, 185, 129, 0.4);
  backdrop-filter: blur(10px);
}

.btn-secondary:hover {
  transform: translateY(-3px);
  background: rgba(16, 185, 129, 0.1);
  border-color: #10b981;
  color: #ffffff;
  box-shadow: 0 8px 25px rgba(16, 185, 129, 0.15);
}
/* ========================================= */

/* --- BAGIAN FOTO PROFIL ELEGAN --- */
.hero-image {
  flex: 1;
  display: flex;
  justify-content: center;
}

.image-border {
  width: 350px;
  height: 350px;
  border-radius: 50%; 
  background: linear-gradient(135deg, var(--accent-color) 0%, #0ea5e9 100%);
  padding: 6px; 
  overflow: hidden;
  position: relative;
  
  box-shadow: 
    0 0 30px rgba(16, 185, 129, 0.4),  
    0 0 10px rgba(16, 185, 129, 0.2);  
  
  transition: transform 0.5s ease, box-shadow 0.5s ease;
}

.hero-image:hover .image-border {
  transform: translateY(-5px); 
  box-shadow: 
    0 0 50px rgba(16, 185, 129, 0.7),  
    0 0 20px rgba(16, 185, 129, 0.3);
}

.image-border img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: inherit; 
  display: block; 
}

/* Responsif untuk HP */
@media (max-width: 900px) {
  .home-hero {
    flex-direction: column-reverse;
    text-align: center;
    justify-content: center;
    padding-top: 2rem;
  }

  .hero-text h1 {
    font-size: 2.8rem; 
  }

  .description {
    text-align: center; 
    margin: 0 auto 2rem auto;
  }

  .hero-buttons {
    justify-content: center;
    /* Tambahan biar di layar sempit banget tombolnya tetep rapi */
    gap: 1rem; 
  }
  
  .hero-btn {
    padding: 10px 24px;
    font-size: 0.95rem;
  }

  .image-border {
    width: 250px; 
    height: 250px;
  }
}
</style>