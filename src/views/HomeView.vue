<script setup lang="ts">
import { ref, onMounted } from 'vue'

interface Image {
  url: string
}

interface Product {
  id: number
  name: string
  price: number
  image: Image
}

let products = ref<Product[]>([])

const fetchProducts = async () => {
  try {
    const res = await fetch('http://localhost:1337/api/products?populate=image')
    const data = await res.json()
    products.value = data.data
    console.log(products.value)
  } catch (error) {
    console.error(error)
  }
}

onMounted(() => {
  fetchProducts()
})
</script>

<template>
  <TitlePage title="HomePage" />
  <div class="products__grid">
    <div v-for="product in products" :key="product.id" class="product__card">
      <h2>{{ product.name }}</h2>
      <p>{{ product.price }}</p>
      <img
        :src="`http://localhost:1337${product.image?.url}`"
        alt="product image"
        width="100"
        height="100"
      />
    </div>
  </div>
</template>

<style scoped>
.products__grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}

.product__card {
  border: 1px solid #ccc;
  border-radius: 10px;
  padding: 20px;
}
</style>
