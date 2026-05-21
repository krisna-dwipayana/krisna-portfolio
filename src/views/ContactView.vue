<script setup>
// Bagian script tetap kosong karena kita nanganin Formspree di HTML (action)
</script>

<template>
  <section class="contact-section">
    <div class="contact-container">
      
      <div class="contact-info">
        <h2>Let's Talk!</h2>
        <p class="contact-desc">
          I am currently open to new opportunities, virtual internships, and collaborative projects. Whether you have a question, a data problem to solve, or just want to connect, feel free to drop a message!
        </p>
        
        <div class="info-items">
          <div class="info-item">
             <span class="icon">📧</span>
             <div>
               <strong>Email</strong>
               <p>krisnadwipayana0704@gmail.com</p>
             </div>
          </div>
          <div class="info-item">
             <span class="icon">📍</span>
             <div>
               <strong>Location</strong>
               <p>South Jakarta, Indonesia</p>
             </div>
          </div>
        </div>

        <div class="social-links">
          <a href="https://www.linkedin.com/in/krisna-dwipayana17/" target="_blank" rel="noopener noreferrer" class="social-btn" title="Visit my LinkedIn">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" class="svg-icon">
              <path d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z"/>
            </svg>
          </a>
          
          <a href="https://github.com/krisna-dwipayana" target="_blank" rel="noopener noreferrer" class="social-btn" title="Visit my GitHub">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" class="svg-icon">
              <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
            </svg>
          </a>
        </div>
      </div>

      <form class="contact-form" action="https://formspree.io/f/mgoqkavw" method="POST">
        <div class="form-group">
          <label>Your Name</label>
          <input type="text" name="name" placeholder="John Doe" required>
        </div>
        
        <div class="form-group">
          <label>Your Email</label>
          <input type="email" name="email" placeholder="john@example.com" required>
        </div>
        
        <div class="form-group">
          <label>Message</label>
          <textarea name="message" rows="5" placeholder="Hello Krisna, I would like to talk about..." required></textarea>
        </div>
        
        <input type="hidden" name="_gotcha" style="display:none !important">
        
        <button type="submit" class="btn-send">Send Message 🚀</button>
      </form>

    </div>
  </section>
</template>

<style scoped>
/* Styling menyesuaikan gambar referensimu image_8b9270.png */
.contact-section {
  padding-top: 2rem;
  display: flex;
  justify-content: center;
}

.contact-container {
  display: flex;
  gap: 4rem;
  background: rgba(18, 43, 32, 0.4); /* Transparan gelap */
  border: 1px solid rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(10px);
  padding: 3rem;
  border-radius: 20px;
  max-width: 1000px;
  width: 100%;
}

.contact-info { flex: 1; }
.contact-form { flex: 1; display: flex; flex-direction: column; gap: 1.5rem; }

.contact-info h2 { font-size: 2.5rem; margin-bottom: 1rem; }
.contact-desc { color: var(--text-secondary); line-height: 1.6; margin-bottom: 2rem; }

.info-items { display: flex; flex-direction: column; gap: 1.5rem; margin-bottom: 2.5rem; }
.info-item { display: flex; gap: 1rem; align-items: center; }
.icon { background: rgba(16, 185, 129, 0.1); padding: 0.8rem; border-radius: 12px; font-size: 1.2rem; }
.info-item strong { display: block; margin-bottom: 0.2rem; font-family: 'Fira Code', monospace;}
.info-item p { color: var(--text-secondary); font-size: 0.9rem; }

/* Styling Tombol Social Media Baru */
.social-links { display: flex; gap: 1rem; }
.social-btn { 
  display: flex; justify-content: center; align-items: center;
  width: 45px; height: 45px; border-radius: 12px;
  background: rgba(16, 185, 129, 0.1); 
  text-decoration: none; border: 1px solid transparent;
  transition: 0.3s;
}
.social-btn:hover { border-color: var(--accent-color); background: rgba(16, 185, 129, 0.2); }

/* --- STYLE UNTUK IKON SVG --- */
.svg-icon {
  width: 22px; /* Sesuaikan ukuran ikon biar pas di kotak */
  height: 22px;
  fill: var(--accent-color); /* Warna awal hijau aksen */
  transition: 0.3s ease;
}

/* Biar ikonnya tetap green/terang pas di-hover kotak-nya */
.social-btn:hover .svg-icon {
  fill: white; /* Optional: ubah jadi putih pas di-hover kotak-nya biar kontras */
}

.form-group { display: flex; flex-direction: column; gap: 0.5rem; }
.form-group label { font-weight: 600; font-size: 0.9rem; }
.form-group input, .form-group textarea {
  background: rgba(0, 0, 0, 0.2);
  border: 1px solid rgba(255, 255, 255, 0.1);
  color: white; padding: 1rem; border-radius: 8px; font-family: 'Inter', sans-serif;
  transition: 0.3s;
}
.form-group input:focus, .form-group textarea:focus {
  outline: none; border-color: var(--accent-color);
}

.btn-send {
  background: var(--accent-color); color: white; border: none;
  padding: 1rem; border-radius: 8px; font-weight: bold; font-size: 1rem;
  cursor: pointer; transition: 0.3s; margin-top: 1rem;
}
.btn-send:hover { background: #0ea5e9; }

@media (max-width: 800px) {
  .contact-container { flex-direction: column; padding: 2rem; }
}
</style>