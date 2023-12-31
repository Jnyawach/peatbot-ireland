<script setup lang="ts">
import MainLayout from "./components/MainLayout.vue";
import MapsIntegration from "./components/maps-integration.vue";
import ImageModal from "./components/ImageModal.vue";
import TrialMap from "./components/trial-map.vue";
</script>

<template>
  <MainLayout>
  <div>
    <!--
    <MapsIntegration></MapsIntegration>
    -->
    <trial-map></trial-map>
    <div class="">
      <div class="p-3 bg-white shadow">
        <h1 class="text-2xl font-bold my-3">Legend</h1>
      </div>
    </div>
  </div>
    <section class="max-w-[1280px] p-5">

      <div class="grid md:grid-cols-2">
        <div>
          <h1 class="text-2xl font-bold my-3">Add some description</h1>
          <p class="text-sm leading-7">
            Herring Gulls are common across the continent and are often
            identified as the classic seagull. However, the Herring Gull is
            just one of some two dozen gull species that call North America home.
            As shoreline birds, Herring Gulls tend to stick near large water
            bodies where they’re close to their primary food source of marine
            invertebrates, fish, and insects. Being opportunistic predators,
            these birds also scavenge fish, carrion, trash,
            and of course, boldly snatch the occasional abandoned French fry.
          </p>
        </div>
        <div>
          <h1 class="text-2xl font-bold my-3">Chart title</h1>
        </div>
      </div>
      <div class="my-5 grid md:grid-cols-3 gap-2">
        <div class="h-60  overflow-hidden bg-no-repeat bg-cover"
             style="background-image: url('https://www.wwt.org.uk/uploads/images/2021-11-04/peat-1920x735.png')">
          <div class="grid h-full p-5 hover:bg-black/30  transition-colors duration-300">
            <div class="h-full w-full flex place-content-center group">
              <div class="self-center hidden group-hover:block">
                <ImageModal>
                  <template #trigger>
                    <button class="bg-white/50 py-3 px-5 outline outline-offset-2 outline-white/50">View details
                    </button>
                  </template>
                  <template #header>
                    <h1 class="text-2xl font-bold">Peatbog coverage</h1>
                  </template>
                  <div class="relative">
                    <img alt="Peatbog coverage"
                         src="https://www.wwt.org.uk/uploads/images/2021-11-04/peat-1920x735.png">
                    <div class="p-3 pt-8 absolute bottom-0 w-full bg-gradient-to-t from-black/80 from-70%">
                      <p class="text-sm text-white">
                        Herring Gulls are common across the continent and are often
                        identified as the classic seagull. However, the Herring Gull is
                        just one of some two dozen gull species that call North America home.
                        As shoreline birds, Herring Gulls tend to stick near large water
                        bodies where they’re close to their primary food source of marine
                        invertebrates, fish, and insects. Being opportunistic predators,
                        these birds also scavenge fish, carrion, trash,
                        and of course, boldly snatch the occasional abandoned French fry.
                      </p>
                    </div>
                  </div>
                </ImageModal>
              </div>
            </div>
          </div>
        </div>

        <div class="h-60 overflow-hidden bg-no-repeat bg-cover"
             style="background-image: url('https://www.wwt.org.uk/uploads/images/2021-11-04/peat-1920x735.png')">
          <div class="grid h-full p-5 hover:bg-black/30  transition-colors duration-300">
            <div class="h-full w-full flex place-content-center group">
              <div class="self-center hidden group-hover:block">
                <ImageModal>
                  <template #trigger>
                    <button class="bg-white/50 py-3 px-5 outline outline-offset-2 outline-white/50">View details
                    </button>
                  </template>
                  <template #header>
                    <h1 class="text-2xl font-bold">Peatbog coverage</h1>
                  </template>
                  <div class="relative">
                    <img alt="Peatbog coverage"
                         src="https://www.wwt.org.uk/uploads/images/2021-11-04/peat-1920x735.png">
                    <div class="p-3 pt-8 absolute bottom-0 w-full bg-gradient-to-t from-black/80 from-70%">
                      <p class="text-sm text-white">
                        Herring Gulls are common across the continent and are often
                        identified as the classic seagull. However, the Herring Gull is
                        just one of some two dozen gull species that call North America home.
                        As shoreline birds, Herring Gulls tend to stick near large water
                        bodies where they’re close to their primary food source of marine
                        invertebrates, fish, and insects. Being opportunistic predators,
                        these birds also scavenge fish, carrion, trash,
                        and of course, boldly snatch the occasional abandoned French fry.
                      </p>
                    </div>
                  </div>
                </ImageModal>
              </div>
            </div>
          </div>
        </div>

        <div class="h-60  overflow-hidden bg-no-repeat bg-cover"
             style="background-image: url('https://www.wwt.org.uk/uploads/images/2021-11-04/peat-1920x735.png')">
          <div class="grid h-full p-5 hover:bg-black/30  transition-colors duration-300">
            <div class="h-full w-full flex place-content-center group">
              <div class="self-center hidden group-hover:block">
                <ImageModal>
                  <template #trigger>
                    <button class="bg-white/50 py-3 px-5 outline outline-offset-2 outline-white/50">View details
                    </button>
                  </template>
                  <template #header>
                    <h1 class="text-2xl font-bold">Peatbog coverage</h1>
                  </template>
                  <div class="relative">
                    <img alt="Peatbog coverage"
                         src="https://www.wwt.org.uk/uploads/images/2021-11-04/peat-1920x735.png">
                    <div class="p-3 pt-8 absolute bottom-0 w-full bg-gradient-to-t from-black/80 from-70%">
                      <p class="text-sm text-white">
                        Herring Gulls are common across the continent and are often
                        identified as the classic seagull. However, the Herring Gull is
                        just one of some two dozen gull species that call North America home.
                        As shoreline birds, Herring Gulls tend to stick near large water
                        bodies where they’re close to their primary food source of marine
                        invertebrates, fish, and insects. Being opportunistic predators,
                        these birds also scavenge fish, carrion, trash,
                        and of course, boldly snatch the occasional abandoned French fry.
                      </p>
                    </div>
                  </div>
                </ImageModal>
              </div>
            </div>
          </div>
        </div>


      </div>
    </section>
  </MainLayout>
</template>

<style scoped>

</style>
