<script setup lang="ts">
import "leaflet/dist/leaflet.css";
import { LMap, LTileLayer,LGeoJson,LControlScale } from "@vue-leaflet/vue-leaflet";
import { ref,onMounted } from "vue";


const zoom=ref(14)
const clara_1988=ref<any>({})
const clara_1995=ref<any>({})
const clara_2004=ref<any>({})
const clara_2009=ref<any>({})
const clara_2016=ref<any>({})
const clara_2023=ref<any>({})

const map_range=ref<Number>(1988)

//colors


onMounted(async()=>{
  const response = await fetch(`./data/Clara_1988.geojson`);
  clara_1988.value =  await response.json();
  const response2 = await fetch(`./data/Clara_1995.geojson`);
  clara_1995.value =  await response2.json();
  const response3 = await fetch(`./data/Clara_2004.geojson`);
  clara_2004.value =  await response3.json();
  const response4 = await fetch(`./data/Clara_2009.geojson`);
  clara_2009.value =  await response4.json();
  const response5 = await fetch(`./data/Clara_2016.geojson`);
  clara_2016.value =  await response5.json();
  const response6 = await fetch(`./data/Clara_2023.geojson`);
  clara_2023.value =  await response6.json();

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
  <div class="grid md:grid-cols-7">
    <div class="md:col-span-5">
      <div style="height:600px; width:100%">
        <l-map :use-global-leaflet="false" ref="map" v-model:zoom="zoom" :center="[53.322280, -7.631294]">
          <l-tile-layer
              url="https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png"
              layer-type="base"
              name="OpenStreetMap"
          ></l-tile-layer>

          <l-geo-json v-if="map_range==1988"  :geojson="clara_1988" :options-style="gridStyle"/>
          <l-geo-json v-if="map_range==1995"  :geojson="clara_1995" :options-style="gridStyle"/>
          <l-geo-json v-if="map_range==2004"  :geojson="clara_2004" :options-style="gridStyle"/>
          <l-geo-json v-if="map_range==2009"  :geojson="clara_2009" :options-style="gridStyle"/>
          <l-geo-json v-if="map_range==2016"  :geojson="clara_2016" :options-style="gridStyle"/>
          <l-geo-json v-if="map_range==2023"  :geojson="clara_2023" :options-style="gridStyle"/>
          <l-control-scale position="topright" :imperial="false" :metric="true"></l-control-scale>

        </l-map>
      </div>

    </div>
    <div class="md:col-span-2 p-2 px-3">
      <h1 class="text-lg font-bold my-2">Legend</h1>
      <div>
        <h6 class="text-blue-800 font-medium underline">Band 1: Classification (Gray)</h6>
        <ul class="my-5 border p-3 space-y-3">
          <li>
            <div class="flex justify-between items-center">
              <div class="flex gap-1 items-center">
                <input disabled type="color" class="w-7 h-7"  value="#59b9f4">
                <label class="font-medium">Active-Flush</label>
              </div>
            </div>
          </li>
          <li>
            <div class="flex justify-between items-center">
              <div class="flex gap-1 items-center">
                <input disabled type="color" class="w-7 h-7"  value="#c9074b">
                <label class="font-medium">Central</label>
              </div>
            </div>
          </li>
          <li>
            <div class="flex justify-between items-center">
              <div class="flex gap-1 items-center">
                <input disabled type="color" class="w-7 h-7"  value="#3aba55">
                <label class="font-medium">Sub-Central</label>
              </div>
            </div>
          </li>
          <li>
            <div class="flex justify-between items-center">
              <div class="flex gap-1 items-center">
                <input disabled type="color" class="w-7 h-7"  value="#bdaf35">
                <label class="font-medium">Sub-marginal</label>
              </div>
            </div>
          </li>
          <li>
            <div class="flex justify-between items-center">
              <div class="flex gap-1 items-center">
                <input disabled type="color" class="w-7 h-7"  value="#8a9856">
                <label class="font-medium">Marginal</label>
              </div>
            </div>
          </li>
          <li>
            <div class="flex justify-between items-center">
              <div class="flex gap-1 items-center">
                <input disabled type="color" class="w-7 h-7"  value="#b8abb2">
                <label class="font-medium">Other</label>
              </div>
            </div>
          </li>
        </ul>
        <div class="my-3 border p-2">
          <div class="flex items-center gap-1">
            <span class="text-white text-sm p-1 bg-gray-800 rounded-md">1988</span>
            <input  class="flex-grow h-1 border-0 bg-gray-800" type="range" min="1988" step="7" max="2023"   v-model="map_range">
            <span class="text-white text-sm p-1 bg-gray-800 rounded-md">2023</span>
          </div>
          <p class="my-2 font-bold text-center">Year: {{map_range}}</p>
        </div>
      </div>
    </div>
  </div>


</template>

<style scoped>
input[type=range] {
  -webkit-appearance: none;
  margin: 18px 0;
  width: 100%;
}
input[type=range]:focus {
  outline: none;
}
input[type=range]::-webkit-slider-runnable-track {
  width: 100%;
  height: 8.4px;
  cursor: pointer;
  box-shadow: 1px 1px 1px #000000, 0px 0px 1px #0d0d0d;
  background: #3071a9;
  border-radius: 1.3px;
  border: 0.2px solid #010101;
}
input[type=range]::-webkit-slider-thumb {
  box-shadow: 1px 1px 1px #000000, 0px 0px 1px #0d0d0d;
  border: 1px solid #000000;
  height: 36px;
  width: 16px;
  border-radius: 3px;
  background: #ffffff;
  cursor: pointer;
  -webkit-appearance: none;
  margin-top: -14px;
}
input[type=range]:focus::-webkit-slider-runnable-track {
  background: #367ebd;
}
input[type=range]::-moz-range-track {
  width: 100%;
  height: 8.4px;
  cursor: pointer;
  box-shadow: 1px 1px 1px #000000, 0px 0px 1px #0d0d0d;
  background: #3071a9;
  border-radius: 1.3px;
  border: 0.2px solid #010101;
}
input[type=range]::-moz-range-thumb {
  box-shadow: 1px 1px 1px #000000, 0px 0px 1px #0d0d0d;
  border: 1px solid #000000;
  height: 36px;
  width: 16px;
  border-radius: 3px;
  background: #ffffff;
  cursor: pointer;
}
input[type=range]::-ms-track {
  width: 100%;
  height: 8.4px;
  cursor: pointer;
  background: transparent;
  border-color: transparent;
  border-width: 16px 0;
  color: transparent;
}
input[type=range]::-ms-fill-lower {
  background: #2a6495;
  border: 0.2px solid #010101;
  border-radius: 2.6px;
  box-shadow: 1px 1px 1px #000000, 0px 0px 1px #0d0d0d;
}
input[type=range]::-ms-fill-upper {
  background: #3071a9;
  border: 0.2px solid #010101;
  border-radius: 2.6px;
  box-shadow: 1px 1px 1px #000000, 0px 0px 1px #0d0d0d;
}
input[type=range]::-ms-thumb {
  box-shadow: 1px 1px 1px #000000, 0px 0px 1px #0d0d0d;
  border: 1px solid #000000;
  height: 36px;
  width: 16px;
  border-radius: 3px;
  background: #ffffff;
  cursor: pointer;
}
input[type=range]:focus::-ms-fill-lower {
  background: #3071a9;
}
input[type=range]:focus::-ms-fill-upper {
  background: #367ebd;
}
</style>