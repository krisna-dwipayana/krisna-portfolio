<script setup>
import { ref } from 'vue'

const activeTab = ref('Prompting & Artificial Intelligence')

const categories = [
  'Prompting & Artificial Intelligence',
  'Data Analytics & Business Intelligence',
  'Data Science & Machine Learning',
  'Deep Learning & Neural Network',
  'Quantitative Research',
  'Software Development',
  'Soft Skills'
]

// Data tools/skills
const skillsData = {
  'Prompting & Artificial Intelligence': [
    { name: 'Gemini', src: '/icons/gemini.svg', type: 'image' },
    { name: 'Claude', src: '/icons/claude.svg', type: 'image' },
    { name: 'DeepSeek', src: '/icons/deepseek.svg', type: 'image' },
    { name: 'ChatGPT', src: '/icons/chatgpt.svg', type: 'image' },
    { name: 'Perplexity', src: '/icons/perplexity.svg', type: 'image' },
    { name: 'GitHub Copilot', src: '/icons/githubcopilot.svg', type: 'image' }
  ],
  'Data Analytics & Business Intelligence': [
    { name: 'Microsoft Excel', src: '/icons/ms-excel.svg', type: 'image' },
    { name: 'Google Spreadsheet', src: '/icons/google-sheets.svg', type: 'image' },
    { name: 'Looker Studio', src: '/icons/looker.svg', type: 'image' },
    { name: 'Power BI', src: '/icons/power-bi.svg', type: 'image' },
    { name: 'Tableau', src: '/icons/tableau.svg', type: 'image' },
    { name: 'PostgreSQL', src: '/icons/Postgresql.svg', type: 'image' },
    { name: 'MySQL', src: '/icons/mysql.svg', type: 'image' }
  ],
  'Data Science & Machine Learning': [
    { name: 'Python', src: '/icons/python.svg', type: 'image' },
    { name: 'Jupyter Notebook', src: '/icons/jupyter.svg', type: 'image' },
    { name: 'Google Colab', src: '/icons/google-colab.svg', type: 'image' },
    { name: 'Pandas', src: '/icons/pandas.svg', type: 'image' },
    { name: 'NumPy', src: '/icons/numpy.svg', type: 'image' },
    { name: 'Matplotlib', src: '/icons/matplotlib.svg', type: 'image' },
    { name: 'Seaborn', src: '/icons/seaborn.svg', type: 'image' },
    { name: 'Scikit-learn', src: '/icons/scikit-learn.svg', type: 'image' },
    { name: 'XGBoost', src: '/icons/xgboost.svg', type: 'image' }
  ],
  'Deep Learning & Neural Network': [
    { name: 'TensorFlow', src: '/icons/tensorflow.svg', type: 'image' },
    { name: 'PyTorch', src: '/icons/pytorch.svg', type: 'image' }
  ],
  'Quantitative Research': [
    { name: 'IBM SPSS', src: '/icons/spss-ibm.svg', type: 'image' },
    { name: 'JASP', src: '/icons/jasp.svg', type: 'image' },
    { name: 'R Studio', src: '/icons/r-studio.svg', type: 'image' },
    { name: 'Mendeley', src: '/icons/mendeley.svg', type: 'image' }
  ],
  'Software Development': [
    { name: 'HTML', src: '/icons/html.svg', type: 'image' },
    { name: 'CSS', src: '/icons/css.svg', type: 'image' },
    { name: 'JavaScript', src: '/icons/javascript.svg', type: 'image' },
    { name: 'PHP', src: '/icons/php.svg', type: 'image' },
    { name: 'Laravel', src: '/icons/laravel.svg', type: 'image' },
    { name: 'Vue.js', src: '/icons/vue.svg', type: 'image' },
    { name: 'Flutter', src: '/icons/flutter.svg', type: 'image' },
    { name: 'Dart', src: '/icons/dart.svg', type: 'image' },
    { name: 'Node.js', src: '/icons/node.svg', type: 'image' },
    { name: 'phpMyAdmin', src: '/icons/phpmyadmin.svg', type: 'image' },
    { name: 'Netlify', src: '/icons/netlify.svg', type: 'image' },
    { name: 'Python', src: '/icons/piton.svg', type: 'image' }
  ],
  'Soft Skills': [
    { name: 'Critical Thinking', icon: '🤔', type: 'text' },
    { name: 'Problem Solving', icon: '🧩', type: 'text' },
    { name: 'Communication', icon: '💬', type: 'text' }
  ]
}

