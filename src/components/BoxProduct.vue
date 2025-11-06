<template>
  <div class="card shadow-sm p-3 mb-3">
    <div class="d-flex align-items-center mb-3">
      <img src="https://via.placeholder.com/70" class="rounded me-3" />
      <div class="flex-grow-1">
        <h6 class="fw-bold mb-1">Nama Produk</h6>
        <p class="text-muted mb-1 small">Tipe Produk</p>
        <p class="text-success fw-bold mb-0">Rp34.000</p>
      </div>
    </div>

    <div class="border-top pt-3">
      <div class="mb-2">
        <select class="form-select">
          <option>Reguler (Estimasi tiba 9–10 Nov)</option>
        </select>
      </div>

      <div class="form-check mb-2">
        <input class="form-check-input" type="checkbox" id="proteksi" />
        <label class="form-check-label small" for="proteksi">
          <iconify-icon icon="mdi:shield-check-outline" class="me-1 text-success"></iconify-icon>
          Proteksi Rusak (+Rp900)
        </label>
      </div>
    </div>
  </div>
</template>

<script setup></script>

<style scoped>
.card {
  border-radius: 12px;
}
img {
  width: 70px;
  height: 70px;
  object-fit: cover;
}
</style>
