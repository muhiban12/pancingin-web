<template>
  <div class="container my-4">
    <div class="row g-3">
      <!-- Kolom Kiri -->
      <div class="col-md-8">
        <AddressBox />
        <ProductBox />
      </div>

      <!-- Kolom Kanan -->
      <div class="col-md-4">
        <PaymentBox />
      </div>
    </div>
  </div>
</template>

<script setup>
import AddressBox from '@/components/BoxAlamat.vue'
import ProductBox from '@/components/BoxProduct.vue'
import PaymentBox from '@/components/PaymentBox.vue'
</script>

<style scoped>
body {
  background-color: #a8d4f7;
}
</style>
