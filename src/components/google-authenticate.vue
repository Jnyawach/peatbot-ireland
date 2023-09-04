<script setup lang="ts">
import {useStorage} from "@vueuse/core";
const cred=useStorage('cred',{})
const callback=(response)=>{
cred.value=response
}
</script>

<template>
  <GoogleLogin :callback="callback"/>
</template>

<style scoped>

</style>