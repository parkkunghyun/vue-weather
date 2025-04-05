<template>
    <div class="card">
      <h2>{{ weather.name }}</h2>
      <img :src="`https://openweathermap.org/img/wn/${weather.icon}@2x.png`" />
      <p>{{ weather.description }}</p>
      <p>{{ weather.temp }}°C</p>
    </div>
  </template>
  
  <script setup>
  defineProps({
    weather: Object
  })
  </script>
  
  <style scoped>
  .card {
    background: white;
    border-radius: 10px;
    padding: 1rem;
    text-align: center;
    width: 150px;
    box-shadow: 0 4px 8px rgba(0,0,0,0.1);
    transition: 0.3s;
  }
  .card:hover {
    transform: translateY(-5px);
  }
  img {
    width: 80px;
    height: 80px;
  }
  </style>
  