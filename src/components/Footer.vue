<script setup lang="ts"></script>

<template>
  <footer>
    <div class="container">
      <p class="footer-title"><span class="awesome">Awesome</span> Product Selector</p>
      <nav class="footer-nav">
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/product/posters">Posters</RouterLink>
        <RouterLink to="/product/flyers">Flyers</RouterLink>
        <RouterLink to="/product/business-cards">business-cards</RouterLink>
      </nav>
    </div>
  </footer>
</template>

<style scoped>
footer {
  padding-block: 38px;
}
p.footer-title {
  font-size: 2.6rem;
  font-weight: 600;
  position: relative;
  display: inline-block;
  color: var(--white);
  & .awesome {
    font-weight: 800;
  }
}
nav.footer-nav {
  display: flex;
  flex-direction: column;

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
