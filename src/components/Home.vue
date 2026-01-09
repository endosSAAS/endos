<script setup>
import heroImage from "../assets/image.png";
</script>

<template>
  <main>
    <header class="hero container">
      <div class="hero-content">
        <div class="hero-label vim-cursor">CUSTOM DEVELOPMENT</div>
        <h1 class="hero-title">SOFTWARE AS A SERVICE<br />WEB & MOBILE APPS</h1>
        <p class="hero-subtitle">
          Custom websites, hybrid mobile applications, and automation scripts.
          Built with React, NextJS, Rust, Python, and C++.
        </p>
        <div class="hero-buttons">
          <a
            href="https://maps.app.goo.gl/6teBYEfYSgPnAp9v7?g_st=ipc"
            target="_blank"
            class="btn btn-primary"
            style="text-decoration: none"
            >Contact Us</a
          >
          <a
            href="https://nano-sketch.github.io/porfv/"
            target="_blank"
            class="btn btn-secondary"
            style="text-decoration: none"
            >Portfolio</a
          >
        </div>
      </div>
      <div class="hero-image-wrapper">
        <img
          :src="heroImage"
          alt="Endos Services"
          class="hero-image no-drag"
          draggable="false"
          fetchpriority="high"
          loading="eager"
          decoding="async"
        />
      </div>
    </header>
    <section id="services" class="features container">
      <div class="features-header"><h2>OUR SERVICES</h2></div>
      <div class="features-grid">
        <div class="feature-card">
          <div class="feature-icon">01</div>
          <h3>Web & Mobile Dev</h3>
          <p>
            Websites in React, NextJS, VueJS, or HTML/CSS. Mobile apps using
            React Native and Tauri.
          </p>
        </div>
        <div class="feature-card">
          <div class="feature-icon">02</div>
          <h3>Automation & Native</h3>
          <p>
            Scripts in Python, Rust, Go (web-scraping). Native Windows apps in
            C++, .NET, Java.
          </p>
        </div>
        <div class="feature-card">
          <div class="feature-icon">03</div>
          <h3>Security & Backend</h3>
          <p>
            MongoDB backend setup. Forensic analysis on PE executables and
            cybersecurity services.
          </p>
        </div>
      </div>
    </section>
  </main>
</template>

<style scoped>
main {
  display: flex;
  flex-direction: column;
  gap: 4rem;
}
.hero {
  display: grid;
  grid-template-columns: 1fr;
  gap: 2rem;
  padding-top: 2rem;
  align-items: start;
}
.hero-content {
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding-top: 1rem;
}
.hero-label {
  font-family: var(--font-mono);
  font-size: 0.7rem;
  color: var(--text-secondary);
  margin-bottom: 0.5rem;
}
.hero-label::before {
  content: "$ ";
  color: var(--primary-color);
}
.hero-title {
  font-size: 1.8rem;
  line-height: 1.1;
  font-weight: 700;
  margin-bottom: 1rem;
  letter-spacing: -0.04em;
  text-transform: uppercase;
}
.hero-subtitle {
  font-size: 0.9rem;
  color: var(--text-secondary);
  margin-bottom: 1.5rem;
  max-width: 450px;
  line-height: 1.5;
  border-left: 2px solid var(--border-color);
  padding-left: 1rem;
}
.hero-buttons {
  display: flex;
  gap: 0.75rem;
}
.hero-image-wrapper {
  background: rgba(255, 255, 255, 0.02);
  border: 1px solid rgba(255, 255, 255, 0.1);
  padding: 0.5rem;
  border-radius: 4px;
  backdrop-filter: blur(5px);
  -webkit-backdrop-filter: blur(5px);
  max-width: 90%;
  margin: 0 auto;
}
.hero-image {
  width: 100%;
  height: auto;
  display: block;
  opacity: 0.9;
  border-radius: 2px;
  filter: grayscale(100%) contrast(1.1);
}
.no-drag {
  user-select: none;
  -webkit-user-drag: none;
  pointer-events: none;
}
@media (min-width: 1024px) {
  .hero {
    grid-template-columns: 1.2fr 0.8fr;
    gap: 3rem;
  }
  .hero-title {
    font-size: 2.5rem;
  }
  .hero-image-wrapper {
    margin: 0;
  }
}
.features-header {
  margin-bottom: 1.5rem;
  padding-bottom: 0.5rem;
  border-bottom: 1px dashed var(--border-color);
}
.features-header h2 {
  font-family: var(--font-mono);
  font-size: 0.9rem;
  font-weight: 700;
  color: var(--text-secondary);
  text-transform: uppercase;
}
.features-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 1rem;
}
.feature-card {
  padding: 1rem;
  border: 1px solid var(--border-color);
  background: var(--surface-color);
  transition: all 0.2s;
}
.feature-card:hover {
  border-color: var(--text-secondary);
  background: #111;
}
.feature-icon {
  font-family: var(--font-mono);
  font-size: 0.7rem;
  color: var(--text-secondary);
  margin-bottom: 0.5rem;
}
.feature-card h3 {
  font-size: 1rem;
  font-weight: 700;
  margin-bottom: 0.5rem;
  color: var(--text-primary);
}
.feature-card p {
  color: var(--text-secondary);
  font-size: 0.8rem;
  line-height: 1.4;
}
@media (min-width: 768px) {
  .features-grid {
    grid-template-columns: repeat(3, 1fr);
  }
}
</style>
