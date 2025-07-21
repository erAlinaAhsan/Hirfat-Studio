<template>
  <div class="collection-page">
    <!-- Banner Section -->
    <section class="page-banner">
      <div class="banner-container">
        <img
          src="/images/banner/banner.webp"
          alt="Hirfat Art Studio - Chikankari Collection"
          class="page-banner-image"
        />
      </div>
    </section>

    <!-- Header Section -->
    <section class="collection-header">
      <div class="container">
        <h1 class="page-title">Our Chikankari Collection</h1>
        <p class="page-subtitle">Handcrafted masterpieces from the heart of India</p>
      </div>
    </section>

    <!-- Filter Section -->
    <section class="filter-section">
      <div class="container">
        <div class="filter-tabs">
          <button
            v-for="category in categories"
            :key="category.id"
            @click="setActiveCategory(category.id)"
            :class="['filter-tab', { active: activeCategory === category.id }]"
          >
            <span class="tab-icon">{{ category.icon }}</span>
            {{ category.name }}
            <span class="product-count">({{ getProductCount(category.id) }})</span>
          </button>
        </div>
      </div>
    </section>

    <!-- Products Grid -->
    <section class="products-section">
      <div class="container">
        <div class="products-header">
          <h2 class="category-title">{{ getActiveCategoryName() }}</h2>
          <p class="category-description">{{ getActiveCategoryDescription() }}</p>
        </div>

        <div class="products-grid">
          <div
            v-for="product in allProducts"
            :key="product.id"
            class="product-card"
            :class="{ hidden: !isProductVisible(product) }"
            @click="openEtsyStore"
          >
            <div class="product-showcase">
              <div class="product-image-container">
                <img :src="product.image" :alt="product.name" class="product-image" />
                <div class="fabric-badge">{{ product.fabric }}</div>
              </div>
              <div class="product-overlay">
                <div class="overlay-content">
                  <h3>{{ product.name }}</h3>
                  <p>{{ product.description }}</p>
                  <button class="buy-btn">
                    <span class="buy-icon">🛒</span>
                    Buy on Etsy
                  </button>
                </div>
              </div>
            </div>
            <div class="product-info">
              <h4 class="product-name">{{ product.name }}</h4>
              <p class="product-type">{{ product.category }}</p>
              <div class="product-features">
                <span v-for="feature in product.features" :key="feature" class="feature-tag">
                  {{ feature }}
                </span>
              </div>
            </div>
          </div>
        </div>

        <div class="view-more-section">
          <a href="https://www.etsy.com/shop/HirfatArtStudio" target="_blank" class="view-more-btn">
            View Complete Collection on Etsy →
          </a>
        </div>
      </div>
    </section>

    <!-- Customer Reviews -->
    <section class="reviews-section">
      <div class="container">
        <h2 class="section-title">What Our Customers Say</h2>
        <div class="reviews-grid">
          <div v-for="review in customerReviews" :key="review.id" class="review-card">
            <div class="review-header">
              <div class="customer-info">
                <div class="customer-avatar">{{ review.avatar }}</div>
                <div class="customer-details">
                  <h4 class="customer-name">{{ review.name }}</h4>
                  <div class="review-rating">
                    <span class="stars">{{ review.stars }}</span>
                    <span class="rating-text">{{ review.rating }}/5</span>
                  </div>
                </div>
              </div>
              <div class="review-date">{{ review.date }}</div>
            </div>
            <p class="review-text">{{ review.text }}</p>
            <div class="review-product">
              <span class="product-label">Purchased:</span>
              <span class="product-name">{{ review.productPurchased }}</span>
            </div>
          </div>
        </div>

        <div class="reviews-cta">
          <p>See more reviews on our Etsy store</p>
          <a
            href="https://www.etsy.com/shop/HirfatArtStudio"
            target="_blank"
            class="etsy-reviews-btn"
          >
            View Etsy Reviews →
          </a>
        </div>
      </div>
    </section>

    <!-- About Chikankari -->
    <section class="about-craft">
      <div class="container">
        <div class="craft-content">
          <div class="craft-text">
            <h2>The Timeless Art of Chikankari</h2>
            <p>
              Chikankari is a traditional embroidery technique that originated in Lucknow, the
              capital city of Uttar Pradesh, India. This delicate and intricate form of needlework
              has been practiced for centuries and is considered one of India's finest textile arts.
            </p>
            <p>
              At Hirfat Art Studio, our master artisans use traditional techniques passed down
              through generations. Each piece requires weeks of meticulous handwork, with different
              stitches creating beautiful patterns and textures that make every garment unique.
            </p>
            <div class="craft-highlights">
              <div class="highlight">
                <span class="highlight-icon">🧵</span>
                <div>
                  <h4>Traditional Stitches</h4>
                  <p>36 different traditional stitches used in authentic Chikankari</p>
                </div>
              </div>
              <div class="highlight">
                <span class="highlight-icon">⏱️</span>
                <div>
                  <h4>Time-Intensive Process</h4>
                  <p>Each piece takes 15-30 days to complete by hand</p>
                </div>
              </div>
              <div class="highlight">
                <span class="highlight-icon">🌸</span>
                <div>
                  <h4>Floral Motifs</h4>
                  <p>Inspired by Mughal gardens and Persian patterns</p>
                </div>
              </div>
            </div>
          </div>
          <div class="craft-showcase">
            <div class="traditional-patterns">
              <div class="pattern-item">
                <div class="pattern-icon">🌺</div>
                <p>Traditional Motifs</p>
              </div>
              <div class="pattern-item">
                <div class="pattern-icon">🌿</div>
                <p>Nature Inspired</p>
              </div>
              <div class="pattern-item">
                <div class="pattern-icon">🪷</div>
                <p>Royal Heritage</p>
              </div>
              <div class="pattern-item">
                <div class="pattern-icon">✨</div>
                <p>Hand Embroidered</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup lang="ts">
