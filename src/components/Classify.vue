<script setup lang="ts">
import "leaflet/dist/leaflet.css";
import { LMap, LGeoJson,LControlScale } from "@vue-leaflet/vue-leaflet";
import { ref,onMounted } from "vue";
let props=defineProps({
  year:String,
  dataLink:{
    type:String,
    required:true
  }
})
const zoom=ref(13)

const clara_1988=ref<any>({})
onMounted(async()=>{
  const response = await fetch(props.dataLink);
  clara_1988.value =  await response.json();


})

const gridStyle=(feature:any)=>{
  return {
    fillColor: getColor(feature.properties.gridcode),
    weight: 0,
    opacity: 1,
    color: 'white',
    fillOpacity: 1
  };
}
function getColor(d:number) {
  return d === 1 ? '#59b9f4' :
      d === 2 ? '#c9074b' :
          d === 3 ? '#3aba55' :
              d ===4 ? '#bdaf35' :
                  d ===5 ? '#8a9856' :
                      '#b8abb2';
}
</script>

<template>
  <div style="height:400px; width:100%" class="border relative">
  <l-map :use-global-leaflet="false" ref="map" v-model:zoom="zoom" :center="[53.322280, -7.6280]">
    <!--
    <l-tile-layer
        url="https://tiles.stadiamaps.com/tiles/stamen_toner/{z}/{x}/{y}{r}.png"
        layer-type="base"
        name="OpenMapTiles"

    ></l-tile-layer>
    -->
  <l-geo-json   :geojson="clara_1988" :options-style="gridStyle"/>
    <l-control-scale position="topright" :imperial="false" :metric="true"></l-control-scale>
  </l-map>
    <div class="bg-blue-100 shadow border py-1 px-5  absolute bottom-5 left-2 z-[100000]">
     <span class="text-xs font-bold text-blue-800"> {{year}}</span>
    </div>
  </div>
</template>

<style scoped>

</style>