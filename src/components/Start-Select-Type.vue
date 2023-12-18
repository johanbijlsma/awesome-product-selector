<script setup lang="ts">
const productTypes = [
  {
    id: 1,
    name: 'Posters',
    slug: 'posters',
    url: '/product/posters'
  },
  {
    id: 2,
    name: 'Business Cards',
    slug: 'business-cards',
    url: '/product/business-cards'
  },
  {
    id: 3,
    name: 'Flyers',
    slug: 'flyers',
    url: '/product/flyers'
  }
]
</script>

<template>
  <ul class="container product-types">
    <li v-for="productType in productTypes" :key="productType.id" :class="productType.slug">
      <RouterLink :to="productType.url">
        <span class="link">{{ productType.name }}</span></RouterLink
      >
    </li>
  </ul>
</template>

<style scoped>
.product-types {
  display: flex;
  flex-direction: row;
  gap: 1rem;
  list-style: none;
  justify-content: space-between;
  & > li a {
    color: var(--print-secondary);
    text-rendering: optimizeLegibility;
    text-shadow:
      1px 1px var(--white),
      1px 1px var(--print-grey50);
    font-weight: 600;
    text-decoration: none;
    font-size: 34px;
    min-width: 300px;
    aspect-ratio: 1/1;
    border-radius: 7px;
    display: flex;
    justify-content: center;
    align-items: center;
    transition: all 0.3s ease-in-out;
    /* &:hover {
        color: var(--white);
        background-color: var(--print-secondary50);
    } */
  }
  & li.posters {
    background-image: url('../assets/posters-bg.jpg');
  }
  & li.flyers {
    background-image: url('../assets/flyers-bg.jpg');
  }
  & li.business-cards {
    background-image: url('../assets/businesscards-bg.jpg');
  }
  & li {
    /* background-image: linear-gradient(45deg, black, var(--print-secondary50)); */
    transition: all 0.3s ease-in-out;
    background-size: cover;
    background-blend-mode: multiply;
    border-radius: 7px;
    overflow: hidden;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
    position: relative;
    & span.link {
      position: relative;
      z-index: 5;
    }
  }
  & li::after {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
    z-index: 3;
  }
  & li:hover::after {
    background-color: rgba(0, 0, 0, 0.2);
  }
  & li:hover {
    background-blend-mode: hue;
    background-size: 150%;
    transition: all 0.3s ease-in-out;
    cursor: pointer;
  }
}
</style>
