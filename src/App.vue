<template>
  <div>
    <Header />
    <HomeView />
    <Footer />
  </div>
</template>

<script setup>
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'
import HomeView from './views/HomeView.vue'
</script>

<style>
body {
  margin: 0;
  font-family: 'Arial', sans-serif;
  background-color: #f1f5f9;
}
</style>
