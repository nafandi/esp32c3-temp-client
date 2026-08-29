<script setup lang="ts">

//import { useFetch } from '@vueuse/core';
// todo : write implemtation of fetch
const url = "/api/";
async function fetchurl() {
  fetch(url).then(function (response) { return response.json() }).then(function (json) {
    console.log("humidity : " + json.humidity);
    console.log("temperature : " + json.temperature)
  })
}
</script>
<template>
<h1>Temperature Monitor - esp32</h1>
<h2>cheap temperature monitor for your home</h2>
<h3>Temperature : </h3>
<h3>Humidity: </h3>
<h2>Refresh</h2>
<fetchurl />
</template>
