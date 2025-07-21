<script setup lang="ts">
import { useRouter } from 'vue-router'

const router = useRouter()

const goToCollection = (category: string) => {
  router.push({
    path: '/collection',
    query: { category },
  })
}
</script>

<template>
  <div class="home">
    <!-- Hero Section -->
    <section class="hero">
      <div class="hero-content">
        <div class="hero-text">
          <h1 class="hero-title">🎨 Hirfat Art Studio</h1>
          <p class="hero-slogan">Made in India for the World</p>
          <p class="hero-subtitle">Promoting Hand Art to the World</p>
          <p class="hero-description">
            Discover the timeless beauty of authentic Chikankari embroidery. Each piece is
            meticulously handcrafted by skilled artisans in Lucknow, bringing you the finest
            traditional Indian hand art with delicate stitches and elegant patterns.
          </p>
          <div class="hero-buttons">
            <router-link to="/collection" class="cta-btn primary">
              🛍️ Explore Collection
            </router-link>
            <a
              href="https://www.etsy.com/shop/HirfatArtStudio"
              class="cta-btn secondary"
              target="_blank"
            >
              🛒 Shop on Etsy
            </a>
          </div>
        </div>
      </div>
    </section>

    <!-- Full Width Banner -->
    <section class="full-banner">
      <img
        src="/images/banner/banner.webp"
        alt="Hirfat Art Studio - Authentic Chikankari Collection"
        class="banner-image"
      />
    </section>

    <!-- About Section -->
    <section class="about">
      <div class="container">
        <div class="about-content">
          <div class="about-text">
            <h2>The Art of Chikankari</h2>
            <p>
              Hirfat Art Studio is dedicated to preserving and promoting the ancient art of
              Chikankari embroidery. Originating from Lucknow, India, this exquisite needlework
              technique has been passed down through generations of skilled artisans who create
              magic with just a needle and thread.
            </p>
            <p>
              Our master craftspeople use traditional techniques with over 36 different stitches to
              create contemporary designs, ensuring each piece tells a story of heritage, skill, and
              artistic excellence. From delicate kurta sets to elegant sarees, every creation is a
              testament to India's rich textile tradition.
            </p>
            <div class="features-grid">
              <div class="feature">
                <span class="feature-icon">🏺</span>
                <h4>Heritage Craft</h4>
                <p>Authentic Lucknowi Chikankari techniques preserved for centuries</p>
              </div>
              <div class="feature">
                <span class="feature-icon">👨‍🎨</span>
                <h4>Master Artisans</h4>
                <p>Skilled craftspeople with generations of expertise in traditional stitches</p>
              </div>
              <div class="feature">
                <span class="feature-icon">🌍</span>
                <h4>Global Reach</h4>
                <p>Bringing Indian heritage to customers worldwide through Etsy</p>
              </div>
              <div class="feature">
                <span class="feature-icon">💎</span>
                <h4>Premium Quality</h4>
                <p>Finest fabrics like Chanderi, Georgette, and Cotton with meticulous detailing</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Featured Categories -->
    <section class="categories">
      <div class="container">
        <h2 class="section-title">Our Signature Collections</h2>
        <div class="categories-grid">
          <!-- Kurti Category -->
          <div class="category-card" @click="goToCollection('kurti')">
            <div class="category-showcase">
              <img src="/images/products/kurti1.webp" alt="Kurti" class="category-image" />
            </div>
            <div class="category-info">
              <h3>Kurti</h3>
              <p>Elegant kurtis with traditional Chikankari embroidery</p>
              <span class="view-more">View Collection →</span>
            </div>
          </div>

          <!-- Kurti Pant Sets Category -->
          <div class="category-card" @click="goToCollection('kurti-pant-sets')">
            <div class="category-showcase">
              <img src="/images/products/kurti2.jpg" alt="Kurti Pant Sets" class="category-image" />
            </div>
            <div class="category-info">
              <h3>Kurti Pant Sets</h3>
              <p>Complete kurti and pant sets with intricate hand embroidery</p>
              <span class="view-more">View Collection →</span>
            </div>
          </div>

          <!-- Unstitched Category -->
          <div class="category-card" @click="goToCollection('unstitched')">
            <div class="category-showcase">
              <div class="placeholder-image">
                <span class="placeholder-text">Coming Soon</span>
              </div>
            </div>
            <div class="category-info">
              <h3>Unstitched</h3>
              <p>Unstitched fabric pieces for custom tailoring</p>
              <span class="view-more">View Collection →</span>
            </div>
          </div>

          <!-- Frock Suit Category -->
          <div class="category-card" @click="goToCollection('frock-suit')">
            <div class="category-showcase">
              <div class="placeholder-image">
                <span class="placeholder-text">Coming Soon</span>
              </div>
            </div>
            <div class="category-info">
              <h3>Frock Suit</h3>
              <p>Beautiful frock suits with Chikankari work</p>
              <span class="view-more">View Collection →</span>
            </div>
          </div>

          <!-- Lehanga Category -->
          <div class="category-card" @click="goToCollection('lehanga')">
            <div class="category-showcase">
              <div class="placeholder-image">
                <span class="placeholder-text">Coming Soon</span>
              </div>
            </div>
            <div class="category-info">
              <h3>Lehanga</h3>
              <p>Traditional lehangas with exquisite embroidery</p>
              <span class="view-more">View Collection →</span>
            </div>
          </div>

          <!-- Saree Category -->
          <div class="category-card" @click="goToCollection('saree')">
            <div class="category-showcase">
              <div class="placeholder-image">
                <span class="placeholder-text">Coming Soon</span>
              </div>
            </div>
            <div class="category-info">
              <h3>Saree</h3>
              <p>Elegant sarees with traditional Chikankari work</p>
              <span class="view-more">View Collection →</span>
            </div>
          </div>

          <!-- Co-ord Sets Category -->
          <div class="category-card" @click="goToCollection('co-ord-sets')">
            <div class="category-showcase">
              <div class="placeholder-image">
                <span class="placeholder-text">Coming Soon</span>
              </div>
            </div>
            <div class="category-info">
              <h3>Co-ord Sets</h3>
              <p>Stylish co-ord sets with hand embroidery</p>
              <span class="view-more">View Collection →</span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Why Choose Us -->
    <section class="why-choose-us">
      <div class="container">
        <h2 class="section-title">Why Choose Hirfat Art Studio</h2>
        <div class="benefits-grid">
          <div class="benefit">
            <div class="benefit-icon">✨</div>
            <h3>Authentic Craftsmanship</h3>
            <p>
              Every piece is hand-embroidered using traditional Lucknowi techniques with over 36
              different stitches, ensuring authenticity and quality.
            </p>
          </div>
          <div class="benefit">
            <div class="benefit-icon">🚚</div>
            <h3>Worldwide Shipping</h3>
            <p>
              We deliver our beautiful creations to customers around the globe through our Etsy
              store with secure and reliable shipping.
            </p>
          </div>
          <div class="benefit">
            <div class="benefit-icon">💯</div>
            <h3>Quality Guaranteed</h3>
            <p>
              Premium fabrics like Chanderi, Georgette, and Cotton, expert craftsmanship, and
              rigorous quality checks ensure your satisfaction.
            </p>
          </div>
          <div class="benefit">
            <div class="benefit-icon">🎨</div>
            <h3>Unique Designs</h3>
            <p>
              Our designs blend traditional Mughal-inspired motifs with contemporary aesthetics for
              the modern connoisseur.
            </p>
          </div>
        </div>
      </div>
    </section>

    <!-- Testimonials -->
    <section class="testimonials">
      <div class="container">
        <h2 class="section-title">What Our Customers Say</h2>
        <div class="testimonials-grid">
          <div class="testimonial-card">
            <div class="testimonial-content">
              <p>
                "The quality of Chikankari work is exceptional. The intricate embroidery and
                attention to detail is remarkable. I've received so many compliments!"
              </p>
              <div class="customer-info">
                <div class="customer-avatar">S</div>
                <div class="customer-details">
                  <h4>Sarah Johnson</h4>
                  <div class="rating">⭐⭐⭐⭐⭐</div>
                </div>
              </div>
            </div>
          </div>
          <div class="testimonial-card">
            <div class="testimonial-content">
              <p>
                "Beautiful traditional work with modern styling. The fabric quality is superb and
                the fit is perfect. Definitely ordering more pieces!"
              </p>
              <div class="customer-info">
                <div class="customer-avatar">M</div>
                <div class="customer-details">
                  <h4>Maria Garcia</h4>
                  <div class="rating">⭐⭐⭐⭐⭐</div>
                </div>
              </div>
            </div>
          </div>
          <div class="testimonial-card">
            <div class="testimonial-content">
              <p>
                "Hirfat Art Studio delivers authentic Indian craftsmanship. The Chikankari work is
                exquisite and the customer service is outstanding."
              </p>
              <div class="customer-info">
                <div class="customer-avatar">A</div>
                <div class="customer-details">
                  <h4>Aisha Patel</h4>
                  <div class="rating">⭐⭐⭐⭐⭐</div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- CTA Section -->
    <section class="cta-section">
      <div class="container">
        <div class="cta-content">
          <h2>Experience the Beauty of Authentic Chikankari</h2>
          <p>
            Browse our complete collection on Etsy and discover the perfect piece that speaks to
            your style and celebrates the timeless art of Indian embroidery.
          </p>
          <div class="cta-buttons">
            <router-link to="/collection" class="btn-primary">View Our Collection</router-link>
            <a
              href="https://www.etsy.com/shop/HirfatArtStudio"
              target="_blank"
              class="btn-secondary"
            >
              Shop on Etsy
            </a>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<style scoped>
