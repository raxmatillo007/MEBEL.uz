<template>
  <header class="header">
    <div class="container">
      <!-- Chap tomon: Logo va Kategoriyalar -->
      <div class="left">
        <div class="logo">Mebel.uz</div>
        <div class="dropdown" ref="dropdown">
          <button class="dropdown-toggle" @click="toggleDropdown" type="button" aria-haspopup="true" :aria-expanded="isOpen.toString()">
            <i class="fas fa-bars"></i>
            Kategoriyalar
            <i :class="['fas', isOpen ? 'fa-chevron-up' : 'fa-chevron-down']"></i>
          </button>
          <ul v-if="isOpen" class="dropdown-menu" role="menu">
            <li role="none"><a href="#" role="menuitem">Yumshoq mebel</a></li>
            <li role="none"><a href="#" role="menuitem">Yotoqxona</a></li>
            <li role="none"><a href="#" role="menuitem">Ofis mebeli</a></li>
          </ul>
        </div>
      </div>

      <!-- O'rtada: Qidiruv -->
      <form class="search" @submit.prevent="submitSearch">
        <input
          v-model="searchQuery"
          type="text"
          placeholder="Nimani qidiryapsiz?"
          @keydown.enter.prevent="submitSearch"
          aria-label="Qidiruv"
          autocomplete="off"
          spellcheck="false"
        />
        <button type="submit" aria-label="Qidiruvni boshlash"><i class="fas fa-search"></i></button>
      </form>

      <!-- O'ng tomon: Bosh menyu, Tillar, Shahar va Profil -->
      <div class="right">
        <nav class="main-menu" role="navigation" aria-label="Asosiy menyu">
          <ul>
            <li><a href="#">Home</a></li>
            <li><a href="#">About</a></li>
            <li><a href="#">Settings</a></li>
            <li><a href="#">Contact</a></li>
            <li><a href="#">Blog</a></li>  <!-- Yangi menyu elementi -->
          </ul>
        </nav>

        <div class="actions">
          <select v-model="city" aria-label="Shahar tanlash">
            <option value="toshkent">Toshkent</option>
            <option value="samarqand">Samarqand</option>
          </select>
          <select v-model="language" aria-label="Til tanlash">
            <option value="uz">O'zbekcha</option>
            <option value="ru">Русский</option>
          </select>
          <button class="profile-btn" aria-label="Profil">
            <i class="fas fa-user-circle"></i>
          </button>
        </div>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      isOpen: false,
      searchQuery: "",
      city: "toshkent",
      language: "uz",
    };
  },
  methods: {
    toggleDropdown() {
      this.isOpen = !this.isOpen;
    },
    handleClickOutside(event) {
      const dropdown = this.$refs.dropdown;
      if (dropdown && !dropdown.contains(event.target)) {
        this.isOpen = false;
      }
    },
    submitSearch() {
      if (this.searchQuery.trim() === "") {
        alert("Iltimos, qidiruv so'zini kiriting");
        return;
      }
      alert(`Qidirilmoqda: ${this.searchQuery}`);
    },
  },
  mounted() {
    document.addEventListener("click", this.handleClickOutside);
  },
  beforeUnmount() {
    document.removeEventListener("click", this.handleClickOutside);
  },
};
</script>

<style scoped>
/* Umumiy */
* {
  box-sizing: border-box;
}

.header {
  background-color: #fff;
  border-bottom: 1px solid #eee;
  position: sticky;
  top: 0;
  z-index: 1000;
  width: 100%;
  user-select: none;
}

.container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 12px 24px;
  flex-wrap: wrap;
  gap: 16px;
}

/* Chap tomon */
.left {
  display: flex;
  align-items: center;
  gap: 20px;
}

.logo {
  font-size: 1.8rem;
  font-weight: 700;
  color: #2c3e50;
  user-select: text;
}

.dropdown {
  position: relative;
}

