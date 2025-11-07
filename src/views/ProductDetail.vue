<template>
  <template v-if="product">
    <ProductDetailContent
      :product="product"
      :selectedImage="selectedImage"
      :selectedVariants="selectedVariants"
      :quantity="quantity"
      @update:quantity="quantity = $event"
      @update:variants="selectedVariants = $event"
      @back="goBack"
    />
  </template>

  <template v-else>
    <div class="text-center my-5">
      <div class="spinner-border"></div>
      <p>Loading...</p>
    </div>
  </template>
</template>

<script>
import ProductDetailContent from "../components/ProductDetailContent.vue";

export default {
  components: { ProductDetailContent },
  data() {
    return {
      product: null,
      selectedImage: "",
      quantity: 1,
      selectedVariants: {}
    };
  },
  mounted() {
    const id = Number(this.$route.params.id);
    const products = [
      { id: 1, name: "Reel Pancing Premium", images: ["https://picsum.photos/500/400?1", "https://picsum.photos/500/400?4"], price: 150000, stock: 10, rating: 4.5, description: "Reel pancing premium", variants: [{ name: "Warna", options: ["Hitam", "Merah", "Biru"] }] },
      { id: 2, name: "Kail Pancing Super", images: ["https://picsum.photos/500/400?2"], price: 50000, stock: 20, rating: 4.0, description: "Kail berkualitas tinggi", variants: [] },
      { id: 3, name: "Umpan Ikan Segar", images: ["https://picsum.photos/500/400?3"], price: 25000, stock: 15, rating: 4.2, description: "Umpan ikan segar", variants: [] }
    ];

    this.product = products.find(p => p.id === id);
    if (!this.product) this.$router.push("/");

    this.selectedImage = this.product.images[0];
    this.product.variants?.forEach(v => this.selectedVariants[v.name] = v.options[0]);
  },
  methods: {
    goBack() {
      window.history.length > 1 ? this.$router.back() : this.$router.push("/");
    }
  }
};
</script>