import { ref, computed, onMounted } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()
const activeCategory = ref('all')

const categories = ref([
  {
    id: 'all',
    name: 'All Products',
    icon: '🌟',
    description: 'Our complete collection of handcrafted Chikankari pieces',
  },
  {
    id: 'kurti',
    name: 'Kurti',
    icon: '👘',
    description: 'Elegant kurtis with traditional Chikankari embroidery',
  },
  {
    id: 'kurti-pant-sets',
    name: 'Kurti Pant Sets',
    icon: '👗',
    description: 'Complete kurti and pant sets with intricate hand embroidery',
  },
  {
    id: 'unstitched',
    name: 'Unstitched',
    icon: '✂️',
    description: 'Unstitched fabric pieces for custom tailoring',
  },
  {
    id: 'frock-suit',
    name: 'Frock Suit',
    icon: '👑',
    description: 'Beautiful frock suits with Chikankari work',
  },
  {
    id: 'lehanga',
    name: 'Lehanga',
    icon: '💃',
    description: 'Traditional lehangas with exquisite embroidery',
  },
  {
    id: 'saree',
    name: 'Saree',
    icon: '🥻',
    description: 'Elegant sarees with traditional Chikankari work',
  },
  {
    id: 'co-ord-sets',
    name: 'Co-ord Sets',
    icon: '✨',
    description: 'Stylish co-ord sets with hand embroidery',
  },
])

