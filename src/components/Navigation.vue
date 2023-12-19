<script setup lang="ts">
import { RouterLink } from 'vue-router'
</script>

<template>
  <nav class="container navigation">
    <RouterLink to="/"
      ><h1><span class="awesome">Awesome</span> Product Selector</h1></RouterLink
    >
    <RouterLink to="/product/posters">Posters</RouterLink>
    <RouterLink to="/product/business-cards">Business-cards</RouterLink>
    <RouterLink to="/product/flyers">Flyers</RouterLink>
  </nav>
</template>

<style scoped>
h1 {
  /* font-size:  3rem; */
  font-size: clamp(1.5rem, 3vw, 3.5rem);
  font-weight: 600;
  position: relative;
  display: block;
  & .awesome {
    font-weight: 800;
  }
}

.navigation {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  margin: 0 2rem;
  flex-wrap: wrap;
  flex-direction: column;
  & > a {
    color: var(--white);
    font-weight: 600;
    text-decoration: none;
    font-size: 1.375rem;
    padding: 0.5rem 1rem;
    border-radius: 7px;
    transition: all 0.3s ease-in-out;

    &.router-link-exact-active {
      color: var(--print-tertiary);
      background-color: var(--white) / 90%;
    }
  }
  & > a {
    flex-grow: 0;
  }
  & > a:has(> h1) {
    flex-grow: 1;
    width: 100%;
  }
}

@media screen and (min-width: 768px) {
  .navigation a:has(:not(h1)) {
    flex-grow: 0;
  }
  .navigation a:has(> h1) {
    width: fit-content !important;
    flex-grow: 0;
  }
  .navigation {
    flex-direction: row;
    align-items: center;
  }
}
</style>