// Data penjelasan (Description) untuk masing-masing kategori
const categoryDescriptions = {
  'Prompting & Artificial Intelligence': `
    <div class="workflow-steps">
      <p><strong>🎯 Task :</strong> I define specific, actionable objectives to ensure the AI focuses on delivering precise and relevant outputs without ambiguity.</p>
      <p><strong>🗂️ Context :</strong> I provide comprehensive background information, target audience, and business goals to align the AI's response with the exact situation.</p>
      <p><strong>📎 References :</strong> I supply specific examples and reference materials to guide the AI in mirroring the desired style, tone, and data formatting.</p>
      <p><strong>✅ Evaluate :</strong> I establish strict constraints such as tone, length, and format to define clear criteria for a high-quality, immediately usable output.</p>
      <p><strong>🔄 Iterate :</strong> I continuously review and refine prompts through an active feedback loop, adjusting instructions until the perfect result is achieved.</p>
    </div>
  `,
  'Data Analytics & Business Intelligence': `
    <div class="workflow-steps">
      <p><strong>📥 Acquire :</strong> I gather data from multiple sources to build a comprehensive and reliable foundation for business analysis.</p>
      <p><strong>🧩 Parse :</strong> I structure and format raw, unstructured data into a highly organized and standardized dataset.</p>
      <p><strong>🧹 Filter :</strong> I meticulously clean the data, handling missing values and noise, to focus strictly on relevant KPIs.</p>
      <p><strong>⛏️ Mine :</strong> I delve into the clean dataset to uncover hidden patterns, trends, and actionable strategic insights.</p>
      <p><strong>📊 Represent :</strong> I translate complex numbers into compelling visual narratives through intuitive charts and dashboards.</p>
      <p><strong>✨ Refine :</strong> I iterate on visual designs to eliminate clutter and ensure the core message is instantly clear to all stakeholders.</p>
      <p><strong>🖱️ Interact :</strong> I build dynamic capabilities using tools like Power BI or Tableau, empowering decision-makers to explore the data independently.</p>
    </div>
  `,
  'Data Science & Machine Learning': `
    <div class="workflow-steps">
      <p><strong>🎯 Business Understanding :</strong> I define the core problem and set clear objectives to ensure the project aligns directly with business needs.</p>
      <p><strong>🔍 Data Understanding :</strong> I gather and explore the initial dataset to identify underlying patterns, anomalies, and potential quality issues.</p>
      <p><strong>🛠️ Data Preparation :</strong> I clean, transform, and prepare the data to ensure high consistency and readiness for modeling.</p>
      <p><strong>🤖 Modeling :</strong> I select and apply the most suitable algorithms to build robust predictive models that solve the business problem.</p>
      <p><strong>✅ Evaluation:</strong> I assess the model's performance against technical metrics and its actual alignment with the initial business goals.</p>
    </div>
  `,
  'Deep Learning & Neural Network': `
    <div class="workflow-steps">
      <p><strong>📥 Obtain :</strong> I acquire and aggregate large-scale, diverse datasets to provide a strong foundation for training complex neural architectures.</p>
      <p><strong>🧹 Scrub :</strong> I clean, normalize, and preprocess raw data, applying augmentation techniques to enhance model robustness.</p>
      <p><strong>🔍 Explore :</strong> I conduct exploratory data analysis (EDA) to visualize distributions and understand underlying dataset patterns.</p>
      <p><strong>🧠 Model :</strong> I design and train neural network architectures, tuning hyperparameters to minimize loss and maximize accuracy.</p>
      <p><strong>📊 Interpret :</strong> I evaluate model performance using metrics and explainability techniques to ensure actionable and reliable outcomes.</p>
    </div>
  `,
  'Quantitative Research': `
    <div class="workflow-steps">
      <p><strong>📌 Define :</strong> I identify the core research problem and formulate clear, testable hypotheses to ensure a scientifically rigorous study.</p>
      <p><strong>📐 Design :</strong> I carefully design the research methodology and data collection instruments to guarantee high validity and reliability.</p>
      <p><strong>📥 Collect :</strong> I systematically gather quantitative data using strict protocols to minimize bias and ensure accurate representation.</p>
      <p><strong>🧮 Analyze :</strong> I conduct rigorous hypothesis testing using statistical software to uncover significant relationships and variations.</p>
      <p><strong>🧠 Interpret :</strong> I translate raw statistical outputs into meaningful conclusions that provide genuine answers to the research questions.</p>
      <p><strong>📢 Communicate :</strong> I synthesize complex statistical results into clear, accessible reports with actionable recommendations for all stakeholders.</p>
    </div>
  `,
  'Software Development': `
    <div class="workflow-steps">
      <p><strong>🌐 Web Development :</strong> I build responsive, dynamic, and scalable web applications using modern frameworks like Vue.js, Laravel, and Node.js.</p>
      <p><strong>📱 Mobile Development :</strong> I design and develop cross-platform mobile applications using Flutter and Dart for seamless user experiences.</p>
      <p><strong>☁️ Deployment :</strong> I deploy and manage projects efficiently using platforms like Vercel and Netlify to ensure high availability and performance.</p>
    </div>
  `,
  'Soft Skills': `
    <div class="workflow-steps">
      <p><strong>🤔 Critical Thinking :</strong> I objectively analyze data by questioning assumptions and identifying biases to ensure insights are logically sound.</p>
      <p><strong>🧩 Problem Solving :</strong> I methodically break down complex challenges to identify root causes and design efficient, sustainable solutions.</p>
      <p><strong>💬 Communication :</strong> I translate intricate technical findings into clear, compelling narratives that empower stakeholders to make data-driven decisions.</p>
    </div>
  `
}
</script>

