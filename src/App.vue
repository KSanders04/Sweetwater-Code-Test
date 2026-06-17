<script setup lang="ts">
import ReviewForm from "./components/ReviewForm.vue";
import ReviewGallery from "./components/ReviewGallery.vue";
</script>

<template>
  <!-- <Header /> -->
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

@media (max-width: 1024px) {
  .container {
    padding: 16px;
  }
}

@media (max-width: 768px) {
  .container {
    flex-direction: column;
    align-items: stretch;
    gap: 16px;
    padding: 12px;
  }
}
</style>
