<script setup lang="ts">
import { RouterLink } from 'vue-router'
</script>

<template>
  <nav class="container navigation">
    <RouterLink to="/"
      ><h1><span class="awesome">Awesome</span> Product Selector</h1></RouterLink
    >
    <RouterLink to="/product/posters">Posters</RouterLink>
    <RouterLink to="/product/flyers">Flyers</RouterLink>
    <RouterLink to="/product/business-cards">Business-cards</RouterLink>
  </nav>
</template>

<style scoped>
h1 {
  font-size: 2.6rem;
  font-weight: 600;
  position: relative;
  display: inline-block;
  & .awesome {
    font-weight: 800;
  }
}

.navigation {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 0 2rem;
  & > a {
    color: var(--white);
    font-weight: 600;
    text-decoration: none;
    font-size: 22px;
    &.router-link-exact-active {
      color: var(--print-secondary);
    }
  }
}
</style>
