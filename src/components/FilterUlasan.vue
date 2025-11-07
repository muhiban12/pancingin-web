<template>
  <div class="review-filter mb-3">
    <div class="text-md fw-bold">Filter Ulasan</div>
    <div class="mt-2 d-flex gap-2 flex-wrap">
      <button
        v-for="star in [5, 4, 3, 2, 1]"
        :key="star"
        :class="['btn btn-outline-primary', selected === star ? 'active' : '']"
        @click="emit('update:filter', star)"
      >
        {{ star }}⭐
      </button>
    </div>
  </div>
</template>

<script setup>
const { selected } = defineProps({ selected: Number })
const emit = defineEmits(['update:filter'])
</script>

<style scoped>
.review-filter .btn.active {
  background-color: #0099cc;
  color: white;
  border-color: #0099cc;
}
</style>
