# Vue3 Weather App

Vue3를 활용해 개발한 도시별 날씨 조회 서비스입니다.

### 🔗 배포 링크  
[https://vue-weather-orpin.vercel.app/](https://vue-weather-orpin.vercel.app/)

---

## 🛠️ 주요 기능 및 설계 방식

### 1. 컴포넌트 기반 설계
- SearchBar, WeatherCard 등 독립적이고 재사용 가능한 UI 컴포넌트 구성
- 관심 있는 기능별로 컴포넌트를 분리하여 유지보수성과 가독성 향상

### 2. 사용자 UX 개선
- 빈값 입력 시 안내 메시지 출력
- 동일한 도시 중복 검색 방지
- API 호출 실패 시 에러 처리 및 알림 제공

### 3. 동적 UI 렌더링
- Vue3의 `ref`, `v-if`, `v-for`를 활용하여 데이터 상태에 따라 유동적으로 화면 구성
- 사용자의 검색 결과에 따라 날씨 정보 동적 출력

---

## ⚙️ 기술 스택

|구분|기술|
|---|---|
|Frontend|Vue3, Vite|
|API|OpenWeather API|
|Deployment|Vercel|

---

## ⚡ 아쉬운 점 & 개선 방향

|문제|내용|
|---|---|
|서버 상태 관리|fetch로 API 호출 후 상태(loading, error, success)를 직접 처리|
|데이터 캐싱 부재|동일한 요청 시에도 API를 매번 호출|
|코드 구조|에러 처리, 로딩 처리, 데이터 캐싱 등이 수동적|

> 위 한계점을 기반으로 동일한 날씨 앱을 Next.js + React Query 기반으로 리팩토링하며 개선 경험을 쌓았습니다.