// Product collection using your actual kurti images
const allProducts = ref([
  // Kurti Category (kurti1, kurti4, kurti9, kurti10)
  {
    id: 1,
    name: 'Royal Blue Georgette Chikankari Kurti',
    category: "Women's Kurti",
    image: '/images/products/kurti1.webp',
    fabric: 'Pure Georgette',
    type: 'kurti',
    description: 'Elegant blue georgette kurti with traditional Chikankari embroidery',
    features: ['Pure Georgette', 'Hand Embroidered', 'Casual Wear'],
  },
  {
    id: 4,
    name: 'Yellow Georgette Chikankari Kurti',
    category: "Women's Kurti",
    image: '/images/products/kurti4.jpg',
    fabric: 'Georgette',
    type: 'kurti',
    description: 'Bright yellow georgette kurti with traditional embroidery',
    features: ['Georgette Fabric', 'Vibrant Color', 'Festival Wear'],
  },
  {
    id: 9,
    name: 'Designer Chikankari Kurti',
    category: "Women's Kurti",
    image: '/images/products/kurti10.webp',
    fabric: 'Georgette',
    type: 'kurti',
    description: 'Stunning designer kurti for special occasions',
    features: ['Designer Piece', 'Heavy Work', 'Special Occasion'],
  },

  // Kurti Pant Sets Category (kurti2, kurti3, kurti5, kurti6, kurti7, kurti8)
  {
    id: 2,
    name: 'Maroon Cotton Chikankari Kurti Pant Set',
    category: "Women's Kurti Pant Set",
    image: '/images/products/kurti2.jpg',
    fabric: 'Cotton',
    type: 'kurti-pant-sets',
    description: 'Beautiful maroon cotton kurti pant set with intricate floral motifs',
    features: ['100% Cotton', 'Floral Motifs', 'Complete Set'],
  },
  {
    id: 3,
    name: 'Purple Chanderi Chikankari Kurti Pant Set',
    category: "Women's Kurti Pant Set",
    image: '/images/products/kurti3.jpg',
    fabric: 'Chanderi Silk',
    type: 'kurti-pant-sets',
    description: 'Stunning purple chanderi kurti pant set perfect for festivities',
    features: ['Chanderi Silk', 'Festival Wear', 'Elegant Design'],
  },
  {
    id: 5,
    name: 'White Cotton Chikankari Kurti Pant Set',
    category: "Women's Kurti Pant Set",
    image: '/images/products/kurti5.jpg',
    fabric: 'Pure Cotton',
    type: 'kurti-pant-sets',
    description: 'Classic white cotton kurti pant set with green thread embroidery',
    features: ['Pure Cotton', 'Green Thread', 'Versatile'],
  },
  {
    id: 6,
    name: 'Pink Georgette Chikankari Kurti Pant Set',
    category: "Women's Kurti Pant Set",
    image: '/images/products/kurti6.webp',
    fabric: 'Georgette',
    type: 'kurti-pant-sets',
    description: 'Graceful pink kurti pant set with delicate handwork',
    features: ['Party Wear', 'Georgette', 'Flowing Style'],
  },
  {
    id: 7,
    name: 'Red Chikankari Kurti Pant Set with Mirror Work',
    category: "Women's Kurti Pant Set",
    image: '/images/products/kurti7.webp',
    fabric: 'Cotton Silk',
    type: 'kurti-pant-sets',
    description: 'Vibrant red kurti pant set with traditional mirror and thread work',
    features: ['Mirror Work', 'Cotton Silk', 'Traditional'],
  },
  {
    id: 8,
    name: 'Traditional Chikankari Kurti Pant Set',
    category: "Women's Kurti Pant Set",
    image: '/images/products/kurti8.webp',
    fabric: 'Mul Cotton',
    type: 'kurti-pant-sets',
    description: 'Elegant traditional kurti pant set perfect for celebrations',
    features: ['Mul Cotton', 'Traditional Style', 'Celebration Wear'],
  },

  // Empty categories (Unstitched, Frock Suit, Lehanga, Saree, Co-ord Sets)
  // These will be populated when you provide the images
])

// Customer reviews
const customerReviews = ref([
  {
    id: 1,
    name: 'Sarah Johnson',
    avatar: 'S',
    rating: 5,
    stars: '⭐⭐⭐⭐⭐',
    date: 'March 2024',
    text: 'Absolutely stunning! The Chikankari work is so intricate and beautiful. The quality exceeded my expectations.',
    productPurchased: 'Blue Georgette Kurta Set',
  },
  {
    id: 2,
    name: 'Priya Sharma',
    avatar: 'P',
    rating: 5,
    stars: '⭐⭐⭐⭐⭐',
    date: 'February 2024',
    text: 'Perfect fit and gorgeous embroidery. I received so many compliments! Will definitely order again.',
    productPurchased: 'Purple Chikankari Anarkali',
  },
  {
    id: 3,
    name: 'Maria Garcia',
    avatar: 'M',
    rating: 5,
    stars: '⭐⭐⭐⭐⭐',
    date: 'January 2024',
    text: 'The traditional craftsmanship is remarkable. Each stitch tells a story. Hirfat Art Studio is amazing!',
    productPurchased: 'White Cotton Co-ord Set',
  },
])

// Computed properties and methods
const getActiveCategoryName = () => {
  const category = categories.value.find((cat) => cat.id === activeCategory.value)
  return category ? category.name : 'All Products'
}

const getActiveCategoryDescription = () => {
  const category = categories.value.find((cat) => cat.id === activeCategory.value)
  return category
    ? category.description
    : 'Our complete collection of handcrafted Chikankari pieces'
}

const getProductCount = (categoryId: string) => {
  if (categoryId === 'all') return allProducts.value.length
  return allProducts.value.filter((product) => product.type === categoryId).length
}

const isProductVisible = (product: any) => {
  if (activeCategory.value === 'all') return true
  return product.type === activeCategory.value
}

const setActiveCategory = (categoryId: string) => {
  activeCategory.value = categoryId
}

