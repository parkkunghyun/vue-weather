<template>
    <div class="container">
  
      <SearchBar @search="fetchWeather" />
  
      <div v-if="errorMsg" class="error">
        {{ errorMsg }}
      </div>
  
      <div v-if="weathers.length === 0 && !errorMsg" class="empty">
        검색해서 도시 날씨를 확인해보세요!
      </div>
  
      <div class="cards">
        <WeatherCard
          v-for="weather in weathers"
          :key="weather.id"
          :weather="weather"
        />
      </div>
    </div>
  </template>
  
  
  <script setup>
import { ref } from 'vue'
import SearchBar from '../components/SearchBar.vue'
import WeatherCard from '../components/WeatherCard.vue'

const weathers = ref([])
const errorMsg = ref('')  // 에러메세지용 ref

async function fetchWeather(city) {
    const apiKey = import.meta.env.VITE_API_KEY
  const url = `https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${apiKey}&units=metric`

  // 빈값 체크
  if (!city.trim()) {
    alert('도시를 입력해주세요.')
    return
  }

  // 중복 체크
  const isDuplicate = weathers.value.some(w => w.name.toLowerCase() === city.toLowerCase())
  if (isDuplicate) {
    alert('이미 추가된 도시입니다.')
    return
  }

  try {
    const res = await fetch(url)
    const data = await res.json()

    // 존재하지 않는 도시
    if (res.status === 404) {
      alert('존재하지 않는 도시입니다. 다시 입력해주세요.')
      return
    }

    // 성공 처리
    errorMsg.value = ''
    weathers.value.push({
      id: data.id,
      name: data.name,
      temp: data.main.temp,
      icon: data.weather[0].icon,
      description: data.weather[0].main
    })

  } catch (error) {
    alert('오류가 발생했습니다. 다시 시도해주세요.')
  }
}


</script>

  
  <style scoped>
.container {
  max-width: 900px;
  margin: 0 auto;
  padding: 2rem 1rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  min-height: 100vh;
}

.title {
  font-size: 3rem;
  font-weight: 800;
  margin-bottom: 2rem;
  color: #0ea5e9;
  text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.2);
  animation: fadeDown 1s ease;
}

.empty {
  color: #94a3b8;
  margin-top: 3rem;
  font-size: 1.3rem;
  animation: fadeUp 1s ease;
}

.cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 1.5rem;
  width: 100%;
  margin-top: 2rem;
  animation: fadeUp 1s ease;
}

.error {
  color: #ef4444;
  margin-top: 1.5rem;
  font-size: 1.1rem;
  animation: fadeUp 0.5s ease;
}

/* 애니메이션 */
@keyframes fadeDown {
  from {
    opacity: 0;
    transform: translateY(-20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes fadeUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* 반응형 */
@media (max-width: 500px) {
  .title {
    font-size: 2.2rem;
  }

  .empty {
    font-size: 1rem;
  }
}
</style>
