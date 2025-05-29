<template>
  <div id="app">
    <div v-if="loading" class="loading-overlay">
      <div class="spinner"></div>
      <h3>Sayt yuklanmoqda...</h3>
    </div>
    <div v-else>
      <Header />
      <RouterView />
    </div>
  </div>
</template>

<script>
import Header from './components/Header.vue'

export default {
  components: { Header },
  data() {
    return {
      loading: true
    }
  },
  mounted() {
    setTimeout(() => {
      this.loading = false
    }, 2000)
  }
}
</script>

<style>
.loading-overlay {
  position: fixed;
  inset: 0;
  background: linear-gradient(135deg, #007bff, #00c6ff);
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  z-index: 9999;
  color: white;
  font-family: 'Segoe UI', sans-serif;
}

.spinner {
  border: 6px solid rgba(255, 255, 255, 0.2);
  border-top: 6px solid #ffffff;
  border-radius: 50%;
  width: 60px;
  height: 60px;
  animation: spin 1s ease-in-out infinite;
  margin-bottom: 16px;
}

@keyframes spin {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
</style>