.home {
  background: #faf9f6;
}

/* Hero Section */
.hero {
  background: linear-gradient(135deg, #f8f6f0 0%, #f5f2e8 100%);
  padding: 4rem 0;
  border-bottom: 1px solid #e8e4d8;
}

.hero-content {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
}

/* Full Width Banner */
.full-banner {
  width: 100%;
  height: 500px;
  overflow: hidden;
  position: relative;
}

.banner-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}

.hero-title {
  font-size: 3.5rem;
  font-weight: 700;
  color: #8b6914;
  margin-bottom: 1rem;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.1);
}

.hero-slogan {
  font-size: 1.2rem;
  color: #b8860b;
  font-weight: 500;
  margin-bottom: 0.5rem;
}

.hero-subtitle {
  font-size: 1.1rem;
  color: #8b6914;
  margin-bottom: 1.5rem;
  font-style: italic;
}

.hero-description {
  font-size: 1.1rem;
  color: #6b5b3a;
  line-height: 1.7;
  margin-bottom: 2rem;
}

.hero-buttons {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
}

.cta-btn {
  padding: 1rem 2rem;
  border-radius: 8px;
  text-decoration: none;
  font-weight: 600;
  font-size: 1.1rem;
  transition: all 0.3s ease;
  border: none;
  cursor: pointer;
}

