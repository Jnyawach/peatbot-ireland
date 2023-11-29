<script setup lang="ts">
import {ref} from "vue";
const show = ref(false);
</script>

<template>
  <div @click="show=true">
    <slot name="trigger"></slot>
  </div>
  <teleport to="body">
    <Transition
        enter-from-class="opacity-0 scale-125"
        enter-to-class="opacity-100 scale-100"
        enter-active-class="transition duration-300"
        leave-active-class="transition duration-200"
        leave-from-class="opacity-100 scale-100"
        leave-to-class="opacity-0 scale-125"
    >
      <div @click.self="show=false" v-if="show" class="inset-0 fixed bg-black bg-opacity-70 z-[100000] grid place-items-center p-5">
        <div class="bg-white lg:w-2/3 w-full rounded-xl relative overflow-hidden">
          <header class="p-3 absolute w-full">
            <div class="flex justify-between">

              <slot name="header">

              </slot>
              <div>
                <div class="text-end">
                  <button type="button" @click="show=false" class="rounded-full bg-sumo-300 h-7 w-7 flex place-content-center">
                    <svg class="h-5 fill-white self-center" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 320 512"><path d="M312.1 375c9.369 9.369 9.369 24.57 0 33.94s-24.57 9.369-33.94 0L160 289.9l-119 119c-9.369 9.369-24.57 9.369-33.94 0s-9.369-24.57 0-33.94L126.1 256L7.027 136.1c-9.369-9.369-9.369-24.57 0-33.94s24.57-9.369 33.94 0L160 222.1l119-119c9.369-9.369 24.57-9.369 33.94 0s9.369 24.57 0 33.94L193.9 256L312.1 375z"/></svg>
                  </button>
                </div>
              </div>
            </div>

          </header>

          <div class="">
            <slot></slot>
          </div>

        </div>
      </div>
    </Transition>
  </teleport>
</template>

<style scoped>

</style>