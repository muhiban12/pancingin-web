<template>
  <div class="review-list">
    <div
      v-for="review in filteredReviews"
      :key="review.id"
      class="review-box mb-3"
    >
      <div class="d-flex align-items-center mb-1">
        <img :src="review.avatar" class="avatar me-2" />
        <strong>{{ review.name }}</strong>
        <span class="ms-auto text-warning">{{ review.rating }} ⭐</span>
      </div>
      <p class="mb-0">{{ review.comment }}</p>
    </div>

    <div v-if="filteredReviews.length === 0" class="text-center text-muted mt-4">
      Belum ada ulasan dengan filter ini 🎣
    </div>
  </div>
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
  reviews: Array,
  filter: Number
})

const filteredReviews = computed(() =>
  props.filter ? props.reviews.filter(r => r.rating === props.filter) : props.reviews
)
</script>

<style scoped>
.review-box {
  background: #ffffff;
  border: 1px solid #d6e6ff;
  border-radius: 10px;
  padding: 12px;
}
.avatar {
  width: 32px;
  height: 32px;
  border-radius: 50%;
  object-fit: cover;
}
</style>
