<script setup>
import Movie from "./components/movies.vue";
</script>

<template>
  <div class="app-container">
    <Suspense>
      <Movie />
    </Suspense>
  </div>
</template>

<style scoped>
</style>