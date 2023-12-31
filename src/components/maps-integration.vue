<script setup lang="ts">
import {onMounted, ref} from 'vue'
import "leaflet/dist/leaflet.css";
import L from "leaflet";
import geojson from "./data/CART_Classification_1988.geojson";
const cart_1988=ref<any>()


const map=ref()
const mapContainer=ref()


const  setupLeafletMap=()=>{
 map.value = L.map(mapContainer.value).setView([-1.242699, 36.766670], 13);
  L.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png', {
    maxZoom: 19,
    attribution: '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>'
  }).addTo(map.value);

}

onMounted(async ()=>{
  await getData()
  setupLeafletMap()
  L.geoJSON(geojson).addTo(map.value);
})

const getData= async ()=>{
  const response = await fetch('./data/CART_Classification_1988.geojson')
  cart_1988.value =  response.json();
  console.log(cart_1988.value)
}
</script>

<template>
  <div id="map" class="w-full h-[90vh]" ref="mapContainer">
  </div>
</template>

<style scoped>

</style>