<template>
  <div class="star-rating">
    <span
      v-for="star in maxStars"
      :key="star"
      class="star"
      :class="{ filled: star <= (hoverValue || rating) }"
      @click="setRating(star)"
      @mouseover="hoverValue = star"
      @mouseleave="hoverValue = 0"
    >
      ★
    </span>
  </div>
</template>

<script setup>
import { ref } from "vue";

const props = defineProps({
  maxStars: { type: Number, default: 5 },
  modelValue: { type: Number, default: 0 },
});

const emit = defineEmits(["update:modelValue"]);
const rating = ref(props.modelValue);
const hoverValue = ref(0);

const setRating = (star) => {
  rating.value = star;
  emit("update:modelValue", star);
};
</script>

<style scoped>
.star-rating {
  display: flex;
  gap: 4px;
}
.star {
  font-size: 24px;
  color: #d1d5db;
  cursor: pointer;
  transition: color 0.2s;
}
.star.filled {
  color: #fbbf24;
}
</style>
