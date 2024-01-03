<script setup lang="ts">

</script>

<template>
  <div class="border-b p-2 py-3">
   <div class="flex justify-between">
     <div>
       <h1 class="text-md font-bold">Web-based Peatland Spatial-temporal & Restoration Monitoring System (Clara bog)</h1>
     </div>
     <div class="flex items-center gap-2">
       <!--
      <div>
        <ul class="flex gap-2 items-center">
          <li>Link 1</li>
          <li>Link 1</li>
        </ul>
      </div>
      -->
      <div>
        <svg class="h-5 w-5"  viewBox="0 0 16 16" aria-hidden="false">
          <path d="M11 7V6h3v9H3V6h3v1H4v7h9V7zM6.74 4L8 2.739V11h1V2.705L10.295 4l.324.324.707-.707L8.517.807l-2.809 2.81.707.707z" class="jsx-3680692050"></path>
        </svg>
      </div>
     </div>
   </div>
  </div>
  <div>
    <slot />
  </div>
</template>

<style scoped>

</style>