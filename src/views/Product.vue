<script setup>
import ProductCard from '@/components/ProductCard.vue'
import { ref, onMounted } from 'vue'



const datas = ref([])


const fetchDate = async () => {
    try {
        const response = await fetch('https://fakestoreapi.com/products')
        const json = await response.json()
        console.log(json)
        datas.value = json
    } catch (error) {
        console.error('Error fetching data:', error)
    }
}

onMounted(() => {
    fetchDate()
})

</script>

<template>
    <div class="products-container">
        <ProductCard v-for="data in datas" :key="data.id" :product="data" />
    </div>
</template>

<style scoped>
.products-container {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 2rem;
  padding: 1rem 0;
}

@media (max-width: 768px) {
  .products-container {
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 1rem;
  }
}
</style>