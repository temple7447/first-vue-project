<script setup>
import { ref } from 'vue'

const currentYear = ref(new Date().getFullYear())
</script>

<template>
  <footer class="footer">
    <div class="footer-content">
      <!-- Company Info -->
      <div class="footer-section">
        <h3 class="footer-title">About Us</h3>
        <p class="footer-description">
          Your trusted online store for quality products. We offer a wide selection 
          of items across multiple categories at competitive prices.
        </p>
        <div class="social-links">
          <a href="#" class="social-link" title="Facebook">f</a>
          <a href="#" class="social-link" title="Twitter">𝕏</a>
          <a href="#" class="social-link" title="Instagram">📷</a>
          <a href="#" class="social-link" title="LinkedIn">in</a>
        </div>
      </div>

      <!-- Quick Links -->
      <div class="footer-section">
        <h3 class="footer-title">Quick Links</h3>
        <ul class="footer-links">
          <li><router-link to="/">Home</router-link></li>
          <li><router-link to="/about">About</router-link></li>
          <li><a href="#">Products</a></li>
          <li><a href="#">Contact</a></li>
        </ul>
      </div>

      <!-- Customer Service -->
      <div class="footer-section">
        <h3 class="footer-title">Customer Service</h3>
        <ul class="footer-links">
          <li><a href="#">Contact Us</a></li>
          <li><a href="#">Shipping Info</a></li>
          <li><a href="#">Returns</a></li>
          <li><a href="#">FAQ</a></li>
        </ul>
      </div>

      <!-- Contact Info -->
      <div class="footer-section">
        <h3 class="footer-title">Contact</h3>
        <div class="contact-info">
          <p>📧 Email: info@store.com</p>
          <p>📞 Phone: +1 (555) 123-4567</p>
          <p>📍 Address: 123 Main St, City, State 12345</p>
        </div>
      </div>
    </div>

    <!-- Footer Bottom -->
    <div class="footer-bottom">
      <p>&copy; {{ currentYear }} Your Store. All rights reserved.</p>
      <div class="footer-bottom-links">
        <a href="#">Privacy Policy</a>
        <span class="divider">|</span>
        <a href="#">Terms of Service</a>
        <span class="divider">|</span>
        <a href="#">Cookie Policy</a>
      </div>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  background-color: #2c3e50;
  color: #ecf0f1;
  padding: 3rem 2rem 0;
  margin-top: 4rem;
}

.footer-content {
  max-width: 1200px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
  padding-bottom: 2rem;
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
}

.footer-section {
  flex: 1;
}

.footer-title {
  font-size: 1.1rem;
  font-weight: 600;
  color: #42b983;
  margin-bottom: 1rem;
}

.footer-description {
  font-size: 0.9rem;
  line-height: 1.6;
  color: #bdc3c7;
  margin-bottom: 1.5rem;
}

.social-links {
  display: flex;
  gap: 1rem;
}

.social-link {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background-color: #42b983;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  text-decoration: none;
  font-weight: 600;
  transition: all 0.3s ease;
}

.social-link:hover {
  background-color: #359268;
  transform: translateY(-3px);
}

.footer-links {
  list-style: none;
  padding: 0;
  margin: 0;
}

.footer-links li {
  margin-bottom: 0.75rem;
}

.footer-links a {
  color: #bdc3c7;
  text-decoration: none;
  transition: color 0.3s ease;
  font-size: 0.9rem;
}

.footer-links a:hover {
  color: #42b983;
}

.contact-info {
  font-size: 0.9rem;
  color: #bdc3c7;
  line-height: 1.8;
}

.contact-info p {
  margin: 0.5rem 0;
}

/* Footer Bottom */
.footer-bottom {
  background-color: rgba(0, 0, 0, 0.2);
  padding: 1.5rem 2rem;
  text-align: center;
  color: #95a5a6;
  font-size: 0.85rem;
}

.footer-bottom p {
  margin: 0 0 1rem 0;
}

.footer-bottom-links {
  display: flex;
  justify-content: center;
  gap: 0.5rem;
  flex-wrap: wrap;
}

.footer-bottom-links a {
  color: #95a5a6;
  text-decoration: none;
  transition: color 0.3s ease;
}

.footer-bottom-links a:hover {
  color: #42b983;
}

.divider {
  color: #555;
}

/* Responsive Design */
@media (max-width: 768px) {
  .footer {
    padding: 2rem 1rem 0;
  }

  .footer-content {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }

  .footer-bottom {
    padding: 1rem;
  }

  .footer-bottom-links {
    gap: 0.25rem;
  }

  .divider {
    display: none;
  }

  .footer-bottom-links a {
    display: block;
    margin: 0.25rem 0;
  }
}
</style>
