<script setup lang="ts">
import {ref} from "vue";
import OneInfo from "./components/OneInfo.vue";

const weatherListInit = new Map<number, Weather>();
weatherListInit.set(1, {id: 1, title: "Today's weather", content: "Today's weather is sunny."});
weatherListInit.set(2, {id: 2, title: "Tomorrow's weather", content: "Tomorrow's weather is rainy."});
weatherListInit.set(3, {id: 3, title: "Day after Tomorrow's weather", content: "Day after Tomorrow's weather is snowy."});
const weatherList = ref(weatherListInit)

interface Weather {
  id: number;
  title: string;
  content: string;
}
</script>

<template>
  <h1>Props basic</h1>
  <section>
    <h2>generate components with loop</h2>
    <OneInfo 
      v-for="[id, weather] in weatherList" 
      v-bind:key="id" 
      v-bind:title="weather.title" 
      v-bind:content="weather.content"/>
  </section>
</template>

