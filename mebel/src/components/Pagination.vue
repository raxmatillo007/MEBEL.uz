<template>
  <nav class="pagination" aria-label="Pagination Navigation">
    <button 
      class="page-btn" 
      :disabled="currentPage === 1" 
      @click="$emit('page-changed', currentPage - 1)">
      &laquo; Oldingi
    </button>

    <button 
      v-for="page in pages" 
      :key="page" 
      class="page-btn" 
      :class="{ active: page === currentPage }" 
      @click="$emit('page-changed', page)">
      {{ page }}
    </button>

    <button 
      class="page-btn" 
      :disabled="currentPage === totalPages" 
      @click="$emit('page-changed', currentPage + 1)">
      Keyingi &raquo;
    </button>
  </nav>
</template>

<script>
export default {
  name: 'Pagination',
  props: {
    currentPage: {
      type: Number,
      default: 1
    },
    totalPages: {
      type: Number,
      required: true
    }
  },
  computed: {
    pages() {
      let pages = [];
      for(let i = 1; i <= this.totalPages; i++) {
        pages.push(i);
      }
      return pages;
    }
  }
}
</script>

<style scoped>
.pagination {
  display: flex;
  justify-content: center;
  gap: 8px;
  margin: 20px 0;
  user-select: none;
}

.page-btn {
  padding: 8px 14px;
  border: none;
  background-color: #eee;
  color: #444;
  font-weight: 600;
  border-radius: 6px;
  cursor: pointer;
  transition: background-color 0.25s, color 0.25s;
}

.page-btn:hover:not(:disabled) {
  background-color: #007bff;
  color: white;
}

.page-btn:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}

.page-btn.active {
  background-color: #007bff;
  color: white;
  cursor: default;
  box-shadow: 0 0 8px rgba(0, 123, 255, 0.6);
}
</style>
