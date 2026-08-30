<script setup lang="ts">
import { h, ref } from 'vue';
let temp = ref(0);
let humidity = ref(0);
const url = "/api/";
async function fetchurl() {
  let sensor = await fetch(url);
  let data = await sensor.json();
  temp.value = data.temperature;
  humidity.value = data.humidity;
}
// call api on browser load
window.addEventListener("DOMContentLoaded", fetchurl);
// make it automatic
setInterval(fetchurl, 30000);
</script>
<template>
<div class ="lg:border lg:border-black lg:dark:border-white rounded-2xl p-4 lg:p-15">
    <h1 v-if="temp > 20" class="text-6xl font-bold">How hot your day?</h1>
    <h1 v-if="temp < 20" class="text-6xl font-bold">How cool your day?</h1>
    <h2 class="text-xl p-2">cheap temperature monitor for your home</h2>
    <div class="flex gap-3 lg:gap-5 flex-row justify-center">
        <div class="flex border flex-col p-1 lg:p-5 text-3xl">
            <p>Temperature</p>
            <p>{{temp}} C</p>
        </div>
        <div class="flex border flex-col p-1 lg:p-5 text-3xl">
            <p>Humidity</p>
            <p>{{humidity}} %</p>
        </div>
    </div>
</div>
</template>
