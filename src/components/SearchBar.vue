<template>
    <div class="search-bar">
      <input
        v-model="city"
        type="text"
        placeholder="도시를 입력하세요"
        @keyup.enter="onSearch"
      />
      <button @click="onSearch">검색</button>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  
  const emit = defineEmits(['search'])
  const city = ref('')
  
  function onSearch() {
    emit('search', city.value)
    city.value = ''   // 검색 후 input 초기화
  }
  </script>
  
  
  <style scoped>
  .search {
    display: flex;
    justify-content: center;
    gap: 0.5rem;
    margin: 1rem 0;
  }
  input {
    padding: 0.5rem;
    width: 200px;
  }
  button {
    background: #0ea5e9;
    color: white;
    padding: 0.5rem 1rem;
    border: none;
    cursor: pointer;
    transition: 0.3s;
  }
  button:hover {
    background: #0284c7;
  }
  </style>
  