.dropdown-toggle {
  background-color: #f1f1f1;
  border: none;
  padding: 10px 16px;
  border-radius: 12px;
  font-weight: 600;
  display: flex;
  align-items: center;
  gap: 10px;
  cursor: pointer;
  user-select: none;
  transition: background-color 0.3s ease;
  font-size: 16px;
  color: #34495e;
}

.dropdown-toggle:hover,
.dropdown-toggle:focus {
  background-color: #d6e6fa;
  outline: none;
}

.dropdown-toggle i.fas.fa-bars {
  font-size: 20px;
  color: #3498db;
}

.dropdown-toggle i.fas.fa-chevron-up,
.dropdown-toggle i.fas.fa-chevron-down {
  font-size: 14px;
  color: #3498db;
  margin-left: 6px;
}

/* Dropdown menyu */
.dropdown-menu {
  list-style: none;
  position: absolute;
  top: 50px;
  left: 0;
  background: #fff;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  border-radius: 10px;
  width: 200px;
  padding: 12px 0;
  z-index: 100;
  user-select: none;
}

.dropdown-menu li {
  padding: 12px 20px;
}

.dropdown-menu li a {
  color: #2c3e50;
  text-decoration: none;
  display: block;
  font-weight: 500;
  font-size: 16px;
  transition: color 0.3s ease;
}

.dropdown-menu li:hover {
  background-color: #e8f0fe;
}

.dropdown-menu li:hover a {
  color: #3498db;
}

/* Qidiruv */
.search {
  flex: 1;
  display: flex;
  max-width: 600px;
  border: 2px solid #3498db;
  border-radius: 40px;
  overflow: hidden;
  background-color: white;
  height: 48px;
  box-shadow: 0 2px 6px rgba(52, 152, 219, 0.25);
}

.search input {
  flex: 1;
  padding: 0 20px;
  border: none;
  font-size: 18px;
  font-weight: 400;
  background: transparent;
  color: #2c3e50;
  line-height: 48px;
}

.search input::placeholder {
  font-weight: 300;
  font-size: 16px;
  color: #999;
}

.search button {
  background-color: #3498db;
  border: none;
  color: #fff;
  padding: 0 24px;
  cursor: pointer;
  font-size: 20px;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: background-color 0.3s ease;
}

.search button:hover {
  background-color: #1d6dbb;
}

/* O'ng tomon */
.right {
  display: flex;
  align-items: center;
  gap: 20px;
}

/* Bosh menyu */
.main-menu ul {
  display: flex;
  list-style: none;
  padding: 0;
  margin: 0;
  gap: 20px;
}

.main-menu ul li a {
  text-decoration: none;
  color: #2c3e50;
  font-weight: 600;
  padding: 8px 14px;
  border-radius: 8px;
  transition: background-color 0.3s ease, color 0.3s ease;
}

.main-menu ul li a:hover,
.main-menu ul li a:focus {
  background-color: #3498db;
  color: white;
  outline: none;
}

/* Actions */
.actions {
  display: flex;
  align-items: center;
  gap: 16px;
}

.actions select {
  padding: 8px 14px;
  border-radius: 8px;
  border: 1px solid #ccc;
  background-color: #fff;
  font-size: 14px;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
  background-image: none;
  cursor: pointer;
  transition: border-color 0.3s ease;
}

.actions select:hover,
.actions select:focus {
  border-color: #3498db;
  outline: none;
}

.profile-btn {
  background: none;
  border: none;
  font-size: 28px;
  color: #3498db;
  cursor: pointer;
  transition: color 0.3s ease;
}

.profile-btn:hover,
.profile-btn:focus {
  color: #1d6dbb;
  outline: none;
}

/* Responsive */
@media (max-width: 768px) {
  .container {
    flex-direction: column;
    gap: 12px;
    align-items: stretch;
  }

  .left {
    justify-content: space-between;
  }

  .search {
    max-width: 100%;
  }

  .right {
    flex-wrap: wrap;
    justify-content: space-between;
  }

  .main-menu ul {
    flex-wrap: wrap;
    gap: 10px;
  }
}
</style>
