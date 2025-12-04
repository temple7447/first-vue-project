<template>
  <div class="about">
    <!-- Hero Section -->
    <section class="hero">
      <div class="hero-content">
        <h1>About Our Store</h1>
        <p class="hero-subtitle">Your trusted destination for quality products at great prices</p>
      </div>
    </section>

    <!-- About Content -->
    <section class="about-content">
      <div class="content-wrapper">
        <div class="about-text">
          <h2>Who We Are</h2>
          <p>
            We are committed to providing customers with an exceptional shopping experience. 
            Our carefully curated selection of products spans multiple categories, from fashion 
            to electronics, ensuring you'll find exactly what you're looking for.
          </p>
          <p>
            With a focus on quality, affordability, and customer satisfaction, we've built 
            a community of loyal shoppers who trust us for their everyday needs.
          </p>
        </div>

        <!-- Features -->
        <div class="features">
          <h2>Why Choose Us</h2>
          <div class="features-grid">
            <div class="feature-card">
              <div class="feature-icon">📦</div>
              <h3>Fast Shipping</h3>
              <p>Quick and reliable delivery to your doorstep</p>
            </div>
            <div class="feature-card">
              <div class="feature-icon">💰</div>
              <h3>Best Prices</h3>
              <p>Competitive pricing on all our products</p>
            </div>
            <div class="feature-card">
              <div class="feature-icon">✅</div>
              <h3>Quality Assured</h3>
              <p>All products verified for quality</p>
            </div>
            <div class="feature-card">
              <div class="feature-icon">🛡️</div>
              <h3>Secure Shopping</h3>
              <p>Protected transactions and data security</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- CTA Section -->
    <section class="cta-section">
      <h2>Ready to Shop?</h2>
      <p>Explore our wide range of products and find what you love</p>
      <router-link to="/" class="cta-button">Start Shopping</router-link>
    </section>
  </div>
</template>

<script setup>
</script>

<style scoped>
.about {
  width: 100%;
}

/* Hero Section */
.hero {
  background: linear-gradient(135deg, #42b983 0%, #359268 100%);
  color: white;
  padding: 4rem 2rem;
  text-align: center;
  margin-bottom: 3rem;
}

.hero-content h1 {
  font-size: 2.5rem;
  margin: 0;
  font-weight: 700;
}

.hero-subtitle {
  font-size: 1.2rem;
  margin: 1rem 0 0 0;
  opacity: 0.95;
}

/* About Content */
.about-content {
  padding: 2rem 0;
}

.content-wrapper {
  max-width: 1000px;
  margin: 0 auto;
  padding: 0 2rem;
}

.about-text {
  margin-bottom: 3rem;
}

.about-text h2 {
  font-size: 2rem;
  color: #2c3e50;
  margin-bottom: 1rem;
}

.about-text p {
  font-size: 1rem;
  line-height: 1.8;
  color: #555;
  margin-bottom: 1rem;
}

/* Features Section */
.features h2 {
  font-size: 2rem;
  color: #2c3e50;
  margin-bottom: 2rem;
  text-align: center;
}

.features-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 1.5rem;
  margin-bottom: 3rem;
}

.feature-card {
  background: white;
  border: 1px solid #ecf0f1;
  border-radius: 8px;
  padding: 2rem;
  text-align: center;
  transition: all 0.3s ease;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
}

.feature-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  border-color: #42b983;
}

.feature-icon {
  font-size: 2.5rem;
  margin-bottom: 1rem;
}

.feature-card h3 {
  color: #2c3e50;
  margin: 1rem 0;
  font-size: 1.1rem;
}

.feature-card p {
  color: #7f8c8d;
  font-size: 0.9rem;
  line-height: 1.6;
  margin: 0;
}

/* CTA Section */
.cta-section {
  background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
  padding: 3rem 2rem;
  text-align: center;
  margin-top: 3rem;
}

.cta-section h2 {
  font-size: 2rem;
  color: #2c3e50;
  margin-bottom: 0.5rem;
}

.cta-section p {
  font-size: 1.1rem;
  color: #555;
  margin-bottom: 2rem;
}

.cta-button {
  display: inline-block;
  background-color: #42b983;
  color: white;
  padding: 1rem 2rem;
  border-radius: 4px;
  text-decoration: none;
  font-weight: 600;
  transition: background-color 0.3s ease;
}

.cta-button:hover {
  background-color: #359268;
}

/* Responsive Design */
@media (max-width: 768px) {
  .hero-content h1 {
    font-size: 1.8rem;
  }

  .hero-subtitle {
    font-size: 1rem;
  }

  .about-text h2,
  .features h2,
  .cta-section h2 {
    font-size: 1.5rem;
  }

  .features-grid {
    grid-template-columns: 1fr;
    gap: 1rem;
  }

  .cta-button {
    padding: 0.75rem 1.5rem;
    font-size: 0.95rem;
  }
}
</style>