const openEtsyStore = () => {
  window.open('https://www.etsy.com/shop/HirfatArtStudio', '_blank')
}

// Initialize category from route query
onMounted(() => {
  if (route.query.category) {
    activeCategory.value = route.query.category as string
  }
})
</script>

<style scoped>
.collection-page {
  background: #faf9f6;
  min-height: 100vh;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0;
}

/* Banner Section */
.page-banner {
  position: relative;
  height: 300px;
  overflow: hidden;
  margin-bottom: 0;
}

.banner-container {
  position: relative;
  width: 100%;
  height: 100%;
}

.page-banner-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}

/* Header Section */
.collection-header {
  background: linear-gradient(135deg, #f8f6f0 0%, #f5f2e8 100%);
  padding: 4rem 0 2rem;
  text-align: center;
  border-bottom: 1px solid #e8e4d8;
}

.page-title {
  font-size: 3rem;
  color: #8b6914;
  margin-bottom: 1rem;
  font-weight: 700;
}

.page-subtitle {
  font-size: 1.3rem;
  color: #b8860b;
  font-style: italic;
}

/* Filter Section */
.filter-section {
  background: #fff;
  padding: 2rem 0;
  border-bottom: 1px solid #e8e4d8;
}

.filter-tabs {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  justify-content: center;
}

.filter-tab {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.8rem 1.5rem;
  border: 2px solid #e8e4d8;
  border-radius: 25px;
  background: #f8f6f0;
  color: #8b6914;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.3s ease;
}

.filter-tab:hover {
  border-color: #daa520;
  background: #f5f2e8;
}

.filter-tab.active {
  background: linear-gradient(135deg, #daa520 0%, #b8860b 100%);
  color: white;
  border-color: #daa520;
}

.tab-icon {
  font-size: 1.2rem;
}

.product-count {
  font-size: 0.9rem;
  opacity: 0.8;
}

/* Products Section */
.products-section {
  padding: 3rem 0;
}

.products-header {
  text-align: center;
  margin-bottom: 3rem;
}

.category-title {
  font-size: 2.2rem;
  color: #8b6914;
  margin-bottom: 1rem;
}

.category-description {
  font-size: 1.1rem;
  color: #6b5b3a;
  max-width: 600px;
  margin: 0 auto;
}

.products-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 2rem;
  margin-bottom: 3rem;
}

.product-card {
  background: white;
  border-radius: 15px;
  overflow: hidden;
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease;
  cursor: pointer;
  border: 2px solid #e8e4d8;
}

.product-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 15px 35px rgba(0, 0, 0, 0.15);
}

.product-card.hidden {
  display: none;
}

.product-showcase {
  height: 280px;
  background: linear-gradient(135deg, #f8f6f0 0%, #fff 100%);
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  border-bottom: 1px solid #e8e4d8;
}

.product-image-container {
  position: relative;
  width: 100%;
  height: 280px;
  overflow: hidden;
}

.product-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.3s ease;
}

.product-card:hover .product-image {
  transform: scale(1.05);
}

.fabric-badge {
  position: absolute;
  top: 15px;
  right: 15px;
  background: linear-gradient(135deg, #8b6914 0%, #daa520 100%);
  color: white;
  padding: 0.5rem 1rem;
  border-radius: 20px;
  font-size: 0.8rem;
  font-weight: bold;
  z-index: 2;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.2);
}

.product-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(135deg, rgba(139, 105, 20, 0.95), rgba(218, 165, 32, 0.95));
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: all 0.3s ease;
}

.product-card:hover .product-overlay {
  opacity: 1;
}

.overlay-content {
  text-align: center;
  color: white;
  padding: 2rem;
}

.overlay-content h3 {
  font-size: 1.3rem;
  margin-bottom: 1rem;
}

.overlay-content p {
  font-size: 0.95rem;
  margin-bottom: 1.5rem;
  line-height: 1.4;
}

.buy-btn {
  background: white;
  color: #8b6914;
  border: none;
  padding: 0.8rem 1.5rem;
  border-radius: 25px;
  font-weight: 600;
  cursor: pointer;
  display: flex;
  align-items: center;
  gap: 0.5rem;
  margin: 0 auto;
  transition: all 0.3s ease;
}

.buy-btn:hover {
  transform: scale(1.05);
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
}

.product-info {
  padding: 1.5rem;
}

.product-name {
  font-size: 1.2rem;
  color: #8b6914;
  margin-bottom: 0.5rem;
  font-weight: 600;
}

