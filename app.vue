<template>
  <div class="container">
    <span :class="['logo']">ikakprosto.ru</span>
    <NuxtPage />
  </div>
</template>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  max-width: 676px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.logo {
  color:rgb(250, 108, 6);
  font-size: 24px;
  font-weight: bold;
}
</style>
