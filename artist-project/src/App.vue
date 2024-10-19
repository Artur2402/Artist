<script setup>
import Categories from './components/Categories.vue';
import VideoSlider from './components/VideoSlider.vue';
import Artists from './components/Artists.vue';
</script>

<template>
  <div>
    <h1>Главная страница</h1>
    <VideoSlider />
    <Categories />
    <Artists />
  </div>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}

h1 {
  text-align: center;
  margin-top: 20px;
}
</style>
