<script setup lang="ts">
import { RouterView } from 'vue-router'
import Footer from './components/Footer.vue'
import Navigation from './components/Navigation.vue'
</script>

<template>
  <header>
    <Navigation></Navigation>
  </header>
  <main>
    <RouterView />
  </main>
  <Footer />
</template>

<style scoped>
header {
  line-height: 1.5;
}
</style>
