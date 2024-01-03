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
            <p class="font-medium text-blue-800">This study had 4 main objectives</p>
            <ol class="list-decimal pl-5 text-blue-800 space-y-3">
              <li>
                <span class="text-gray-900">
                  To conduct a site assessment of Clara bog to determine the past and
                current condition, and restoration initiatives
                </span>
              </li>
              <li>
                <span class="text-gray-900">
                  To detect changes over five decades using NDVI & NDWI Landsat 5,
                7 and Sentinel 2 satellite images and Support Vector machine, Random Forest & CART classification
                </span>
              </li>
              <li>
                <span class="text-gray-900">
                  To determine most accurate supervised classification algorithm for
                change detection utilizing evaluation metrics
                </span>
              </li>
              <li>
                <span class="text-gray-900">
                  Develop an interactive web-based peatland monitoring system for
                Clara bog and utilizing the best classification model.
                </span>
              </li>
            </ol>

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
      <div class="my-3 grid grid-cols-2">
       <div>
         <img src="@/assets/change-detection.png"  alt="Clara bog change detection">
       </div>
      </div>
    </section>
    <!--
    <section class="max-w-[1280px] p-5 mx-auto border-t border-black">
      <h2 class="font-bold my-3">References</h2>
      <ul class="text-sm space-y-2">
        <li>
          <p>
            <span class="font-bold">Review Google Earth Engine and Artificial Intelligence (AI):A Comprehensive Review</span> Liping
            Yang, Joshua Driscol 1,2, Sarigai Sarigai 1,2, Qiusheng Wu 4 , Haifei Chen 5 and Christopher D.
            Lippitt 1,2
          </p>
        </li>
        <li>
          <p>
            Purbahapsari, A. F., & Batoarung, I. B. (2022). <span class="font-bold">Geospatial Artificial Intelligence for Early Detection
            of Forest and Land Fires.</span> KnE Social Sciences. https://doi.org/10.18502/kss.v7i9.10947
          </p>
        </li>
        <li>
          <p>
            Czapiewski, S., & Szumińska, D. (2022). <span class="font-bold">An overview of remote sensing data applications in
            peatland research based on works from the period 2010–2021. In Land (Vol. 11, Issue 1).</span> MDPI.
          </p>
        </li>
        <li>
          <p>
            Chouinard, E. F.-. et al., 2023.<span class="font-bold"> Extensive global wetland loss over the past three centuries.</span> Nature,
            February, 614(281–286 (2023))
          </p>
        </li>
        <li>
          <p>
            Minasny, B., Berglund, Ö., Connolly, J.,. (2019). <span class="font-bold">Digital mapping of peatlands – A critical review.
            In Earth-Science Reviews</span> (Vol. 196). Elsevier B.V. https://doi.org/10.1016/j.earscirev.2019.05.014
          </p>
        </li>
        <li>
          <p>
            Connolly, J., 2018. <span class="font-bold">Mapping land use on Irish peatlands using medium resolution satellite imagery.
            Irish Geography</span>, Vol. 51, No. 2 November 2018(DOI: 10.2014/igj.v51i2.1371), pp. 1-2.
            FAO, 2020. Peatland mapping and monitoring. ISBN 978-92-5-132295-6 ed. s.l.:Food and Agriculture
            Organization of the United Nations.
          </p>
        </li>
      </ul>
    </section>
    -->
  </MainLayout>
</template>

<style scoped>

</style>
