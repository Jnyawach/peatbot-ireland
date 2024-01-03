<script setup lang="ts">

</script>

<template>
  <div class="p-2 px-3">
    <h1 class="text-lg font-bold my-2">Legend</h1>
    <div>
      <h6 class="text-blue-800 font-medium underline">Band 1: Classification (Gray)</h6>
      <ul class=" my-2 p-3 border  flex flex-wrap items-center gap-3">
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

    </div>
  </div>
</template>

<style scoped>

</style>