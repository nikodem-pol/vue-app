<script setup>
import { RouterLink, RouterView } from 'vue-router'
import NavigationBar from './components/NavigationBar.vue'
import Prototype from './components/Prototype.vue'
</script>

<template>
  <NavigationBar></NavigationBar>
  <div class="container">
    <RouterView :key="$route.path"></RouterView>
  </div>
</template>

<style scoped>
  .container {
  margin: 0 auto;
  max-width: 960px;
}
</style>
