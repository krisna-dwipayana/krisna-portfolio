<script setup>
import { ref, computed } from 'vue'

// Kategori untuk tab filter
const activeCategory = ref('All')
const categories = ['All', 'BI & Analytics', 'Data Engineering', 'Machine Learning']

// Data proyekmu
const projects = ref([
  {
    id: 1,
    title: 'Demographic Analysis Dashboard',
    category: 'BI & Analytics',
    description: 'Built an interactive dashboard analyzing global population trends across 212 nations and 6 continents, featuring a world map, demographic change over decades, regional distribution, and country-level comparisons.',
    tech: ['Google Spreadsheets', 'SQL', 'Looker Studio'],
    link: 'https://datastudio.google.com/reporting/d5312de0-5c39-4558-b372-66ffbcf4f089/page/YpPaF',
    imageSrc: 'demografi-ds.jpg'
  },
  {
    id: 2,
    title: 'Global IT Salary Dashboard',
    category: 'BI & Analytics',
    description: 'Built an interactive dashboard analyzing salary trends across 12 roles, 10 industries, and 10 countries, featuring breakdowns by job title, experience level, location, company size, education, and remote work proportion.',
    tech: ['SQL', 'Microsoft Excel', 'Power BI'],
    link: 'https://github.com/krisna-dwipayana/global-salary-dashboard',
    imageSrc: 'salary-ds.jpg'
  },
  {
    id: 3,
    title: 'Hoax Detection Classification Model',
    category: 'Machine Learning',
    description: 'Built a predictive analysis model using Logistic Regression methodology to classify hoax data accurately. Structured the methodology for a national competition research paper.',
    tech: ['Python', 'Logistic Regression', 'Scikit-Learn'],
    link: 'https://github.com/krisna-dwipayana/hoax-detection-project',
    imageSrc: 'hoax.jpg'
  },
  {
    id: 4,
    title: 'IMDb Business Performance Dashboard',
    category: 'BI & Analytics',
    description: 'Built an interactive dashboard analyzing 1,348 movies across 14 categories, featuring KPI cards, top/bottom rated movies, duration by genre, age rating distribution, and average rating trends from 1919–2017.',
    tech: ['SQL', 'Microsoft Excel', 'Looker Studio'],
    link: 'https://datastudio.google.com/reporting/22d3c696-778e-4445-b7c8-f1d023a1b99e/page/NGUcF',
    imageSrc: 'imdb-film-ds.jpg'
  },
  {
    id: 5,
    title: 'CNN-Based Image Recognition for Fashion-MNIST',
    category: 'Machine Learning',
    description: 'Developed an end-to-end image recognition system for the Fashion-MNIST dataset. Managed data preprocessing with Pandas and designed a robust CNN architecture in TensorFlow, reaching a 91.69% classification accuracy.',
    tech: ['Python', 'TensorFlow', 'CNN', 'Pandas'],
    link: 'https://github.com/krisna-dwipayana/fashion-mnist-cnn-classifier',
    imageSrc: 'store.jpg'
  },
  {
    id: 6,
    title: 'Vehicle Rental Database System',
    category: 'Data Engineering',
    description: 'A centralized PostgreSQL database system for managing vehicle rental operations, including customer data, fleet inventory, rental transactions, and maintenance records..',
    tech: ['SQL', 'Relational Database', 'PostgreSQL'],
    link: 'https://github.com/krisna-dwipayana/vehicle-rental-system',
    imageSrc: 'db.jpg'
  }
])

// Logika untuk filter kotak project
const filteredProjects = computed(() => {
  if (activeCategory.value === 'All') return projects.value
  return projects.value.filter(p => p.category === activeCategory.value)
})

// FUNGSI KHUSUS VITE UNTUK MEMANGGIL GAMBAR DINAMIS
const getImageUrl = (name) => {
  return new URL(`../assets/${name}`, import.meta.url).href
}
</script>

<template>
  <section class="projects-section">
    <div class="section-header">
      <h2 class="section-title">My <span>Projects</span></h2>
      <p class="section-subtitle">git log --oneline --graph projects/</p>
    </div>

    <div class="project-filters">
      <button 
        v-for="cat in categories" 
        :key="cat" 
        class="filter-btn"
        :class="{ active: activeCategory === cat }"
        @click="activeCategory = cat"
      >
        {{ cat }}
      </button>
    </div>

    <div class="projects-grid">
      <div 
        class="project-card" 
        v-for="project in filteredProjects" 
        :key="project.id"
      >
        <div class="project-image">
            <img :src="getImageUrl(project.imageSrc)" :alt="project.title" />
        </div>
        
        <div class="project-content">
          <span class="project-category">{{ project.category }}</span>
          <h3 class="project-title">{{ project.title }}</h3>
          <p class="project-desc">{{ project.description }}</p>
          
          <div class="project-tech">
            <span v-for="(tech, index) in project.tech" :key="index" class="tech-tag">
              {{ tech }}
            </span>
          </div>
        </div>
        
        <div class="project-footer">
          <a :href="project.link" class="project-link" target="_blank" rel="noopener noreferrer">
            View Details <span class="arrow">→</span>
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.projects-section {
  padding-top: 2rem;
}

