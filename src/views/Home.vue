<template>
  <div class="home">
    <!-- Hero Section -->
    <section class="hero">
      <div class="hero-overlay"></div>
      <div class="hero-content">
        <h1 class="hero-title">Welcome to Your Store</h1>
        <p class="hero-subtitle">Discover quality products at unbeatable prices</p>
        <router-link to="/products" class="cta-button">Shop Now</router-link>
      </div>
    </section>

    <!-- Categories Section -->
    <section class="categories">
      <div class="section-header">
        <h2>Shop by Category</h2>
        <p>Browse our wide selection of premium products</p>
      </div>
      <div class="categories-grid">
        <div class="category-card" v-for="category in categories" :key="category.id">
          <div class="category-icon">{{ category.icon }}</div>
          <h3>{{ category.name }}</h3>
          <p>{{ category.count }} items</p>
          <a href="#" class="category-link">Explore →</a>
        </div>
      </div>
    </section>

    <!-- Featured Products Section -->
    <section class="featured-products">
      <div class="section-header">
        <h2>Featured Products</h2>
        <p>Handpicked selections just for you</p>
      </div>
      <div class="products-grid">
        <ProductCard v-for="product in featuredProducts" :key="product.id" :product="product" />
      </div>
      <div class="view-all">
        <router-link to="/products" class="view-all-button">View All Products</router-link>
      </div>
    </section>

    <!-- Benefits Section -->
    <section class="benefits">
      <div class="benefits-grid">
        <div class="benefit-item">
          <div class="benefit-icon">🚚</div>
          <h3>Free Shipping</h3>
          <p>On orders over $50</p>
        </div>
        <div class="benefit-item">
          <div class="benefit-icon">💳</div>
          <h3>Secure Payment</h3>
          <p>100% secure transactions</p>
        </div>
        <div class="benefit-item">
          <div class="benefit-icon">↩️</div>
          <h3>Easy Returns</h3>
          <p>30-day return policy</p>
        </div>
        <div class="benefit-item">
          <div class="benefit-icon">⭐</div>
          <h3>Best Quality</h3>
          <p>Premium products guaranteed</p>
        </div>
      </div>
    </section>

    <!-- Testimonials Section -->
    <section class="testimonials">
      <div class="section-header">
        <h2>What Customers Say</h2>
        <p>Join thousands of satisfied customers</p>
      </div>
      <div class="testimonials-grid">
        <div class="testimonial-card" v-for="testimonial in testimonials" :key="testimonial.id">
          <div class="stars">⭐⭐⭐⭐⭐</div>
          <p class="testimonial-text">"{{ testimonial.text }}"</p>
          <p class="testimonial-author">— {{ testimonial.author }}</p>
        </div>
      </div>
    </section>

    <!-- Newsletter Section -->
    <section class="newsletter">
      <div class="newsletter-content">
        <h2>Subscribe to Our Newsletter</h2>
        <p>Get exclusive deals and updates delivered to your inbox</p>
        <form @submit.prevent="handleNewsletterSubmit" class="newsletter-form">
          <input 
            v-model="email" 
            type="email" 
            placeholder="Enter your email" 
            required
          />
          <button type="submit" class="newsletter-button">Subscribe</button>
        </form>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import ProductCard from '@/components/ProductCard.vue'

const email = ref('')
const featuredProducts = ref([])

const categories = [
  { id: 1, name: "Men's Clothing", count: 4, icon: '👕' },
  { id: 2, name: "Women's Fashion", count: 6, icon: '👗' },
  { id: 3, name: "Jewelry", count: 4, icon: '💎' },
  { id: 4, name: "Electronics", count: 16, icon: '📱' }
]

const testimonials = [
  {
    id: 1,
    text: "Amazing quality products and fast shipping. Highly recommend!",
    author: "Sarah Johnson"
  },
  {
    id: 2,
    text: "Great prices and excellent customer service. Will shop again!",
    author: "Michael Chen"
  },
  {
    id: 3,
    text: "Best online shopping experience I've had. Thank you!",
    author: "Emma Wilson"
  }
]

const fetchFeaturedProducts = async () => {
  try {
    const response = await fetch('https://fakestoreapi.com/products?limit=4')
    const json = await response.json()
    featuredProducts.value = json
  } catch (error) {
    console.error('Error fetching featured products:', error)
  }
}

const handleNewsletterSubmit = () => {
  alert(`Thank you for subscribing with ${email.value}!`)
  email.value = ''
}

fetchFeaturedProducts()
</script>

<style scoped>
.home {
  width: 100%;
}

/* Hero Section */
.hero {
  position: relative;
  height: 600px;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  margin-bottom: 4rem;
}

.hero-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1200 600"><defs><pattern id="grid" width="40" height="40" patternUnits="userSpaceOnUse"><path d="M 40 0 L 0 0 0 40" fill="none" stroke="rgba(255,255,255,0.1)" stroke-width="1"/></pattern></defs><rect width="1200" height="600" fill="url(%23grid)"/></svg>');
  opacity: 0.5;
}

.hero-content {
  position: relative;
  z-index: 2;
  text-align: center;
  color: white;
  max-width: 600px;
}

