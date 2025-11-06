<template>
  <div class="card shadow-sm p-3">
    <h5 class="mb-3 d-flex align-items-center">
      <iconify-icon icon="mdi:credit-card-outline" class="me-2 text-primary"></iconify-icon>
      Metode Pembayaran
    </h5>

    <div class="list-group mb-3">
      <label class="list-group-item">
        <input type="radio" name="pay" class="form-check-input me-2" checked />
        BCA Virtual Account
      </label>
      <label class="list-group-item">
        <input type="radio" name="pay" class="form-check-input me-2" />
        Mandiri Virtual Account
      </label>
      <label class="list-group-item">
        <input type="radio" name="pay" class="form-check-input me-2" />
        Gopay / OVO / Dana
      </label>
    </div>

    <div class="d-flex justify-content-between mb-2">
      <span>Total Barang</span>
      <span>Rp12.000</span>
    </div>
    <div class="d-flex justify-content-between mb-3">
      <span>Ongkos Kirim</span>
      <span>Rp15.000</span>
    </div>

    <div class="d-flex justify-content-between fw-bold fs-6 border-top pt-2 mb-3">
      <span>Total Tagihan</span>
      <span class="text-success">Rp27.000</span>
    </div>

    <button class="btn btn-success w-100 d-flex align-items-center justify-content-center">
      <iconify-icon icon="mdi:check-circle-outline" class="me-2"></iconify-icon>
      Bayar Sekarang
    </button>
  </div>
</template>

<script setup></script>

<style scoped>
.card {
  border-radius: 12px;
}
</style>
