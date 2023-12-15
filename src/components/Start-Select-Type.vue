<script setup lang="ts">
const productTypes = [
  {
    id: 1,
    name: 'Posters',
    url: '/product/posters'
  },
  {
    id: 2,
    name: 'Business Cards',
    url: '/product/business-cards'
  },
  {
    id: 3,
    name: 'Flyers',
    url: '/product/flyers'
  }
]
</script>

<template>
  <h2>Welcome to the Awesome Product Selector 👋</h2>
  <ul>
    <li v-for="productType in productTypes" :key="productType.id">
      {{ productType.name }}
    </li>
  </ul>
</template>
