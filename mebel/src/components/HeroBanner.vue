<template>
  <section class="hero-banner">
    <div class="hero-content">
      <h1 class="hero-title">Yumshoq va zamonaviy mebellar</h1>
      <p class="hero-subtitle">
        Uyingiz uchun qulaylik va go‘zallikni birlashtiring
      </p>
      <button class="hero-btn" @click="shopNow">Hozir xarid qiling</button>
    </div>
    <div class="hero-image">
      <img :src="bannerImage" alt="Mebel banner" />
    </div>
  </section>
</template>

<script>
import bannerImage from '@/assets/img/sofa.avif'

export default {
  name: 'HeroBanner',
  data() {
    return {
      bannerImage
    }
  },
  methods: {
    shopNow() {
      alert('Do‘konimizga xush kelibsiz!') 
      // Keyin bu yerga masalan, router push qilinishi mumkin
    }
  }
}
</script>

<style scoped>
.hero-banner {
  display: flex;
  align-items: center;
  justify-content: space-between;
  background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
  border-radius: 12px;
  padding: 40px 30px;
  box-shadow: 0 8px 20px rgba(0,0,0,0.1);
  gap: 40px;
  flex-wrap: wrap;
}

.hero-content {
  max-width: 500px;
}

.hero-title {
  font-size: 2.8rem;
  color: #2c3e50;
  margin-bottom: 16px;
  font-weight: 700;
  line-height: 1.2;
}

.hero-subtitle {
  font-size: 1.1rem;
  color: #555;
  margin-bottom: 24px;
}

.hero-btn {
  background-color: #e67e22;
  color: white;
  border: none;
  padding: 14px 28px;
  font-size: 1rem;
  font-weight: 600;
  border-radius: 30px;
  cursor: pointer;
  transition: background-color 0.3s ease;
  box-shadow: 0 4px 12px rgba(230,126,34,0.6);
}

.hero-btn:hover {
  background-color: #cf6f14;
}

.hero-image img {
  max-width: 400px;
  width: 100%;
  border-radius: 12px;
  box-shadow: 0 8px 20px rgba(0,0,0,0.1);
}

/* Responsive kichik ekran uchun */
@media (max-width: 768px) {
  .hero-banner {
    flex-direction: column;
    text-align: center;
  }
  .hero-content {
    max-width: 100%;
  }
  .hero-image img {
    max-width: 100%;
    margin-top: 20px;
  }
}
</style>
