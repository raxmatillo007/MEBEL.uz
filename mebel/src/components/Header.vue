<template>
  <header class="header">
    <div class="container">
      <div class="logo">MeubelShop</div>
      <nav :class="{ 'nav-active': isNavOpen }" class="nav">
        <ul>
          <li><router-link to="/">Bosh sahifa</router-link></li>
          <li><router-link to="/about">Biz haqimizda</router-link></li>
          <li><router-link to="/products">Mahsulotlar</router-link></li>
          <li><router-link to="/contact">Bog'lanish</router-link></li>
        </ul>
      </nav>
      <button class="burger" @click="toggleNav">
        <span :class="{ 'line1': true, 'active': isNavOpen }"></span>
        <span :class="{ 'line2': true, 'active': isNavOpen }"></span>
        <span :class="{ 'line3': true, 'active': isNavOpen }"></span>
      </button>
    </div>
  </header>
</template>

<script>
export default {
  name: 'Header',
  data() {
    return {
      isNavOpen: false
    }
  },
  methods: {
    toggleNav() {
      this.isNavOpen = !this.isNavOpen
    }
  }
}
</script>

<style scoped>
.header {
  background-color: #ffffff;
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
  position: sticky;
  top: 0;
  z-index: 1000;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
  height: 60px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.logo {
  font-weight: 700;
  font-size: 1.5rem;
  color: #2c3e50;
  cursor: pointer;
}

.nav ul {
  list-style: none;
  display: flex;
  gap: 24px;
  margin: 0;
  padding: 0;
}

.nav ul li a {
  text-decoration: none;
  color: #34495e;
  font-weight: 600;
  transition: color 0.3s ease;
}

.nav ul li a:hover {
  color: #e67e22;
}

/* Burger button */
.burger {
  display: none;
  flex-direction: column;
  border: none;
  background: none;
  cursor: pointer;
  gap: 6px;
  padding: 0;
  z-index: 1100;
}

.burger span {
  width: 25px;
  height: 3px;
  background-color: #34495e;
  border-radius: 2px;
  transition: all 0.3s ease;
}

/* Burger animation */
.line1.active {
  transform: rotate(45deg) translate(5px, 5px);
}

.line2.active {
  opacity: 0;
}

.line3.active {
  transform: rotate(-45deg) translate(5px, -5px);
}

/* Responsive */
@media (max-width: 768px) {
  .nav {
    position: fixed;
    top: 60px;
    right: 0;
    background-color: #fff;
    height: calc(100% - 60px);
    width: 250px;
    transform: translateX(100%);
    transition: transform 0.3s ease-in-out;
    box-shadow: -2px 0 8px rgba(0,0,0,0.1);
    padding-top: 20px;
  }

  .nav.nav-active {
    transform: translateX(0);
  }

  .nav ul {
    flex-direction: column;
    gap: 16px;
    padding-left: 20px;
  }

  .burger {
    display: flex;
  }
}
</style>