.product-type {
  color: #b8860b;
  font-size: 0.95rem;
  margin-bottom: 1rem;
}

.product-features {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.feature-tag {
  background: #f8f6f0;
  color: #8b6914;
  padding: 0.3rem 0.8rem;
  border-radius: 15px;
  font-size: 0.8rem;
  border: 1px solid #e8e4d8;
}

.view-more-section {
  text-align: center;
}

.view-more-btn {
  display: inline-block;
  background: linear-gradient(135deg, #daa520 0%, #b8860b 100%);
  color: white;
  padding: 1rem 2.5rem;
  border-radius: 25px;
  text-decoration: none;
  font-weight: 600;
  font-size: 1.1rem;
  transition: all 0.3s ease;
}

.view-more-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 20px rgba(218, 165, 32, 0.4);
}

/* Reviews Section */
.reviews-section {
  background: #f8f6f0;
  padding: 4rem 0;
}

.section-title {
  font-size: 2.5rem;
  color: #8b6914;
  text-align: center;
  margin-bottom: 3rem;
}

.reviews-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 2rem;
  margin-bottom: 3rem;
}

.review-card {
  background: white;
  padding: 2rem;
  border-radius: 15px;
  border: 1px solid #e8e4d8;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
}

.review-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  margin-bottom: 1rem;
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

.customer-name {
  color: #8b6914;
  margin-bottom: 0.3rem;
}

.review-rating {
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.rating-text {
  color: #b8860b;
  font-size: 0.9rem;
}

.review-date {
  color: #999;
  font-size: 0.9rem;
}

.review-text {
  color: #6b5b3a;
  line-height: 1.6;
  margin-bottom: 1rem;
  font-style: italic;
}

.review-product {
  display: flex;
  gap: 0.5rem;
  font-size: 0.9rem;
}

.product-label {
  color: #999;
}

.product-name {
  color: #8b6914;
  font-weight: 500;
}

.reviews-cta {
  text-align: center;
}

.reviews-cta p {
  color: #6b5b3a;
  margin-bottom: 1rem;
}

.etsy-reviews-btn {
  display: inline-block;
  background: white;
  color: #8b6914;
  padding: 0.8rem 2rem;
  border-radius: 25px;
  text-decoration: none;
  font-weight: 600;
  border: 2px solid #daa520;
  transition: all 0.3s ease;
}

.etsy-reviews-btn:hover {
  background: #daa520;
  color: white;
}

/* About Craft Section */
.about-craft {
  background: white;
  padding: 4rem 0;
}

.craft-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  align-items: center;
}

.craft-text h2 {
  font-size: 2.2rem;
  color: #8b6914;
  margin-bottom: 1.5rem;
}

.craft-text p {
  color: #6b5b3a;
  line-height: 1.7;
  margin-bottom: 1.5rem;
}

.craft-highlights {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.highlight {
  display: flex;
  align-items: center;
  gap: 1rem;
  padding: 1rem;
  background: #f8f6f0;
  border-radius: 10px;
  border: 1px solid #e8e4d8;
}

.highlight-icon {
  font-size: 2rem;
  flex-shrink: 0;
}

.highlight h4 {
  color: #8b6914;
  margin-bottom: 0.3rem;
}

.highlight p {
  color: #6b5b3a;
  font-size: 0.9rem;
  margin: 0;
}

.craft-showcase {
  background: #f8f6f0;
  padding: 3rem;
  border-radius: 15px;
  border: 2px solid #e8e4d8;
}

.traditional-patterns {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 2rem;
}

.pattern-item {
  text-align: center;
  padding: 1.5rem;
  background: white;
  border-radius: 10px;
  border: 1px solid #e8e4d8;
}

.pattern-icon {
  font-size: 3rem;
  margin-bottom: 1rem;
}

.pattern-item p {
  color: #8b6914;
  font-weight: 500;
  margin: 0;
}

/* Responsive Design */
@media (max-width: 768px) {
  .page-title {
    font-size: 2.2rem;
  }

  .filter-tabs {
    flex-direction: column;
    align-items: center;
  }

  .products-grid {
    grid-template-columns: 1fr;
  }

  .reviews-grid {
    grid-template-columns: 1fr;
  }

  .craft-content {
    grid-template-columns: 1fr;
    gap: 2rem;
  }

  .traditional-patterns {
    grid-template-columns: 1fr;
  }
}

@media (max-width: 600px) {
  .page-banner {
    height: 180px;
  }
  .page-banner-image {
    object-fit: contain;
  }
}
</style>