.cta-btn.primary {
  background: linear-gradient(135deg, #daa520 0%, #b8860b 100%);
  color: white;
  box-shadow: 0 4px 15px rgba(218, 165, 32, 0.3);
}

.cta-btn.primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(218, 165, 32, 0.4);
}

.cta-btn.secondary {
  background: #f8f6f0;
  color: #8b6914;
  border: 2px solid #daa520;
}

.cta-btn.secondary:hover {
  background: #daa520;
  color: white;
}

.banner-container {
  position: relative;
  border-radius: 15px;
  overflow: hidden;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
  border: 2px solid #e8e4d8;
}

.hero-banner {
  width: 100%;
  height: 400px;
  object-fit: cover;
  display: block;
}

/* About Section */
.about {
  padding: 5rem 0;
  background: #fff;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
}

.about-text h2 {
  font-size: 2.5rem;
  color: #8b6914;
  text-align: center;
  margin-bottom: 2rem;
}

.about-text p {
  font-size: 1.1rem;
  color: #6b5b3a;
  line-height: 1.8;
  margin-bottom: 1.5rem;
  text-align: center;
  max-width: 800px;
  margin-left: auto;
  margin-right: auto;
}

.features-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
  margin-top: 3rem;
}

.feature {
  text-align: center;
  padding: 2rem;
  background: #f8f6f0;
  border-radius: 10px;
  border: 1px solid #e8e4d8;
  transition: transform 0.3s ease;
}

.feature:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
}

.feature-icon {
  font-size: 3rem;
  margin-bottom: 1rem;
  display: block;
}

.feature h4 {
  font-size: 1.3rem;
  color: #8b6914;
  margin-bottom: 1rem;
}

.feature p {
  color: #6b5b3a;
  line-height: 1.6;
}

/* Categories Section */
.categories {
  padding: 5rem 0;
  background: #f8f6f0;
}

.section-title {
  font-size: 2.5rem;
  text-align: center;
  color: #8b6914;
  margin-bottom: 3rem;
}

.categories-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 2rem;
}

.category-card {
  background: white;
  border-radius: 15px;
  overflow: hidden;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease;
  cursor: pointer;
  border: 2px solid #e8e4d8;
}

.category-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 15px 35px rgba(0, 0, 0, 0.15);
}

