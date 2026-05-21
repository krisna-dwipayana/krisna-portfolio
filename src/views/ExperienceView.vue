<script setup>
import { ref } from 'vue'

const activeTab = ref('IT Experience')

const categories = [
  { id: 'IT Experience', icon: '💻' },
  { id: 'Non-IT Experience', icon: '🏢' },
  { id: 'Certification', icon: '📜' }
]

// Data pengalaman kerja, organisasi, dan sertifikasi
const experienceData = {
  'IT Experience': [
    {
      title: 'System Analyst Intern',
      organization: 'PT Zahir Internasional',
      date: 'Dec 2025 - Jan 2026',
      description: [
        'Designed a comprehensive ERD and built a scalable PostgreSQL architecture with 1NF–3NF normalization for vehicle rental operations.',
        'Translated business requirements into technical specifications utilizing strict ENUM-based data validation.',
        'Created Database Views to safeguard transaction performance and authored clear system blueprints (DDL/DML).'
      ],
      tech: ['PostgreSQL', 'Database Design', 'ERD', 'Data Normalization']
    },
    {
      title: 'Data Analytics Intern',
      organization: 'Edutech Luarsekolah',
      date: 'Jul 2025 - Oct 2025',
      description: [
        'Designed and deployed interactive dashboards across advertising, property, and demographic domains to drive strategic decisions.',
        'Analyzed massive datasets, including $2.05B in property transactions and global demographic data across 212 nations.',
        'Delivered structured reporting on audience demographics, 27M+ ad clicks, and population shifts to optimize targeting strategies.'
      ],
      tech: ['Data Analysis', 'Data Visualization', 'Dashboarding', 'Reporting']
    },
    {
      title: 'Big Data Analytics Virtual Intern',
      organization: 'PT. KIMIA FARMA, TBK x Rakamin Academy',
      date: 'May 2025 - Jun 2025',
      description: [
        'Developed a holistic business performance dashboard tracking Rp321.17M in Net Sales and Rp72.56M in Net Profit.',
        'Analyzed multi-year branch performance and leveraged time-series data to identify revenue trends and seasonal stability.',
        'Designed interactive geospatial maps with dynamic filters to empower local-level, data-driven decision-making.'
      ],
      tech: ['Data Analysis', 'Microsoft Excel', 'Big Data', 'Geospatial Mapping']
    },
    {
      title: 'FullStack Web Developer & Flutter Developer',
      organization: 'ITBOX Academy',
      date: '2024 - 2026',
      description: [
        'Acquired comprehensive training bundles focusing on modern web development (MERN/Laravel) and cross-platform mobile application development using Flutter.'
      ],
      tech: ['Web Development', 'Mobile Dev', 'Certificate']
    }
  ],
  'Non-IT Experience': [
    {
      title: 'Data Entry Clerk',
      organization: 'PT Bank Rakyat Indonesia (Persero) Tbk',
      date: 'Sep 2023 - Feb 2024',
      description: [
        'Digitized 100+ daily records to significantly reduce document retrieval time and boost efficiency.',
        'Ensured 100% regulatory compliance by enforcing strict data security and confidentiality protocols.',
        'Maintained archive data integrity using advanced Excel functions (Pivot Tables, VLOOKUP).',
        'Acted as the primary liaison between Archive and Customer Service to resolve operational issues.'
      ],
      tech: ['Data Entry', 'Microsoft Excel', 'Data Integrity', 'Regulatory Compliance']
    }
  ],
  'Certification': [
    { 
      title: 'AI for Data & Analytics', 
      org: 'Coding Studio', 
      img: '/certificates/certificate7.jpg' 
    },
    { 
      title: 'Fundamental Machine Learning', 
      org: 'Aksademy', 
      img: '/certificates/certificate2.jpg' 
    },
    { 
      title: 'Data Analytics: SQL', 
      org: 'Ioda Academy', 
      img: '/certificates/certificate3.jpg' 
    },
    { 
      title: 'Data Analyst Bootcamp', 
      org: 'Nusacodes', 
      img: '/certificates/certificate6.jpg' 
    },
    { 
      title: 'Data Engineer Course', 
      org: 'DSAREA', 
      img: '/certificates/certificate4.jpg' 
    },
    { 
      title: 'Data Science Course', 
      org: 'DSAREA', 
      img: '/certificates/certificate5.jpg' 
    },
    { 
      title: 'Dashboard Excel untuk Portofolio Data Analyst', 
      org: 'HaloTech Academy', 
      img: '/certificates/certificate1.jpg' 
    }
  ]
}
</script>

