<template>
  <div class="product-card" @click="handleClick">
    <div class="image-wrapper">
      <img :src="product.image" :alt="product.name" />
    </div>
    <div class="product-info">
      <h3 class="product-name">{{ product.name }}</h3>
      <p class="product-price">{{ formattedPrice }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ProductCard',
  props: {
    product: {
      type: Object,
      required: true
    }
  },
  computed: {
    formattedPrice() {
      // Narxni mingliklar bo'yicha ajratib ko'rsatish (masalan, 2 500 000 so'm)
      return this.product.price.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ' ') + ' so\'m';
    }
  },
  methods: {
    handleClick() {
      // Mahsulotga bosilganda nimadir qilish mumkin (alert, router push, va h.k)
      alert(`Siz "${this.product.name}" mahsulotini tanladingiz!`);
    }
  }
}
</script>

<style scoped>
.product-card {
  width: 220px;
  background-color: #fff;
  border-radius: 12px;
  box-shadow: 0 6px 12px rgba(0,0,0,0.1);
  cursor: pointer;
  transition: transform 0.25s ease, box-shadow 0.25s ease;
  display: flex;
  flex-direction: column;
  overflow: hidden;
}

.product-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 12px 24px rgba(0,0,0,0.15);
}

.image-wrapper {
  width: 100%;
  height: 140px;
  overflow: hidden;
  border-bottom: 1px solid #eee;
}

.image-wrapper img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: scale 0.3s ease;
}

.product-card:hover .image-wrapper img {
  transform: scale(1.05);
}

.product-info {
  padding: 16px;
  text-align: left;
  flex-grow: 1;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.product-name {
  font-size: 1.1rem;
  font-weight: 600;
  color: #333;
  margin: 0 0 8px 0;
  line-height: 1.2;
}

.product-price {
  font-size: 1rem;
  font-weight: 700;
  color: #1a73e8;
  margin: 0;
}
</style>
