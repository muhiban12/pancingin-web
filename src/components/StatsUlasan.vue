<template>
  <div class="review-stats">
    <h5 class="fw-bold mb-3">Statistik Ulasan</h5>
    <p class="fs-5">⭐ {{ average }}/5.0 dari {{ total }} ulasan</p>

    <div v-for="star in [5,4,3,2,1]" :key="star" class="d-flex align-items-center mb-2">
      <span class="me-2">{{ star }} ⭐</span>
      <div class="progress flex-grow-1 me-2" style="height: 8px;">
        <div
          class="progress-bar bg-primary"
          :style="{ width: getPercent(star) + '%' }"
        ></div>
      </div>
      <span>{{ ratings[star] || 0 }}</span>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  ratings: Object, // { 5: 12, 4: 3, ... }
  total: Number,
  average: Number
})

function getPercent(star) {
  return props.total ? (props.ratings[star] || 0) / props.total * 100 : 0
}
</script>

<style scoped>
.review-stats {
  background: #f0faff;
  padding: 20px;
  border-radius: 12px;
  border: 1px solid #d0eaff;
}
</style>
