<template>
  <div class="product-list">
    <ProductCard
      v-for="product in paginatedProducts"
      :key="product.id"
      :product="product"
    />
  </div>
</template>

<script>
import ProductCard from './ProductCard.vue';
import sofaImage from '@/assets/img/sofa.avif';

export default {
  name: 'ProductList',
  components: { ProductCard },
  props: {
    currentPage: {
      type: Number,
      default: 1
    },
    itemsPerPage: {
      type: Number,
      default: 8
    }
  },
  data() {
    return {
      products: [
        { id: 1, name: 'Divan Royal', price: 2500000, image: sofaImage },
        { id: 2, name: 'Kreslo Comfort', price: 1200000, image: sofaImage },
        { id: 3, name: 'Karavot Classic', price: 3400000, image: sofaImage },
        { id: 4, name: 'Divan Modern', price: 2700000, image: sofaImage },
        { id: 5, name: 'Kreslo Deluxe', price: 1500000, image: sofaImage },
        { id: 6, name: 'Karavot Lux', price: 3900000, image: sofaImage },
        { id: 7, name: 'Divan Soft', price: 2200000, image: sofaImage },
        { id: 8, name: 'Kreslo Cozy', price: 1100000, image: sofaImage },
        { id: 9, name: 'Divan Elegant', price: 2600000, image: sofaImage },
        { id: 10, name: 'Kreslo Relax', price: 1350000, image: sofaImage },
        { id: 11, name: 'Karavot Premium', price: 3600000, image: sofaImage },
        { id: 12, name: 'Divan Classic', price: 2450000, image: sofaImage },
        { id: 13, name: 'Kreslo Soft', price: 1400000, image: sofaImage },
        { id: 14, name: 'Karavot Modern', price: 3200000, image: sofaImage },
        { id: 15, name: 'Divan Cozy', price: 2300000, image: sofaImage },
        { id: 16, name: 'Kreslo Premium', price: 1700000, image: sofaImage },
        { id: 17, name: 'Karavot Soft', price: 3000000, image: sofaImage },
        { id: 18, name: 'Divan Deluxe', price: 2800000, image: sofaImage },
        { id: 19, name: 'Kreslo Elegant', price: 1600000, image: sofaImage },
        { id: 20, name: 'Karavot Cozy', price: 3100000, image: sofaImage }
      ]
    };
  },
  computed: {
    paginatedProducts() {
      const start = (this.currentPage - 1) * this.itemsPerPage;
      const end = start + this.itemsPerPage;
      return this.products.slice(start, end);
    }
  }
};
</script>

<style scoped>
.product-list {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
  gap: 20px;
  padding: 20px 0;
  justify-items: center;
}
</style>
