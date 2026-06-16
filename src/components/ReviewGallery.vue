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
      <Rates v-model="review.starRating" />
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
}
.reviewCard {
  background-color: #f5f5f5;
  width: 60%;
  padding: 20px 40px;
  margin: 0 0 20px 0;
  border-radius: 8px;
  font-family: Roboto;
}
.description {
  font-weight: 500;
  font-size: 16px;
}

.user {
  color: rgb(105, 105, 105);
}
.reviewCard img {
  height: 100px;
  width: 75px;
}

.readMore {
  background: none;
  border: none;
  color: #0671ba;
  cursor: pointer;
  padding: 0 0 9px 0;
  font-weight: 600;
}
</style>
