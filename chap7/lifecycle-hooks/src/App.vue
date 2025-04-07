<script setup lang="ts">
import {ref, computed, onBeforeMount, onMounted, onBeforeUpdate, onUpdated, onRenderTracked, onRenderTriggered} from "vue";
import type {DebuggerEvent} from "vue";

const heightInit = Math.round(Math.random() * 10);
const widthInit = Math.round(Math.random() * 10);
const height = ref(heightInit);
const width = ref(widthInit);

const area = computed(
  (): number => {
    return height.value * width.value;
  }
);
const change = (): void => {
  height.value = Math.round(Math.random() * 10);
  width.value = Math.round(Math.random() * 10);
}
onBeforeMount(
  (): void => {
    console.log(`beforeMount called: ${height.value} * ${width.value}`);
  }
);
onMounted(
  (): void => {
    console.log(`mounted called: ${height.value} * ${width.value}`);
  }
);
onBeforeUpdate(
  (): void => {
    console.log(`beforeUpdate called: ${height.value} * ${width.value}`);
  }
);
onUpdated(
  (): void => {
    console.log(`updated called: ${height.value} * ${width.value}`);
  }
);
onRenderTracked(
  (event: DebuggerEvent): void => {
    console.log(`renderTriggerd called: ${height.value} * ${width.value}`);
    console.log(event);
  }
);
</script>

<template>
  <p>height: {{ height }}, width: {{ width }}, area: {{ area }}</p>
  <button v-on:click="change">change value</button>
</template>
