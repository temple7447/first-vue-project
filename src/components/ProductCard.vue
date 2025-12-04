<script setup>
defineProps({
  product: {
    type: Object,
    required: true
  }
})


const getStarRating = (rate) => {
  return Math.round(rate)
}
</script>

<template>

  <div class="product-card">
    <div class="product-image">
      <img :src="product.image" :alt="product.title" />
    </div>

    <div class="product-info">
      <span class="category">{{ product.category }}</span>
      
      <h3 class="product-title">{{ product.title }}</h3>

      <p class="product-description">{{ product.description }}</p>

      <div class="rating">
        <div class="stars">
          <span v-for="i in 5" :key="i" class="star" :class="{ filled: i <= getStarRating(product.rating.rate) }">★</span>
        </div>
        <span class="rating-text">{{ product.rating.rate }} ({{ product.rating.count }} reviews)</span>
      </div>

      <div class="product-footer">
        <span class="price">${{ product.price }}</span>
        <button class="add-to-cart">Add to Cart</button>
      </div>
    </div>
  </div>
</template>

<style scoped>
.product-card {
  background: white;
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  display: flex;
  flex-direction: column;
  height: 100%;
}

.product-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.15);
}

.product-image {
  width: 100%;
  aspect-ratio: 1;
  overflow: hidden;
  background-color: #f5f5f5;
  display: flex;
  align-items: center;
  justify-content: center;
}

.product-image img {
  width: 100%;
  height: 100%;
  object-fit: contain;
  padding: 1rem;
}

.product-info {
  padding: 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
  flex: 1;
}

.category {
  font-size: 0.75rem;
  font-weight: 600;
  color: #42b983;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.product-title {
  font-size: 1rem;
  font-weight: 600;
  color: #2c3e50;
  line-height: 1.3;
  margin: 0;
}

.product-description {
  font-size: 0.875rem;
  color: #7f8c8d;
  line-height: 1.4;
  margin: 0;
  flex: 1;
}

.rating {
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.stars {
  display: flex;
  gap: 0.25rem;
}

.star {
  font-size: 1rem;
  color: #ddd;
  transition: color 0.2s ease;
}

.star.filled {
  color: #ffc107;
}

.rating-text {
  font-size: 0.875rem;
  color: #95a5a6;
}

.product-footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-top: 1rem;
  border-top: 1px solid #ecf0f1;
}

.price {
  font-size: 1.5rem;
  font-weight: 700;
  color: #42b983;
}

.add-to-cart {
  padding: 0.75rem 1.5rem;
  background-color: #42b983;
  color: white;
  border: none;
  border-radius: 4px;
  font-weight: 600;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.add-to-cart:hover {
  background-color: #359268;
}

@media (max-width: 768px) {
  .product-info {
    padding: 1rem;
    gap: 0.5rem;
  }

  .product-title {
    font-size: 0.95rem;
  }

  .price {
    font-size: 1.25rem;
  }
}
</style>