<template>
  <section class="skills-section">
    <h2 class="section-title">Tech <span>Stack</span></h2>
    <p class="section-subtitle">The technologies and frameworks I use to turn raw datasets into actionable insights.</p>

    <div class="tabs-container">
      <button 
        v-for="cat in categories" 
        :key="cat"
        @click="activeTab = cat"
        :class="['tab-btn', { active: activeTab === cat }]"
      >
        {{ cat }}
      </button>
    </div>

    <!-- FIX GLITCH: wrapper dengan background solid menutup celah antar card -->
    <div class="skills-grid-wrapper">
      <div class="skills-grid">
        <div 
          v-for="skill in skillsData[activeTab]" 
          :key="skill.name" 
          class="skill-item"
        >
          <i v-if="skill.type === 'icon'" :class="skill.class"></i>
          <img v-else-if="skill.type === 'image'" :src="skill.src" :alt="skill.name" class="skill-img" />
          <span v-else class="text-icon">{{ skill.icon }}</span>
          
          <span>{{ skill.name }}</span>
        </div>
      </div>
    </div>

    <div class="category-description">
      <div v-html="categoryDescriptions[activeTab]"></div>
    </div>

  </section>
</template>

<style scoped>
/* FIX GLITCH #1: isolate stacking context dari video background */
.skills-section {
  padding: 2rem 0;
  animation: fadeIn 0.8s ease-in-out;
  max-width: 1000px;
  margin: 0 auto;
  isolation: isolate;
  position: relative;
  z-index: 2;
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
  font-family: 'Fira Code', monospace;
  margin-bottom: 2rem;
  border-bottom: 1px solid rgba(16, 185, 129, 0.2);
  padding-bottom: 1rem;
}

.tabs-container {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  margin-bottom: 3rem;
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

/* FIX GLITCH #2: wrapper menutup celah gap antar card dengan background solid */
.skills-grid-wrapper {
  background-color: rgba(7, 19, 15, 0.85);
  border-radius: 12px;
  padding: 1rem;
}

.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 1.5rem;
  animation: fadeIn 0.4s ease-in-out; 
}

.skill-item {
  background-color: rgba(30, 41, 59, 0.6);
  border: 1px solid rgba(16, 185, 129, 0.1);
  padding: 1.2rem;
  border-radius: 10px;
  display: flex;
  align-items: center;
  gap: 1rem;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  font-weight: 500;
  color: var(--text-primary);
}

.skill-item:hover {
  transform: translateY(-5px);
  border-color: var(--accent-color);
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
}

.skill-item i { font-size: 2.5rem; }
.text-icon { font-size: 2rem; }
.skill-img { width: 40px; height: 40px; object-fit: contain; }

.category-description {
  margin-top: 2.5rem;
  padding: 1.5rem;
  background-color: rgba(16, 185, 129, 0.05);
  border-left: 4px solid var(--accent-color);
  border-radius: 0 8px 8px 0;
  color: var(--text-secondary);
  line-height: 1.6;
  font-size: 0.95rem;
  animation: fadeIn 0.6s ease-in-out;
}

:deep(.workflow-steps p) {
  margin-bottom: 1rem; 
}
:deep(.workflow-steps p:last-child) {
  margin-bottom: 0;
}
:deep(.workflow-steps strong) {
  color: var(--text-primary);
}

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(10px); }
  to { opacity: 1; transform: translateY(0); }
}
</style>