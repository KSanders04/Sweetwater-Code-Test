<script setup lang="ts">
import { computed } from "vue";
import reviews from "../data/UX Team Code Review JSON.json";

type StarRow = {
  stars: number;
  count: number;
  percent: number;
};

const totalReviews = reviews.length;

const starRows = computed<StarRow[]>(() => {
  return [5, 4, 3, 2, 1].map((stars) => {
    const count = reviews.filter(
      (review) => review.starRating === stars,
    ).length;
    const percent = totalReviews > 0 ? (count / totalReviews) * 100 : 0;
    return { stars, count, percent };
  });
});

const totalStars = computed<number>(() => {
  return reviews.reduce((sum, review) => {
    const value =
      typeof review.starRating === "number"
        ? review.starRating
        : Number(review.starRating) || 0;
    return sum + value;
  }, 0);
});

const averageStars = computed<number>(() => {
  return totalReviews > 0 ? totalStars.value / totalReviews : 0;
});

const averageStarsFormatted = computed<string>(() => {
  return averageStars.value.toFixed(2);
});
</script>

<template>
  <section class="summaryCard">
    <h2>Rating Summary</h2>
    <p class="meta">
      {{ totalReviews }} reviews • Overall {{ averageStarsFormatted }} Stars
    </p>
    <div v-for="row in starRows" :key="row.stars" class="barRow">
      <span class="label">{{ row.stars }} star</span>
      <div
        class="track"
        role="img"
        :aria-label="`${row.stars} star ratings: ${row.count}`"
      >
        <div class="fill" :style="{ width: `${row.percent}%` }"></div>
      </div>
      <span class="count">{{ row.count }}</span>
    </div>
  </section>
</template>

<style scoped>
.summaryCard {
  background: #f5f5f5;
  border-radius: 8px;
  padding: 24px;
  box-sizing: border-box;
  font-family: Roboto;
  margin: 0 0 20px;
}
h2 {
  margin: 0;
}
.meta {
  margin: 8px 0 20px;
  color: #4f4f4f;
}
.barRow {
  display: grid;
  grid-template-columns: 70px 1fr 24px;
  align-items: center;
  gap: 12px;
  margin-bottom: 12px;
}
.label,
.count {
  font-weight: 600;
}
.track {
  height: 14px;
  background: #d6d6d6;
  border-radius: 999px;
  overflow: hidden;
}
.fill {
  height: 100%;
  background: #3573e7;
  border-radius: 999px;
  transition: width 250ms ease;
}

@media (max-width: 768px) {
  .summaryCard {
    padding: 16px;
  }

  .barRow {
    grid-template-columns: 60px 1fr 22px;
    gap: 8px;
  }

  .meta {
    margin-bottom: 16px;
  }
}
</style>
