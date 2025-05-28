<template>
  <aside class="sidebar">
    <h2 class="sidebar-title">Kategoriyalar</h2>
    <ul class="category-list">
      <li v-for="category in categories" :key="category.id" class="category-item">
        <a href="#" @click.prevent="selectCategory(category.name)" :class="{ active: selectedCategory === category.name }">
          {{ category.name }}
        </a>
      </li>
    </ul>
  </aside>
</template>

<script>
export default {
  name: "Sidebar",
  data() {
    return {
      categories: [
        { id: 1, name: "Divanlar" },
        { id: 2, name: "Kreslolar" },
        { id: 3, name: "Karavotlar" },
        { id: 4, name: "Stollar" },
        { id: 5, name: "Stullar" },
      ],
      selectedCategory: null,
    };
  },
  methods: {
    selectCategory(category) {
      this.selectedCategory = category;
      this.$emit("category-selected", category); // tashqi componentlarga habar beramiz
    },
  },
};
</script>

<style scoped>
.sidebar {
  width: 250px;
  background: #f7f9fc;
  border-radius: 8px;
  padding: 20px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.1);
  height: fit-content;
}

.sidebar-title {
  font-size: 1.2rem;
  font-weight: 700;
  margin-bottom: 20px;
  color: #2c3e50;
}

.category-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.category-item + .category-item {
  margin-top: 12px;
}

.category-item a {
  text-decoration: none;
  color: #34495e;
  font-weight: 600;
  display: block;
  padding: 10px 15px;
  border-radius: 6px;
  transition: background-color 0.3s ease, color 0.3s ease;
  cursor: pointer;
}

.category-item a:hover,
.category-item a.active {
  background-color: #e67e22;
  color: white;
}

/* Responsive kichik ekran uchun */
@media (max-width: 768px) {
  .sidebar {
    width: 100%;
    margin-bottom: 20px;
  }
}
</style>

