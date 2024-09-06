<template>
 <Suspense>
  <template #default>
    <component :is="HomeFlowComponent" />
  </template>
  <template #fallback>
    <splashscreen/>
  </template>
 </Suspense>
</template>

<script setup>

import splashscreen from './components/SplashScreen.vue';
import { defineAsyncComponent } from 'vue';


const HomeFlowComponent = defineAsyncComponent(()=>
  new Promise((resolve) => {
    setTimeout(()=>{
      resolve(import("./components/HomeFlow.vue"));
    }, 2500);
  }));




</script>

<style>
Html,
body,
.app{
  min-height: 100vh;
  margin: 0;
  font-family: Arial, Helvetica, sans-serif;
}

* {
  --brand-green:#04b500;
  --brand-blue:#0689b0;
}
</style>
