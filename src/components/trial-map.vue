<script setup lang="ts">
import "leaflet/dist/leaflet.css";
import { LMap, LTileLayer,LGeoJson } from "@vue-leaflet/vue-leaflet";
import { ref,onMounted } from "vue";


const zoom=ref(14)
const clara_1988=ref<any>('')
const clara_1995=ref('')
const clara_2004=ref('')
const clara_2013=ref('')

//colors

const map_layers=ref([
  {
    name:'1988',
    layer:'Clara_1988',
    color:'#ef4444',
    data:'',
    visibility:true,
    optionsStyle:{
      "color": "#ef4444",
      "weight": 0,
      "fillColor": "#ef4444",
      "fillOpacity": 0.5

    }
  },
  {
    name:'1995',
    layer:'Clara_1995',
    color:'#f97316',
    data:'',
    visibility:false,
    optionsStyle:{
      "color": "#f97316",
      "weight": 0,
      "fillColor": "#f97316",
      "fillOpacity": 0.35

    }
  },
  {
    name:'2004',
    layer:'Clara_2004',
    color:'#f59e0b',
    data:'',
    visibility:false,
    optionsStyle:{
      "color": "#f59e0b",
      "weight": 0,
      "fillColor": "#f59e0b",
      "fillOpacity": 0.35

    }
  },
  {
    name:'2016',
    layer:'Clara_2016',
    color:'#eab308',
    data:'',
    visibility:false,
    optionsStyle:{
      "color": "#eab308",
      "weight": 0,
      "fillColor": "#eab308",
      "fillOpacity": 0.35

    }
  },
  {
    name:'2023',
    layer:'Clara_2023',
    color:'#84cc16',
    data:'',
    visibility:false,
    optionsStyle:{
      "color": "#84cc16",
      "weight": 0,
      "fillColor": "#84cc16",
      "fillOpacity": 0.35

    }
  }
])
onMounted(async()=>{
  const response = await fetch(`./data/Clara_1988.geojson`);
  clara_1988.value =  await response.json();
  /*
  map_layers.value.forEach(async (layer)=>{
    const response = await fetch(`./data/${layer.layer}.geojson`);
    layer.data =  await response.json();
  })

   */

})

const gridStyle=(feature)=>{
  return {
    fillColor: getColor(feature.properties.gridcode),
    weight: 0,
    opacity: 1,
    color: 'white',
    fillOpacity: 0.7
  };
}
function getColor(d:number) {
  return d === 1 ? '#ff0000' :
      d === 2 ? '#00ff00' :
          d === 3 ? '#0000ff' :
              d ===4 ? '#ff00ff' :
                  d ===5 ? '#ffff00' :
                      d ===6 ? '#00ffff' :
              '#808080';
}
</script>

<template>
  <div class="grid md:grid-cols-7">
    <div class="md:col-span-5">
      <div style="height:600px; width:100%">
        <l-map ref="map" v-model:zoom="zoom" :center="[53.322264, -7.631294]">
          <l-tile-layer
              url="https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png"
              layer-type="base"
              name="OpenStreetMap"
          ></l-tile-layer>
          <l-geo-json  :geojson="clara_1988" :options-style="gridStyle"/>
        </l-map>
      </div>

    </div>
    <div class="md:col-span-2 p-2 px-3">
      <h1 class="text-lg font-bold my-2">Legend</h1>
      <div>
        <h6 class="text-blue-800 font-medium underline">Peat-bog coverage change 1988-2023</h6>
        <ul class="my-5 border p-3 space-y-3">
          <li v-for="layer in map_layers" :key="layer.name">
            <div class="flex justify-between items-center">
              <div class="flex gap-1 items-center">
                <input type="color" class="w-7 h-7"  :value="layer.color">
                <label class="font-medium">Year {{layer.name}}</label>
              </div>
              <div>
                <input @input="$emit('update:visible')" type="checkbox" class="h-5 w-5 rounded-none" v-model="layer.visibility">
              </div>

            </div>
          </li>
        </ul>
      </div>
    </div>
  </div>


</template>

<style scoped>

</style>