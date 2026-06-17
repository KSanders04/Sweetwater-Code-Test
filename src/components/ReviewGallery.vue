<script setup lang="ts">
import { ref } from "vue";
import reviews from "../data/UX Team Code Review JSON.json";
import RatingSummary from "./RatingSummary.vue";
import Rates from "./Rates.vue";

const expanded = ref<number | null>(null);
function toggle(i: number) {
  expanded.value = expanded.value === i ? null : i;
}

// const myScore = ref(0);
</script>

<template>
  <section class="box">
    <RatingSummary />

    <div v-for="(review, i) in reviews" :key="i" class="reviewCard">
      <h2>{{ review.title }}</h2>
      <Rates :modelValue="review.starRating" />
      <p class="description">
        <span v-if="expanded === i">{{ review.description }}</span>
        <span v-else>{{
          review.description.length > 400
            ? review.description.slice(0, 400) + "..."
            : review.description
        }}</span>
      </p>
      <button
        v-if="review.description.length > 400"
        class="readMore"
        @click="toggle(i)"
      >
        {{ expanded === i ? "Show less" : "Read more" }}
      </button>
      <p class="user">by {{ review.user }}</p>
      <img :src="review.imageUrl" :alt="review.title" />
    </div>
  </section>
</template>

<style scoped>
.box {
  width: 50%;
  border-radius: 20px;
  font-family: Roboto;
}
.reviewCard {
  background-color: #f5f5f5;
  width: 60%;
  padding: 20px 40px;
  margin: 0 0 20px 0;
  border-radius: 8px;
}
.description {
  font-weight: 500;
}

.user {
  color: rgb(110, 110, 110);
}
.reviewCard img {
  height: auto;
  width: 75px;
  border-radius: 4px;
}

.readMore {
  background: none;
  border: none;
  color: #0671ba;
  cursor: pointer;
  padding: 4px 0 9px 0;
  font-weight: 600;
  display: block;
}

@media (max-width: 1024px) {
  .box {
    width: 100%;
  }

  .reviewCard {
    padding: 20px 24px;
    width: 93%;
  }
}

@media (max-width: 768px) {
  .reviewCard {
    padding: 16px;
  }

  .reviewCard img {
    width: 100%;
    max-width: 180px;
    height: auto;
  }

  .description {
    font-size: 15px;
  }
}
</style>
