<script setup lang="ts">
import MainLayout from "@/components/MainLayout.vue";
import TrialMap from "@/components/trial-map.vue";
import Classify from "@/components/Classify.vue";
import ClassifyLegend from "@/components/ClassifyLegend.vue";

</script>

<template>
  <MainLayout>
    <div>
      <trial-map></trial-map>
    </div>


    <section class="max-w-[1280px] p-5 mx-auto">
      <p class="text-sm leading-7">
        Clara bog is one of the largest raised bogs in Ireland located in County Offlay. Only two thirds of the bog remain, with a third
        having been degraded to peat extraction. It covers around 840 hectares of which 443.36ha is uncut high bog while 393.18ha mostly cutover bog. Initially the bog was a dome shaped but currently
        two dome shapes. The construction of the Clara to Rahan road lead to its subsidence by 6 metres.
      </p>
      <div class="my-5">
        <div class="grid grid-cols-2  border">
          <div class="grid">
            <img src="@/assets/Clara_bog.png" alt="Clara Bog" class="w-full">
          </div>
          <div class="grid">
            <img src="@/assets/clara_change.png" alt="Clara Bog" class="w-full h-full">
          </div>

        </div>
        <p class="text-sm mt-3">
          Source: <a target="_blank" href="https://www.raisedbogs.ie/life-project/" class="underline text-blue-800">https://www.raisedbogs.ie/life-project/</a>
          Transformation of Clara bog between 1809 and 2006
        </p>
      </div>

      <div class="my-5">
        <p class="my-3">
          Peatlands are yet to be documented spatially with a high level of detail for simulation of the earth’s system. There have been
          recommendations for effective monitoring, FAO report 2020, policy documents and global wetland loss over 3 decades.
          Significant for decision making and mitigation of climate change impacts
        </p>
        <div class="grid grid-cols-2 my-3">
          <div>
            <p class="leading-relaxed">
              Landsat 5 and Landsat 8 satellite imagery spanning from 1988, 1995, 2004, 2009, 2016 and 2023 is acquired using the
              Google Earth engine. Training and validation datasets were established utilising field data from NPWS Ecotope surveys
              conducted in 2005, 2009 and 2016; providing ground truth information of different Ecotope types NDVI and NDWI images are
              then generated from the Landsat data to assess vegetation and water content over time. NDVI quantifies vegetation health and
              density while NDWI indicates water content.
              Two machine learning algorithms are evaluated; Random Forest (RF) and Support Vector Machine (SVM) classify the
              peatland cover types and distinguish between various vegetation and land cover classes. The accuracy of the classification
              models is evaluated using metrics such as Kappa, overall accuracy, and Producer accuracy. Using Python programming,
              Python-based prediction models are developed to forecast trends based on historical data as well as change detection
              models that identify alterations in the peatland landscape. To enhance accessibility and visualisation, an analysis app
              within GEE and a dedicated monitoring website are developed, providing interactive tools for stakeholders.
            </p>

          </div>
          <div class="grid  gap-3">
            <img src="@/assets/problem_statement.png" alt="Problem statement" class="w-full ">
          </div>

        </div>

      </div>

    </section>
    <section class="max-w-[1280px] p-5 mx-auto">
      <h2 class="text-lg font-bold text-center my-3">Random Forest supervised classification</h2>
      <div class="my-5 grid grid-cols-3 gap-2">
        <div>
          <Classify year="1988" data-link="./data/Clara_1988.geojson"></Classify>
        </div>
        <div>
          <Classify year="1995" data-link="./data/Clara_1995.geojson"></Classify>
        </div>
        <div>
          <Classify year="2004" data-link="./data/Clara_2004.geojson"></Classify>
        </div>
        <div>
          <Classify year="2009" data-link="./data/Clara_2009.geojson"></Classify>
        </div>
        <div>
          <Classify year="2016" data-link="./data/Clara_2016.geojson"></Classify>
        </div>
        <div>
          <Classify year="2023" data-link="./data/Clara_2023.geojson"></Classify>
        </div>
      </div>
      <div class="my-3">
        <ClassifyLegend></ClassifyLegend>
      </div>
      <div class="my-3 grid grid-cols-2 gap-2">
        <div>
          <p class="leading-relaxed">
            Random Forest Classification was determined as the best-supervised classification with an overall accuracy of
            82% for 2004 and 82% for 2016. Active flush areas showed slight growth until 2004, stayed steady until 2016, then
            experienced a significant increase, possibly indicating the ongoing restoration efforts. Conversely, submarginal zones
            rose until 2004 but steadily declined afterward, likely due to drainage or peat extraction impacting these regions
            negatively. Marginal and subcentral areas consistently decreased, potentially signifying ongoing habitat loss.
            Re-wetting and revegetation initiatives could be attributed to the positive trends observed, especially in active
            flush zones. However, factors like drainage,
            peat extraction, and climate shifts might have contributed to degradation in the marginal submarginal areas. </p>
        </div>
       <div>
         <img src="@/assets/change-detection.png"  alt="Clara bog change detection">
       </div>
      </div>
    </section>

  </MainLayout>
</template>

<style scoped>

</style>