<template>
  <section class="experience-section">
    <h2 class="section-title">My <span>Experience</span></h2>
    <p class="section-subtitle sql-code">"Dedicated to transforming complex data into impactful, real-world solutions.";</p>

    <div class="tabs-container">
      <button 
        v-for="cat in categories" 
        :key="cat.id"
        @click="activeTab = cat.id"
        :class="['tab-btn', { active: activeTab === cat.id }]"
      >
        <span class="tab-icon">{{ cat.icon }}</span> {{ cat.id }}
      </button>
    </div>

    <div v-if="activeTab === 'Certification'" class="cert-grid">
      <div v-for="(cert, index) in experienceData['Certification']" :key="index" class="cert-card">
        <div class="cert-img-wrapper">
          <img :src="cert.img" :alt="cert.title" onerror="this.src='https://placehold.co/600x400?text=Image+Not+Found'">
        </div>
        <div class="cert-info">
          <h4>{{ cert.title }}</h4>
          <p>{{ cert.org }}</p>
        </div>
      </div>
    </div>

    <div v-else class="experience-content">
      <div 
        v-for="(item, index) in experienceData[activeTab]" 
        :key="index" 
        class="timeline-item"
      >
        <div class="timeline-dot"></div>
        <div class="timeline-card">
          <div class="card-header">
            <h3>{{ item.title }}</h3>
            <span class="date-badge">{{ item.date }}</span>
          </div>
          
          <div class="organization-wrapper">
            <img v-if="item.logo" :src="item.logo" :alt="item.organization" class="experience-logo">
            <h4 class="organization">{{ item.organization }}</h4>
          </div>

          <div class="description">
            <ul v-if="Array.isArray(item.description)" class="job-list">
              <li v-for="(point, i) in item.description" :key="i">{{ point }}</li>
            </ul>
            <p v-else>{{ item.description }}</p>
          </div>
          
          <div class="tech-stack">
            <span v-for="tech in item.tech" :key="tech" class="tech-tag">
              {{ tech }}
            </span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.experience-section {
  padding: 2rem 0;
  animation: fadeIn 0.8s ease-in-out;
  max-width: 1000px; /* Diperlebar sedikit untuk grid */
  margin: 0 auto;
}

.section-title {
  font-size: 2.5rem;
  margin-bottom: 0.5rem;
}

.section-title span {
  color: var(--accent-color);
}

.section-subtitle.sql-code {
  color: var(--text-secondary);
  font-family: 'Fira Code', monospace;
  margin-bottom: 2.5rem;
  background-color: rgba(15, 23, 42, 0.4);
  padding: 0.8rem 1rem;
  border-radius: 6px;
  border-left: 3px solid var(--accent-color);
  display: inline-block;
}

/* Styling Tab Navigasi */
.tabs-container {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  margin-bottom: 3rem;
  border-bottom: 1px solid rgba(16, 185, 129, 0.2);
  padding-bottom: 1.5rem;
}