.category-showcase {
  height: 200px;
  background: linear-gradient(135deg, #f8f6f0 0%, #fff 100%);
  display: flex;
  align-items: center;
  justify-content: center;
  border-bottom: 1px solid #e8e4d8;
  overflow: hidden;
  position: relative;
}

.category-info {
  padding: 2rem;
  text-align: center;
}

.category-info h3 {
  font-size: 1.5rem;
  color: #8b6914;
  margin-bottom: 1rem;
}

.category-info p {
  color: #6b5b3a;
  line-height: 1.6;
  margin-bottom: 1.5rem;
}

.view-more {
  color: #daa520;
  font-weight: 600;
  font-size: 1.1rem;
}

.category-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
  transition: transform 0.3s ease;
}

.category-card:hover .category-image {
  transform: scale(1.1);
}

.placeholder-image {
  width: 100%;
  height: 100%;
  background: linear-gradient(135deg, #f8f6f0 0%, #e8e4d8 100%);
  display: flex;
  align-items: center;
  justify-content: center;
  border: 2px dashed #daa520;
}

.placeholder-text {
  color: #8b6914;
  font-size: 1.2rem;
  font-weight: 600;
  text-align: center;
}

/* Why Choose Us */
.why-choose-us {
  padding: 5rem 0;
  background: white;
}

.benefits-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
}

.benefit {
  text-align: center;
  padding: 2.5rem 2rem;
  background: #f8f6f0;
  border-radius: 10px;
  border: 1px solid #e8e4d8;
  transition: transform 0.3s ease;
}

.benefit:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
}

.benefit-icon {
  font-size: 3rem;
  margin-bottom: 1.5rem;
  display: block;
}

.benefit h3 {
  font-size: 1.4rem;
  color: #8b6914;
  margin-bottom: 1rem;
}

.benefit p {
  color: #6b5b3a;
  line-height: 1.6;
}

/* Testimonials */
.testimonials {
  padding: 5rem 0;
  background: #f8f6f0;
}

.testimonials-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
}

.testimonial-card {
  background: white;
  padding: 2rem;
  border-radius: 10px;
  border: 1px solid #e8e4d8;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
}

.testimonial-content p {
  color: #6b5b3a;
  line-height: 1.6;
  margin-bottom: 1.5rem;
  font-style: italic;
}

.customer-info {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.customer-avatar {
  width: 50px;
  height: 50px;
  border-radius: 50%;
  background: linear-gradient(135deg, #daa520 0%, #b8860b 100%);
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: bold;
  font-size: 1.2rem;
}

.customer-details h4 {
  color: #8b6914;
  margin-bottom: 0.25rem;
}

.rating {
  font-size: 0.9rem;
}

/* CTA Section */
.cta-section {
  padding: 5rem 0;
  background: linear-gradient(135deg, #8b6914 0%, #daa520 100%);
  color: white;
  text-align: center;
}

.cta-content h2 {
  font-size: 2.5rem;
  margin-bottom: 1.5rem;
}

.cta-content p {
  font-size: 1.2rem;
  line-height: 1.7;
  margin-bottom: 2.5rem;
  max-width: 600px;
  margin-left: auto;
  margin-right: auto;
}

.cta-buttons {
  display: flex;
  gap: 1rem;
  justify-content: center;
  flex-wrap: wrap;
}

.btn-primary,
.btn-secondary {
  padding: 1rem 2rem;
  border-radius: 8px;
  text-decoration: none;
  font-weight: 600;
  font-size: 1.1rem;
  transition: all 0.3s ease;
}

.btn-primary {
  background: white;
  color: #8b6914;
}

.btn-primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
}

.btn-secondary {
  background: transparent;
  color: white;
  border: 2px solid white;
}

.btn-secondary:hover {
  background: white;
  color: #8b6914;
}

/* Responsive Design */
@media (max-width: 768px) {
  .hero-content {
    text-align: center;
  }

  .hero-title {
    font-size: 2.5rem;
  }

  .full-banner {
    height: 300px;
  }

  .categories-grid {
    grid-template-columns: 1fr;
  }

  .benefits-grid {
    grid-template-columns: 1fr;
  }

  .testimonials-grid {
    grid-template-columns: 1fr;
  }

  .cta-buttons {
    flex-direction: column;
    align-items: center;
  }
}

@media (max-width: 600px) {
  .full-banner {
    height: 180px;
  }
  .banner-image {
    object-fit: contain;
  }
}
</style>
