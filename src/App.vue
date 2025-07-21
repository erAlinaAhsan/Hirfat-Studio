<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <div id="app">
    <header class="main-header">
      <nav class="navbar">
        <div class="nav-container">
          <div class="nav-brand">
            <div class="brand-logo">
              <img src="/images/logo/logo.jpg" alt="Hirfat Art Studio Logo" class="logo-image" />
              <div class="brand-text">
                <h1>🎨 Hirfat Art Studio</h1>
                <span class="tagline">Promoting Hand Art to the World</span>
              </div>
            </div>
          </div>
          <div class="nav-links">
            <RouterLink to="/" class="nav-link">Home</RouterLink>
            <RouterLink to="/collection" class="nav-link">Collection</RouterLink>
            <RouterLink to="/about" class="nav-link">About</RouterLink>
            <a href="https://wa.me/your-number" class="whatsapp-link" target="_blank">
              📱 WhatsApp
            </a>
          </div>
        </div>
      </nav>
    </header>

    <main class="main-content">
      <RouterView />
    </main>

    <footer class="main-footer">
      <div class="footer-content">
        <div class="footer-section">
          <h3>🎨 Hirfat Art Studio</h3>
          <p>
            Promoting hand art to the world. Exquisite hand-embroidered chikankari pieces crafted
            with love and tradition in India.
          </p>
        </div>
        <div class="footer-section">
          <h4>Quick Links</h4>
          <div class="footer-links">
            <RouterLink to="/">Home</RouterLink>
            <RouterLink to="/collection">Collection</RouterLink>
            <RouterLink to="/about">About</RouterLink>
          </div>
        </div>
        <div class="footer-section">
          <h4>Connect With Us</h4>
          <div class="social-links">
            <a href="https://wa.me/your-number" target="_blank">WhatsApp</a>
            <a href="https://www.etsy.com/shop/HirfatArtStudio" target="_blank">Etsy Store</a>
            <a href="mailto:contact@hirfatstudio.com">Email</a>
          </div>
        </div>
      </div>
      <div class="footer-bottom">
        <p>&copy; 2024 Hirfat Art Studio. All rights reserved. | Made in India for the World</p>
      </div>
    </footer>
  </div>
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family:
    'Inter',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    sans-serif;
  line-height: 1.6;
  color: #333;
  background: #faf9f6;
}

#app {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

/* Header Styles */
.main-header {
  background: linear-gradient(135deg, #8b6914 0%, #daa520 50%, #b8860b 100%);
  color: white;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  position: sticky;
  top: 0;
  z-index: 100;
}

.navbar {
  padding: 1rem 0;
}

.nav-container {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 2rem;
}

.brand-logo {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.logo-image {
  width: 50px;
  height: 50px;
  border-radius: 50%;
  object-fit: cover;
  border: 2px solid white;
}

.brand-text h1 {
  font-size: 1.8rem;
  font-weight: 700;
  margin-bottom: 0.2rem;
  color: white;
}

.tagline {
  font-size: 0.85rem;
  opacity: 0.9;
  font-style: italic;
  color: #f5f2e8;
}

.nav-links {
  display: flex;
  align-items: center;
  gap: 2rem;
}

.nav-link {
  color: white;
  text-decoration: none;
  font-weight: 500;
  padding: 0.5rem 1rem;
  border-radius: 5px;
  transition: all 0.3s ease;
}

.nav-link:hover {
  background: rgba(255, 255, 255, 0.1);
  transform: translateY(-1px);
}

.nav-link.router-link-active {
  background: rgba(255, 255, 255, 0.2);
  font-weight: 600;
}

.whatsapp-link {
  background: #25d366;
  color: white;
  text-decoration: none;
  padding: 0.6rem 1.2rem;
  border-radius: 25px;
  font-weight: 600;
  transition: all 0.3s ease;
  border: 2px solid transparent;
}

.whatsapp-link:hover {
  background: #22c55e;
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(37, 211, 102, 0.3);
}

/* Main Content */
.main-content {
  flex: 1;
}

/* Footer Styles */
.main-footer {
  background: linear-gradient(135deg, #6b5b3a 0%, #8b6914 100%);
  color: white;
  padding: 3rem 0 1rem;
  margin-top: auto;
}

.footer-content {
  max-width: 1200px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 2fr 1fr 1fr;
  gap: 3rem;
  padding: 0 2rem;
}

.footer-section h3 {
  font-size: 1.4rem;
  margin-bottom: 1rem;
  color: #f5f2e8;
}

.footer-section h4 {
  font-size: 1.1rem;
  margin-bottom: 1rem;
  color: #f5f2e8;
}

.footer-section p {
  line-height: 1.6;
  opacity: 0.9;
  margin-bottom: 1rem;
}

.footer-links {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.footer-links a {
  color: white;
  text-decoration: none;
  opacity: 0.8;
  transition: opacity 0.3s ease;
}

.footer-links a:hover {
  opacity: 1;
  color: #f5f2e8;
}

.social-links {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.social-links a {
  color: white;
  text-decoration: none;
  opacity: 0.8;
  transition: all 0.3s ease;
}

.social-links a:hover {
  opacity: 1;
  color: #f5f2e8;
  transform: translateX(5px);
}

.footer-bottom {
  border-top: 1px solid rgba(255, 255, 255, 0.2);
  margin-top: 2rem;
  padding-top: 1rem;
  text-align: center;
  opacity: 0.8;
}

/* Responsive Design */
@media (max-width: 768px) {
  .nav-container {
    flex-direction: column;
    gap: 1rem;
    text-align: center;
  }

  .nav-links {
    flex-wrap: wrap;
    justify-content: center;
    gap: 1rem;
  }

  .footer-content {
    grid-template-columns: 1fr;
    gap: 2rem;
    text-align: center;
  }

  .footer-links,
  .social-links {
    flex-direction: row;
    justify-content: center;
    flex-wrap: wrap;
  }
}

@media (max-width: 480px) {
  .nav-brand h1 {
    font-size: 1.5rem;
  }

  .nav-links {
    gap: 0.5rem;
  }

  .nav-link {
    padding: 0.4rem 0.8rem;
    font-size: 0.9rem;
  }
}
</style>
