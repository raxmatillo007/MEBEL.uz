<template>
  <div id="app">
    <Header />
    <RouterView />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import { RouterView } from 'vue-router';

export default {
  components: { Header, RouterView }
};
</script>