.section-header {
  margin-bottom: 2rem;
}

.section-title {
  font-size: 2.5rem;
  margin-bottom: 0.5rem;
}

.section-title span {
  color: var(--accent-color);
}

.section-subtitle {
  color: var(--text-secondary);
  font-size: 1rem;
  font-family: 'Fira Code', monospace;
  opacity: 0.7;
}

/* --- TABS FILTER KATEGORI --- */
.project-filters {
  display: flex;
  gap: 1rem;
  margin-bottom: 3rem;
  flex-wrap: wrap;
}

.filter-btn {
  background: transparent;
  border: 1px solid rgba(255, 255, 255, 0.1);
  color: var(--text-secondary);
  padding: 0.5rem 1.2rem;
  border-radius: 8px;
  cursor: pointer;
  transition: 0.3s;
  font-family: 'Fira Code', monospace;
  font-size: 0.85rem;
}

.filter-btn:hover, .filter-btn.active {
  border-color: var(--accent-color);
  color: var(--accent-color);
  background: rgba(16, 185, 129, 0.1);
}

/* --- GRID KOTAK PROJECT --- */
.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 2rem;
}

/* --- STYLE KOTAK PROJECT (CARD) --- */
.project-card {
  background: var(--card-bg);
  border: 1px solid rgba(16, 185, 129, 0.1); 
  border-radius: 12px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  overflow: hidden; 
  transition: transform 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275), box-shadow 0.4s ease, border-color 0.4s ease;
  cursor: pointer;
  position: relative;
}

.project-card:hover {
  transform: translateY(-10px); 
  border-color: var(--accent-color); 
  box-shadow: 0 15px 30px rgba(0, 0, 0, 0.5), 0 0 20px rgba(16, 185, 129, 0.15); 
}

.project-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 3px;
  background: linear-gradient(90deg, transparent, var(--accent-color), transparent);
  transform: scaleX(0);
  transition: transform 0.4s ease;
  z-index: 2; 
}

.project-card:hover::before {
  transform: scaleX(1);
}

/* --- GAMBAR PROJECT --- */
.project-image {
    width: 100%;
    height: 200px; 
    overflow: hidden;
}

.project-image img {
    width: 100%;
    height: 100%;
    object-fit: cover; 
    transition: transform 0.4s ease;
}

.project-card:hover .project-image img {
    transform: scale(1.05); 
}

/* --- ISI KONTEN PROJECT --- */
.project-content {
    padding: 1.5rem 2rem; 
}

.project-category {
  display: inline-block;
  color: var(--accent-color);
  font-size: 0.75rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 1px;
  margin-bottom: 0.8rem;
  background: rgba(16, 185, 129, 0.1);
  padding: 0.3rem 0.8rem;
  border-radius: 15px;
}

.project-title {
  font-size: 1.2rem;
  color: var(--text-primary);
  margin-bottom: 1rem;
  line-height: 1.3;
}

.project-desc {
  color: var(--text-secondary);
  font-size: 0.9rem;
  line-height: 1.6;
  margin-bottom: 1.5rem;
}

/* --- TAG TEKNOLOGI (CHIPS) --- */
.project-tech {
  display: flex;
  flex-wrap: wrap;
  gap: 0.6rem;
}

.tech-tag {
  background: transparent;
  border: 1px solid rgba(255, 255, 255, 0.1);
  color: var(--text-secondary);
  padding: 0.3rem 0.6rem;
  border-radius: 6px;
  font-size: 0.75rem;
  font-family: 'Fira Code', monospace;
}

/* --- FOOTER CARD (LINK) --- */
.project-footer {
  margin-top: auto; 
  padding: 1.5rem 2rem; 
}

.project-link {
  color: var(--text-primary);
  text-decoration: none;
  font-weight: 600;
  font-size: 0.95rem;
  display: flex;
  align-items: center;
  gap: 0.5rem;
  transition: color 0.3s ease;
}

.project-link .arrow {
  transition: transform 0.3s ease;
}

.project-card:hover .project-link {
  color: var(--accent-color);
}

.project-card:hover .project-link .arrow {
  transform: translateX(5px); 
}

/* Responsif untuk HP */
@media (max-width: 768px) {
  .projects-grid {
    grid-template-columns: 1fr;
  }
}
</style>