.tab-btn {
  background-color: rgba(30, 41, 59, 0.4);
  border: 1px solid rgba(148, 163, 184, 0.2);
  color: var(--text-secondary);
  padding: 0.8rem 1.5rem;
  border-radius: 8px;
  cursor: pointer;
  font-size: 0.95rem;
  font-weight: 500;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.tab-btn:hover {
  background-color: rgba(16, 185, 129, 0.1);
  border-color: rgba(16, 185, 129, 0.4);
  color: var(--text-primary);
}

.tab-btn.active {
  background-color: rgba(16, 185, 129, 0.15);
  border-color: var(--accent-color);
  color: var(--accent-color);
}

.tab-icon {
  font-size: 1.1rem;
}

/* --- STYLING TIMELINE (IT & Non-IT) --- */
.experience-content {
  position: relative;
  padding-left: 2rem;
  border-left: 2px solid rgba(16, 185, 129, 0.2);
  animation: fadeIn 0.4s ease-in-out;
}

.timeline-item {
  position: relative;
  margin-bottom: 2.5rem;
}

.timeline-item:last-child {
  margin-bottom: 0;
}

.timeline-dot {
  position: absolute;
  left: -2.45rem;
  top: 0;
  width: 16px;
  height: 16px;
  background-color: var(--accent-color);
  border: 4px solid var(--bg-color);
  border-radius: 50%;
  box-shadow: 0 0 10px rgba(16, 185, 129, 0.5);
}

.timeline-card {
  background-color: rgba(30, 41, 59, 0.4);
  border: 1px solid rgba(16, 185, 129, 0.1);
  padding: 1.5rem;
  border-radius: 12px;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.timeline-card:hover {
  transform: translateX(5px);
  border-color: rgba(16, 185, 129, 0.4);
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
}

.card-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  margin-bottom: 0.5rem;
  flex-wrap: wrap;
  gap: 1rem;
}

.card-header h3 {
  color: var(--text-primary);
  font-size: 1.25rem;
  margin: 0;
}

.date-badge {
  background-color: rgba(16, 185, 129, 0.1);
  color: var(--accent-color);
  padding: 0.3rem 0.8rem;
  border-radius: 20px;
  font-size: 0.85rem;
  font-weight: 600;
  border: 1px solid rgba(16, 185, 129, 0.2);
}

/* Styling Wrapper Logo & Nama Perusahaan */
.organization-wrapper {
  display: flex;
  align-items: center;
  gap: 1rem;
  margin-bottom: 1rem;
}

.experience-logo {
  height: 35px; /* Sesuaikan tinggi logo agar pas */
  width: auto;
  /* EFEK GRASYCALE DAN OPACITY SUDAH DIHAPUS CUY JADI SELALU BERWARNA */
}

.organization {
  color: var(--text-secondary);
  font-size: 1rem;
  font-weight: 500;
  margin-bottom: 0; /* Hapus margin bottom bawaan */
}

.description {
  color: var(--text-secondary);
  line-height: 1.6;
  font-size: 0.95rem;
  margin-bottom: 1.2rem;
}

/* Styling untuk list bullet points di experience */
.job-list {
  padding-left: 1.2rem;
  margin-bottom: 0;
}

.job-list li {
  margin-bottom: 0.5rem;
}

.job-list li:last-child {
  margin-bottom: 0;
}

.tech-stack {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.tech-tag {
  background-color: rgba(15, 23, 42, 0.6);
  color: var(--text-secondary);
  padding: 0.3rem 0.6rem;
  border-radius: 6px;
  font-size: 0.8rem;
  border: 1px solid rgba(148, 163, 184, 0.1);
}

/* --- STYLING CERTIFICATION GRID --- */
.cert-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 2rem;
  animation: fadeIn 0.5s ease-in-out;
}

.cert-card {
  background-color: rgba(30, 41, 59, 0.4);
  border: 1px solid rgba(16, 185, 129, 0.1);
  border-radius: 12px;
  overflow: hidden;
  transition: all 0.3s ease;
}

.cert-card:hover {
  transform: translateY(-8px);
  border-color: var(--accent-color);
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.3);
}

.cert-img-wrapper {
  width: 100%;
  height: 200px;
  overflow: hidden;
  background-color: rgba(15, 23, 42, 0.8);
  display: flex;
  align-items: center;
  justify-content: center;
}

.cert-img-wrapper img {
  width: 100%;
  height: 100%;
  object-fit: cover; /* Biar gambar gak penyok */
  transition: transform 0.5s ease;
}

.cert-card:hover .cert-img-wrapper img {
  transform: scale(1.08); /* Efek zoom elegan */
}

.cert-info {
  padding: 1.2rem;
}

.cert-info h4 {
  color: var(--text-primary);
  margin-bottom: 0.5rem;
  font-size: 1.05rem;
  line-height: 1.4;
}

.cert-info p {
  color: var(--accent-color);
  font-size: 0.9rem;
  font-weight: 600;
}

/* Responsif untuk HP */
@media (max-width: 768px) {
  .card-header {
    flex-direction: column;
    gap: 0.5rem;
  }
  .cert-grid {
    grid-template-columns: 1fr; /* Jadi 1 kolom di HP */
  }
}

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(15px); }
  to { opacity: 1; transform: translateY(0); }
}
</style>