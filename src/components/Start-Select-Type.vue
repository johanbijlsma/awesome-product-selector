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
  <div class="container product-types">
    <RouterLink
      v-for="productType in productTypes"
      :key="productType.id"
      :class="productType.slug"
      :to="productType.url"
    >
      <span class="link">{{ productType.name }}</span></RouterLink
    >
  </div>
</template>

<style scoped>
.product-types {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  justify-content: space-between;
  flex-wrap: wrap;
  & > a {
    color: var(--print-secondary);
    text-rendering: optimizeLegibility;
    text-shadow:
      1px 1px var(--white),
      1px 1px var(--print-grey50);
    font-weight: 600;
    text-decoration: none;
    font-size: 34px;
    min-width: 300px;
    flex-grow: 1;
    width: 100%;
    height: 100%;
    aspect-ratio: 1/1;
    border-radius: 7px;
    display: flex;
    justify-content: center;
    align-items: center;
    transition: all 250ms ease-in-out;
  }
  & a.posters {
    background-image: url('../assets/posters-bg.jpg');
  }
  & a.flyers {
    background-image: url('../assets/flyers-bg.jpg');
  }
  & a.business-cards {
    background-image: url('../assets/businesscards-bg.jpg');
  }
  & a {
    transition: all 0.3s ease-in-out;
    background-size: cover;
    /* background-blend-mode: multiply; */
    border-radius: 7px;
    overflow: hidden;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
    position: relative;
    & span.link {
      position: relative;
      z-index: 5;
      display: block;
    }
  }
  & a::after {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
    z-index: 3;
  }
  & a:hover::after,
  & a:focus::after {
    background-color: var(--print-primary50);
  }
  & a:hover,
  & a:focus {
    background-blend-mode: lighten;
    background-size: 150%;
    scale: 1.01;
    transition: all 0.3s ease-in-out;
    cursor: pointer;
    & span.link {
      color: var(--black);
      text-shadow:
        1px 1px var(--print-grey50),
        1px 1px var(--white);
    }
  }
}

@media screen and (min-width: 768px) {
  .product-types {
    flex-direction: row;
    & > a {
      max-width: max-content;
    }
  }
}
</style>
