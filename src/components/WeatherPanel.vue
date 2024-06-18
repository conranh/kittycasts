<script setup>
import { toRefs } from 'vue';
import Search from './Search.vue';

const props = defineProps({
    city: String,
    state: String,
    currentTemp: Number,
    feelsLike: Number,
    condition: String,
    gust: Number,
    wind: Number,
    humidity: Number,
    forecast: Object,
    high: Number,
    low: Number,

    fetchedData: {
        type: Object,
        required: true
    }
});

const { 
    city, 
    state, 
    currentTemp, 
    feelsLike, 
    condition, 
    gust, 
    wind, 
    humidity, 
    forecast, 
    high, 
    low,
    } = toRefs(props);
</script>

<template>
    {{ fetchedData }}
<div class="current-container">
    <div class="location">
        {{ city && state ? city + ', ' + state : city || state }}
    </div>
    <div class="temp-container">
        <div class="current-temp">
            {{ currentTemp ? currentTemp + '°' : currentTemp}}
        </div>
        <div class="temp-details">
            <div class="feels-like">
                {{ feelsLike ? 'Feels Like: ' + feelsLike + '°' : feelsLike}}
            </div>
            <div>{{ low ? 'Low: ' + low + '°': low }}</div>
            <div>{{ high ? 'High: ' + high + '°': high }}</div>
        </div>
    </div>
    <img class="icon">
    <div class="condition">{{ condition }}
    </div>
</div>

<div class="air-container">
    <div class="air">
        <div class="wind">
            {{ wind ? 'Wind: ' + wind + ' mph' : wind }}
        </div>
        <div class="gust">
            {{ gust ? 'Gust: ' + gust + ' mph' : gust }}
        </div>
        <div class="humidity">
            {{ humidity ? 'Humidity: ' + humidity + '%' : humidity }}
        </div>
    </div>

<div class="later"></div>
</div>
</template>

<style>
.current-container {
    align-items: center;
    background-color: rgba(252, 230, 188, 0.75);
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
    display: flex;
    flex-direction: column;
    height:350px;
    left: 78px;
    position: relative;
    text-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
    top: 160px;
    width: 400px;
}

.location {
    display: flex;
    font-size: 28px;
    justify-content: center;
    margin-top: 27px;
}

.temp-container {
    display: flex;
    flex-direction: row;
    margin-top: 10px;
}

.current-temp {
    color: rgba(0, 23, 81, 0.72);
    display: flex;
    font-size: 72px;
    justify-content: flex-start;
    margin-top: 20px;
}

.temp-details {
    align-items: center;
    display: flex;
    flex-direction: column;
    font-size: 16px;
    justify-content: space-around;
    margin-left: 25px;
    margin-top: 10px;
}

.feels-like {
    font-size: 20px;
}

.condition {
    font-size: 24px;
    margin-top: 15px;
}

.air-container {
    display: flex;
    flex-direction: row;
}

.air {
    align-items: center;
    background-color: rgba(198, 230, 255, 0.9);
    box-shadow: 
        0px 4px 4px rgba(0, 0, 0, 0.25), 
        0px 4px 4px rgba(0, 0, 0, 0.25);
    display: flex;
    flex-direction: column;
    font-size: 20px;
    height: 175px;
    justify-content: space-around;
    Left: 78px;
    position: relative;
    top: 180px;
    width: 175px;
}

.later {
    align-items: center;
    background-color: rgba(198, 230, 255, 0.9);
    box-shadow: 
        0px 4px 4px rgba(0, 0, 0, 0.25), 
        0px 4px 4px rgba(0, 0, 0, 0.25);
    display: flex;
    flex-direction: column;
    font-size: 20px;
    height: 175px;
    justify-content: space-around;
    Left: 130px;
    position: relative;
    top: 180px;
    width: 175px;
}
</style>