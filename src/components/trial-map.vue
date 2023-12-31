<script setup lang="ts">
import "leaflet/dist/leaflet.css";
import { LMap, LTileLayer,LGeoJson } from "@vue-leaflet/vue-leaflet";
import { ref,onMounted } from "vue";
import CartClassification1988 from "./data/CART_Classification_2016.geojson";

const zoom=ref(8)
const cart_1988=ref<any>()
const options={

}
const styleFunction=()=>{
  return {

  }
}
onMounted(()=>{
  cart_1988.value=CartClassification1988
})

</script>

<template>
  <div style="height:600px; width:100%">
    <l-map ref="map" v-model:zoom="zoom" :center="[-1.242699, 36.766670]">
      <l-tile-layer
          url="https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png"
          layer-type="base"
          name="OpenStreetMap"
      ></l-tile-layer>
      <l-geo-json
          :geojson="cart_1988"
          :options="options"
          :options-style="styleFunction"
      />
    </l-map>
  </div>
</template>

<style scoped>

</style>