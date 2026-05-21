<template>
  <section class="about-section">
    <h2 class="section-title">About <span>Me</span></h2>
    
    <div class="about-content">
      <div class="about-text">
        <p>
          Hi! I am an Information Technology student at Universitas Bina Sarana Informatika (UBSI), deeply passionate about Data Analytics, Machine Learning, and AI workflows. I enjoy working with data from the ground up using Python and SQL to clean raw datasets, uncover hidden patterns, and transform them into actionable business insights.
        </p>
        <p>
          I firmly believe that great decisions are built on well-structured data, and I am eager to contribute to the processes that make it happen. As a continuous learner, I am always open to new collaborations and ready to grow through real-world challenges.
        </p>
      </div>

      <div class="about-cards">
        <div class="card">
          <i class="icon">🎓</i>
          <h3>Education</h3>
          <p>Information Technology  GPA : 3.93</p>
          <span class="highlight">Universitas Bina Sarana Informatika</span>
        </div>
        
        <div class="card">
          <i class="icon">📊</i>
          <h3>Primary Focus</h3>
          <p>Data Science and Business Intelligence</p>
          <span class="highlight">Data Analytics, Machine Learning, BI tools, and Data Engineering</span>
        </div>

        <div class="card">
          <i class="icon">📍</i>
          <h3>Location</h3>
          <p>Based in</p>
          <span class="highlight">South Jakarta, Indonesia</span>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.about-section {
  padding: 2rem 0;
  animation: fadeIn 0.8s ease-in-out;
}

.section-title {
  font-size: 2.5rem;
  margin-bottom: 2rem;
  text-align: center;
}

.section-title span {
  color: var(--accent-color);
}

.about-content {
  display: flex;
  gap: 4rem;
  align-items: center;
}

.about-text {
  flex: 1.2;
  font-size: 1.1rem;
  line-height: 1.8;
  color: var(--text-secondary);
  text-align: justify;
}

.about-text p {
  margin-bottom: 1.5rem;
}

.about-cards {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.card {
  background-color: rgba(30, 41, 59, 0.6);
  border: 1px solid rgba(56, 189, 248, 0.2);
  padding: 1.5rem;
  border-radius: 12px;
  transition: transform 0.3s, box-shadow 0.3s;
}

.card:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
  border-color: var(--accent-color);
}

.icon {
  font-size: 2rem;
  margin-bottom: 0.5rem;
  display: inline-block;
}

.card h3 {
  font-size: 1.2rem;
  margin-bottom: 0.3rem;
  color: var(--text-primary);
}

.card p {
  color: var(--text-secondary);
  font-size: 0.9rem;
  margin-bottom: 0.5rem;
}

.highlight {
  display: inline-block;
  color: var(--accent-color);
  font-weight: 600;
  font-size: 0.9rem;
}

/* Animasi transisi halaman mulus */
@keyframes fadeIn {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}

/* Responsif untuk HP */
@media (max-width: 900px) {
  .about-content {
    flex-direction: column;
    gap: 2rem;
  }
}
</style>