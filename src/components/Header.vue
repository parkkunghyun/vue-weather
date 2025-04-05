<template>
    <header class="header">
      <h1 class="title">Weather App</h1>
    </header>
  </template>
  
  <style scoped>
  .header {
    background: linear-gradient(90deg, #0ea5e9 0%, #38bdf8 100%);
    color: white;
    text-align: center;
    padding: 2rem 1rem;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
    position: sticky;
    top: 0;
    z-index: 100;
  }
  
  .title {
    font-size: 2.5rem;
    font-weight: 800;
    letter-spacing: 1px;
    text-shadow: 2px 2px 6px rgba(0, 0, 0, 0.2);
    animation: fadeDown 1s ease;
  }
  
  /* 타이틀 애니메이션 */
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
  </style>
  