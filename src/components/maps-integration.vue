<script setup lang="ts">
import {onMounted, ref} from 'vue'
import "leaflet/dist/leaflet.css";
import L from "leaflet";
import geojson from "./data/Clara_1988.json";
const cart_1988=ref<any>()


const map=ref()
const mapContainer=ref()
const clara_1988=ref<any>(geojson)


const  setupLeafletMap=()=>{
 map.value = L.map(mapContainer.value).setView([53.322264, -7.631294], 13);
  L.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png', {
    maxZoom: 19,
    attribution: '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>'
  }).addTo(map.value);

}

onMounted(async ()=>{
  setupLeafletMap()
  await getData()
})

const getData= async ()=>{
  const response = await fetch('./data/Clara_1988.geojson');
  cart_1988.value = await response.json();
  L.geoJSON(clara_1988.value,{
    style: function(feature) {
      return {
        fillColor: 'red',
        weight: 1,
        opacity: 1,
        color: 'white',
        fillOpacity: 0.7
      };
    }
  }).addTo(map.value);
}
</script>

<template>
  <div id="map" class="w-full h-[90vh]" ref="mapContainer">
  </div>
</template>

<style scoped>

</style>