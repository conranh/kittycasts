<script setup>
import { ref } from 'vue';
import Search from './components/Search.vue';
import WeatherPanel from './components/WeatherPanel.vue';
import CatBox from './components/CatBox.vue';

const weatherData = ref(null);

function handleWeatherData(data) {
  weatherData.value = data;
}

function handleDataFetched(data) {
  this.fetchedData = data;
}

</script>

<template>
  <header>
    <img class="logo" src="/src/assets/images/kitty.png">
    <h1>KittyCaSts</h1>
    <h3>Get local forecasts and clothing recommendations from a kitty cat!</h3>
  </header>
  <div class="container">
  <div class="panel">
    <Search @weather-data="handleWeatherData" @data-fetched="handleDataFetched"/>
    <WeatherPanel v-bind="weatherData" :fetched-data="fetchedData"/>
  </div>
    <CatBox/>
  </div>

</template>

<style>
h1 {
  position: absolute;
  left: 170px;
  font-weight: 500;
  text-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
  font-size: 68px;
  margin-top: 15px;
}

h3 {
  position: absolute;
  left: 525px;
  margin-top: 40px;
  text-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
}

.container {
  display: flex;
  flex-direction: row;
}

.logo {
  position: absolute;
  left: 17px;
  width: 140px;
  height: 90px;
  object-fit: cover;
}

header {
  position: relative;
  margin: 0;
  box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.15);
  background-color: rgba(255, 255, 255, 0.21);
  height: 90px;
}

.panel {
  position: relative;
  box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.4);
  height: 1027px;
  width: 564px;
}
</style>
