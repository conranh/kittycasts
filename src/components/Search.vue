<script setup>
import { ref, watch, getCurrentInstance } from "vue";
import { fetchWeather } from "../services/WeatherApi.js";
import Autocomplete from "./Autocomplete.vue";

const selectedCity = ref(null);
const { emit } = getCurrentInstance();

// Component is notified when a city is selected and sends this info to the API for display
watch(selectedCity, async (city) => {
  if (city) {
    const weatherData = await fetchWeather(city);
    emit("weather-data", weatherData);
  }
});
</script>

<template>
  <div class="search-container">
    <form id="searchBar" class="search-bar" autocomplete="off">
      <input
        id="input"
        v-model="input"
        type="text"
        placeholder="Search for your city/state or zip code"
      />
      <button id="searchButton" class="search-button" type="submit"></button>
    </form>
    <Autocomplete @city-selected="selectedCity = $event" />
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Chela+One&family=Share+Tech+Mono&display=swap');

.search-bar {
  display: flex;
  border-color: auto;
  border-width: 3px;
  border-style: solid;
  width: 445px;
  height: 45px;
}

input {
  outline: none;
  border: none;
  padding: 10px;
  font-size: 20px;
  width: 420px;
  background-color: transparent;
  font-family: "Chela One", system-ui;
}

.search-button {
  background-color: transparent;
  background-image: url("/src/assets/images/search.png");
  background-position: center;
  background-repeat: no-repeat;
  border: none;
  cursor: pointer;
  width: 38px;
}

.search-container {
  display: flex;
  flex-direction: column;
  position: absolute;
  top: 25px;
  left: 25px;
}

@media only screen and (max-width: 430px) {
  .search-bar {
    width: 375px;
    height: 37px;
  }

  input {
    font-size: 18px;
    width: 350px;
  }

  .search-button {
    width: 35px;
  }
}
</style>