.hero-title {
  font-size: 3rem;
  font-weight: 700;
  margin: 0 0 1rem 0;
  line-height: 1.2;
}

.hero-subtitle {
  font-size: 1.3rem;
  margin: 0 0 2rem 0;
  opacity: 0.95;
}

.cta-button {
  display: inline-block;
  background-color: #42b983;
  color: white;
  padding: 1rem 2.5rem;
  border-radius: 50px;
  text-decoration: none;
  font-weight: 600;
  transition: all 0.3s ease;
  box-shadow: 0 4px 15px rgba(66, 185, 131, 0.4);
}

.cta-button:hover {
  background-color: #359268;
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(66, 185, 131, 0.6);
}

/* Section Headers */
.section-header {
  text-align: center;
  margin-bottom: 3rem;
}

.section-header h2 {
  font-size: 2.2rem;
  color: #2c3e50;
  margin: 0 0 0.5rem 0;
  font-weight: 700;
}

.section-header p {
  font-size: 1.1rem;
  color: #7f8c8d;
  margin: 0;
}

/* Categories Section */
.categories {
  padding: 3rem 2rem;
  background: white;
  margin-bottom: 2rem;
}

.categories-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 2rem;
  max-width: 1200px;
  margin: 0 auto;
}

.category-card {
  background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
  padding: 2rem;
  border-radius: 12px;
  text-align: center;
  transition: all 0.3s ease;
  cursor: pointer;
}

.category-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.1);
}

.category-icon {
  font-size: 3rem;
  margin-bottom: 1rem;
}

.category-card h3 {
  color: #2c3e50;
  margin: 1rem 0;
  font-size: 1.1rem;
}

.category-card p {
  color: #7f8c8d;
  margin: 0 0 1rem 0;
  font-size: 0.9rem;
}

.category-link {
  color: #42b983;
  text-decoration: none;
  font-weight: 600;
  transition: color 0.3s ease;
}

.category-link:hover {
  color: #359268;
}

/* Featured Products Section */
.featured-products {
  padding: 4rem 2rem;
  background: white;
  margin-bottom: 2rem;
}

.products-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 2rem;
  max-width: 1200px;
  margin: 0 auto 3rem;
}

.view-all {
  text-align: center;
}

.view-all-button {
  display: inline-block;
  background-color: #42b983;
  color: white;
  padding: 0.75rem 2rem;
  border-radius: 50px;
  text-decoration: none;
  font-weight: 600;
  transition: all 0.3s ease;
}

.view-all-button:hover {
  background-color: #359268;
  transform: translateY(-2px);
}

/* Benefits Section */
.benefits {
  padding: 3rem 2rem;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  margin-bottom: 2rem;
}

.benefits-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 2rem;
  max-width: 1200px;
  margin: 0 auto;
}

.benefit-item {
  text-align: center;
  color: white;
}

.benefit-icon {
  font-size: 2.5rem;
  margin-bottom: 1rem;
}

.benefit-item h3 {
  margin: 1rem 0 0.5rem 0;
  font-size: 1.1rem;
}

.benefit-item p {
  margin: 0;
  opacity: 0.9;
}

/* Testimonials Section */
.testimonials {
  padding: 4rem 2rem;
  background: white;
  margin-bottom: 2rem;
}

.testimonials-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
  max-width: 1200px;
  margin: 0 auto;
}

.testimonial-card {
  background: #f5f7fa;
  padding: 2rem;
  border-radius: 12px;
  border-left: 4px solid #42b983;
}

.stars {
  font-size: 1rem;
  margin-bottom: 1rem;
}

.testimonial-text {
  color: #2c3e50;
  font-style: italic;
  margin: 1rem 0;
  line-height: 1.6;
}

.testimonial-author {
  color: #42b983;
  font-weight: 600;
  margin: 0;
}

/* Newsletter Section */
.newsletter {
  background: linear-gradient(135deg, #42b983 0%, #359268 100%);
  padding: 4rem 2rem;
  color: white;
}

.newsletter-content {
  max-width: 600px;
  margin: 0 auto;
  text-align: center;
}

.newsletter-content h2 {
  font-size: 2rem;
  margin: 0 0 1rem 0;
}

.newsletter-content p {
  font-size: 1.1rem;
  margin: 0 0 2rem 0;
  opacity: 0.95;
}

.newsletter-form {
  display: flex;
  gap: 1rem;
}

.newsletter-form input {
  flex: 1;
  padding: 0.75rem 1.5rem;
  border: none;
  border-radius: 50px;
  font-size: 1rem;
}

.newsletter-button {
  padding: 0.75rem 2rem;
  background-color: #2c3e50;
  color: white;
  border: none;
  border-radius: 50px;
  font-weight: 600;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.newsletter-button:hover {
  background-color: #1a252f;
}

/* Responsive Design */
@media (max-width: 768px) {
  .hero-title {
    font-size: 2rem;
  }

  .hero-subtitle {
    font-size: 1rem;
  }

  .section-header h2 {
    font-size: 1.5rem;
  }

  .products-grid,
  .categories-grid {
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 1rem;
  }

  .testimonials-grid {
    grid-template-columns: 1fr;
  }

  .newsletter-form {
    flex-direction: column;
  }
}
</style>
