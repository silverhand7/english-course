<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <div class="container h-100vh">
    <RouterView />
  </div>
</template>


<style>
  body {
    font-family: 'Poppins', sans-serif!important;
  }
  .bg-blurry {
    background: linear-gradient(110.72deg, rgba(255, 255, 255, 0.36) 1.21%, rgba(196, 196, 196, 0.06) 100%);
  }
  .h-100vh {
    height: 100vh;
  }
</style>
