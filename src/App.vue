<script setup lang="ts">
import Header from "./components/header.vue";
import ReviewForm from "./components/ReviewForm.vue";
import ReviewGallery from "./components/ReviewGallery.vue";
</script>

<template>
  <Header />
  <div class="container">
    <ReviewForm />
    <ReviewGallery />
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: row;
  justify-content: center;
  gap: 20px;
}
</style>
