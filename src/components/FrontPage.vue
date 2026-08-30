<script setup lang="ts">
import { ref } from 'vue';
let temp = ref("(loading)");
let humidity = ref("(loading)");
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
<h2>Temperature Monitor - esp32</h2>
<h2>cheap temperature monitor for your home</h2>
<h3>Temperature : {{temp}} C</h3>
<h3>Humidity: {{humidity}} %</h3>
</template>
