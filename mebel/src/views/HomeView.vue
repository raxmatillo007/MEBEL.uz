<template>
  <div class="home-container">
    

    <main class="home-content">
      <HeroBanner />
      <div class="content-layout">
        <Sidebar />
        <div class="products-area">
          <ProductList :currentPage="currentPage" />
          <Pagination
            :currentPage="currentPage"
            :totalPages="totalPages"
            @page-changed="handlePageChange"
          />
        </div>
      </div>
    </main>
  </div>
</template>

<script>
import Header from '@/components/Header.vue'
import HeroBanner from '@/components/HeroBanner.vue'
import Sidebar from '@/components/Sidebar.vue'
import ProductList from '@/components/ProductList.vue'
import Pagination from '@/components/Pagination.vue'

export default {
  name: 'HomeView',
  components: {
    Header,
    HeroBanner,
    Sidebar,
    ProductList,
    Pagination
  },
  data() {
    return {
      currentPage: 1,
      totalPages: 5
    }
  },
  methods: {
    handlePageChange(newPage) {
      this.currentPage = newPage
    }
  }
}
</script>

<style scoped>
.home-container {
  background-color: #f8f9fa;
  min-height: 100vh;
}

.home-content {
  padding: 20px;
}

.content-layout {
  display: flex;
  flex-wrap: wrap;
  gap: 24px;
  margin-top: 20px;
}

.products-area {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 20px;
}
</style>
