<template>
  <div class="product-box container my-4">
    <div class="row">
      <!-- Gambar Produk -->
      <div class="col-md-5 mb-4">
        <div class="main-image mb-3">
          <img :src="selectedImage" class="img-fluid rounded shadow-sm" />
        </div>
        <div class="thumbs d-flex gap-2 flex-wrap">
          <img
            v-for="(img, index) in currentType?.images || product.images"
            :key="index"
            :src="img"
            class="thumb-img"
            :class="{ active: selectedImage === img }"
            @click="emit('update:selectedImage', img)"
          />
        </div>
      </div>

      <!-- Info Produk -->
      <div class="col-md-7">
        <h4 class="fw-bold mb-1">{{ product.name }}</h4>
        <p class="text-muted small">Terjual 1rb+ • {{ product.rating }} (1rb+)</p>
        <h5 class="text-success fw-bold mb-3">Rp{{ product.price.toLocaleString() }}</h5>

        <!-- Pilihan Tipe Produk -->
        <div v-if="product.types?.length" class="product-type-selector mb-4">
          <h6 class="fw-semibold mb-2">Type Produk:</h6>
          <div class="d-flex gap-2 flex-wrap">
            <button
              v-for="(type, index) in product.types"
              :key="index"
              class="btn"
              :class="selectedType === type.name ? 'btn-success' : 'btn-outline-success'"
              @click="selectType(type)"
            >
              {{ type.name }}
            </button>
          </div>
        </div>

        <!-- Tab Tombol -->
        <div class="btn-group mb-3 d-flex flex-wrap">
          <button
            class="btn flex-fill"
            :class="activeTab === 'deskripsi' ? 'btn-primary' : 'btn-outline-primary'"
            @click="activeTab = 'deskripsi'"
          >
            📝 Deskripsi Produk
          </button>
          <button
            class="btn flex-fill"
            :class="activeTab === 'detail' ? 'btn-primary' : 'btn-outline-primary'"
            @click="activeTab = 'detail'"
          >
            📦 Detail Produk
          </button>
        </div>

        <!-- Konten Tab -->
        <div v-if="activeTab === 'deskripsi'" class="tab-content">
          <p class="fw-semibold mb-1">Deskripsi Produk:</p>
          <p class="mt-2">{{ product.description }}</p>
        </div>

        <div v-else class="tab-content">
          <p class="fw-semibold mb-1">Fitur Produk:</p>
          <ul class="desc-list">
            <li>Bahan ringan & tahan karat</li>
            <li>Gagang anti slip nyaman digenggam</li>
            <li>Cocok untuk air tawar maupun laut</li>
          </ul>

          <p class="fw-semibold mt-3 mb-1">Spesifikasi Produk:</p>
          <ul>
            <li>Panjang: ±2,1 meter</li>
            <li>Material: Carbon fiber, aluminium</li>
            <li>Warna: Hitam</li>
          </ul>
        </div>

        <!-- Tombol Aksi -->
        <div class="d-flex gap-3 flex-wrap mt-4">
          <button class="btn btn-outline-primary w-100">
            <iconify-icon icon="mdi:cart-plus" class="me-2" />
            + Keranjang
          </button>
          <button class="btn btn-success w-100" @click="goToCheckout">
            <iconify-icon icon="mdi:fishing" class="me-2" />
            Beli Langsung
          </button>
        </div>

        <!-- Info Toko -->
        <div class="store-info mt-5">
          <h6 class="fw-bold mb-2">🏪 Info Toko</h6>
          <div class="d-flex align-items-center justify-content-between flex-wrap">
            <div>
              <p class="mb-0"><strong>Nama Toko:</strong> Asal_toko</p>
              <p class="mb-0 text-muted">Rating: 4.9 dari 500 ulasan</p>
            </div>
            <div class="d-flex gap-2 mt-2 mt-md-0">
              <button class="btn btn-outline-secondary btn-sm">Follow</button>
              <button class="btn btn-outline-primary btn-sm">Chat Penjual</button>
            </div>
          </div>
        </div>

        <!-- Info Pengiriman -->
        <div class="shipping-info mt-4">
          <h6 class="fw-bold mb-2">🚚 Info Pengiriman</h6>
          <ul class="mb-0">
            <li>Dikirim dari: Asal Kota</li>
            <li>Ongkos Kirim: Rp 5.000</li>
            <li>Estimasi Tiba: 9 - 12 Nov</li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()

const { product, selectedImage } = defineProps({
  product: Object,
  selectedImage: String
})

const emit = defineEmits([
  'update:variants',
  'update:quantity',
  'update:selectedImage'
])

const activeTab = ref('deskripsi')
const selectedType = ref(product.types?.[0]?.name || '')
const currentType = ref(product.types?.[0] || null)

function selectType(type) {
  selectedType.value = type.name
  currentType.value = type
  emit('update:selectedImage', type.images?.[0] || selectedImage)
}

function goToCheckout() {
  router.push({ name: 'checkout' })
}
</script>

<style scoped>
.product-box {
  background-color: #f0faff;
  padding: 30px;
  border-radius: 16px;
  border: 1px solid #cce6ff;
}

.main-image img {
  max-height: 400px;
  object-fit: cover;
}

.thumb-img {
  width: 70px;
  height: 70px;
  object-fit: cover;
  border-radius: 8px;
  cursor: pointer;
  border: 2px solid transparent;
  transition: border 0.2s ease;
}
.thumb-img.active {
  border-color: #0099cc;
}

.desc-list {
  padding-left: 18px;
  margin-bottom: 0;
}
.desc-list li {
  margin-bottom: 4px;
}

.tab-content {
  background-color: #ffffff;
  border: 1px solid #d0eaff;
  padding: 16px;
  border-radius: 12px;
}

.store-info,
.shipping-info {
  background-color: #f8fcff;
  border: 1px solid #d0eaff;
  padding: 16px;
  border-radius: 12px;
}
.store-info h6,
.shipping-info h6 {
  color: #0077aa;
}

.product-type-selector .btn {
  min-width: 100px;
  border-radius: 8px;
}

@media (max-width: 768px) {
  .main-image img {
    max-height: 300px;
  }

  .thumb-img {
    width: 60px;
    height: 60px;
  }

  .btn-group {
    flex-direction: column;
  }

  .btn-group .btn {
    width: 100%;
    margin-bottom: 8px;
  }

  .store-info,
  .shipping-info {
    font-size: 14px;
  }
}
</style>
