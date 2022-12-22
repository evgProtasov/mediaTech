<script setup>
import Header from './components/Header.vue'
import Products from './components/Products.vue'
</script>

<template>
  <div class="wrapper">
    <header>
      <Header />
    </header>
    <main>
      <Products />
    </main>
  </div>  
</template>

<style scoped>
  .wrapper {
    max-width: 1920px;
    margin: 0 auto;
    padding: 0 8px;
  }
  @media (max-width: 580px) {
    .wrapper {
      padding: 0;
    }
  }
</style>
