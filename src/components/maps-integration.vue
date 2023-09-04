<script setup lang="ts">
import {Loader} from "@googlemaps/js-api-loader"
import ee from "@google/earthengine"
import {onMounted, ref, watch} from "vue";
import { useGeolocation } from '@vueuse/core'
import {debounce} from 'lodash';


const {coords}=useGeolocation()
const loader=new  Loader({libraries:['places','marker'],apiKey:import.meta.env.VITE_GOOGLE_MAP_KEY})
let map=ref()
let mapContainer=ref()

//places search and suggestion
const searchSuggestions=ref()
const searchBox=ref()
const searchInput=ref()
const showSuggestions=ref(false)
const clientId = import.meta.env.VITE_CLIENT_ID;

onMounted( ()=>{

  ee.data.authenticateViaOauth(clientId, initialize, function(e) {
    console.error('Authentication error: ' + e);
  }, null, function() {
    ee.data.authenticateViaPopup(initialize);
  })
  ee.initialize();

})

var initialize = function() {
  ee.initialize(null, null, function() {
    // ... run analysis ...
  }, function(e) {
    console.error('Initialization error: ' + e);
  });
};

const setUpMap=  ()=>{
  ee.initialize();
  //load map
  loader.load()
  map.value = new google.maps.Map(mapContainer.value,{
    center:{lat:coords.value.latitude,lng:coords.value.longitude },
    zoom:12
  })
  const srtm = ee.Image("CGIAR/SRTM90_V4");
  const slope = ee.Terrain.slope(srtm);

  // Create a new tile source to fetch visible tiles on demand and display them
  // on the map.
  const mapId = slope.getMap({min: 0, max: 60});
  const tileSource = new ee.layers.EarthEngineTileSource(mapId);
  const overlay = new ee.layers.ImageOverlay(tileSource);
  embeddedMap.overlayMapTypes.push(overlay);


}
watch(searchInput, debounce(function () {
  showSuggestions.value=true
  handleSearchInput()

}, 300))

const handleSearchInput=()=>{
  searchSuggestions.value=[]
  if (!searchInput.value.trim)return;
  const searchOptions = {
    fields: ["formatted_address",  "name","place_id"],
    strictBounds: false,
  };
  const autocompleteService = new google.maps.places.AutocompleteService();

  autocompleteService.getQueryPredictions({ input: searchInput.value}, getPredictions);
}

const setNewLocation=(lat:number,lng:number)=>{
  searchMarker.value.setPosition(new google.maps.LatLng(lat,lng));
}


const getPredictions=(predictions: google.maps.places.QueryAutocompletePrediction[] | null,
                      status: google.maps.places.PlacesServiceStatus)=>{
  if (status != google.maps.places.PlacesServiceStatus.OK || !predictions) {
    alert(status);
    return;
  }
  searchSuggestions.value=predictions
}

const selectSuggestion = (suggestion:any) => {
  const placeService = new google.maps.places.PlacesService(map.value);

  placeService.getDetails({ placeId: suggestion.place_id }, (place, status) => {
    if (status === google.maps.places.PlacesServiceStatus.OK) {
      const location = place.geometry.location;
      const latLng = new google.maps.LatLng(location.lat(), location.lng());
      map.value.setCenter(latLng);

    }
  });

  showSuggestions.value = false;
};

//initialize EE



function onSignInButtonClick() {

  ee.data.authenticateViaOauth(clientId, initialize, function(e) {
    console.error('Authentication error: ' + e);
  }, null, function() {
    ee.data.authenticateViaPopup(initialize);
  })
 
}
</script>

<template>
<div class="grid grid-cols-7 h-screen">
  <div class="bg-white col-span-2">
    <div>
      <div class="border-b p-3 shadow">
        <h1 class="text-center font-bold">GIS Analysis</h1>
      </div>
      <div class="grid grid-cols-2">
        <div>
          <button class="px-3 h-full w-full border py-2 hover:bg-sky-600 hover:text-white">NDWI Analysis</button>
        </div>
        <div>
          <button class="px-3 h-full w-full border py-2 hover:bg-sky-600 hover:text-white">NDVI Analysis</button>
        </div>
      </div>
    </div>

    <div>
      <input
          id="g-sign-in"
          type="image"
          src="https://developers.google.com/identity/images/btn_google_signin_light_normal_web.png"
          @click="onSignInButtonClick()"
          alt="Sign in with Google"
      />
    </div>
  </div>
  <div class="col-span-5">
    <div class="relative">
      <div class="p-2 flex">
        <input type="search"  id="pac-input" v-model="searchInput"
               class="controls h-10 rounded-l-xl border border-gray-100 w-full  px-2" placeholder="Search for places">
        <button class="border bg-gray-100 rounded-r-xl px-3">
          <svg class="h-4 fill-sumo-300" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><path d="M504.1 471l-134-134C399.1 301.5 415.1 256.8 415.1 208c0-114.9-93.13-208-208-208S-.0002 93.13-.0002 208S93.12 416 207.1 416c48.79 0 93.55-16.91 129-45.04l134 134C475.7 509.7 481.9 512 488 512s12.28-2.344 16.97-7.031C514.3 495.6 514.3 480.4 504.1 471zM48 208c0-88.22 71.78-160 160-160s160 71.78 160 160s-71.78 160-160 160S48 296.2 48 208z"/></svg>
        </button>

      </div>
      <div class="relative px-2 w-full">
        <div v-if="showSuggestions" class="absolute bg-gray-100 z-50  rounded-xl border shadow w-[calc(100%-2rem)]">
          <ul class="divide-y">
            <li class="p-2 hover:bg-sumo-500/40 hover:text-sumo-300 font-medium" v-for="suggestion in searchSuggestions">
              <button type="button" @click="selectSuggestion(suggestion)" class="w-full text-start ">{{suggestion.description}}</button>
            </li>
          </ul>
        </div>
      </div>
    </div>
    <div class=" overflow-hidden"   ref="mapContainer" id="map" style="width: 100%; height: 100%"></div>
  </div>
</div>
</template>

<style scoped>

</style>