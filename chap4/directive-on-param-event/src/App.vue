<script setup lang="ts">
import {ref} from "vue";

const mousePointerX = ref(0);
const mousePointerY = ref(0);
const OnImgMousemove = (event: MouseEvnet): void => {
  mousePointerX.value = event.offsetX;
  mousePointerY.value = event.offsetY;
};
</script>

<template>
  <section>
    <img src="./assets/logo.svg" alt="Vueのロゴ" width="200" v-on:mousemove="OnImgMousemove">
    <p>ポインタの位置： x={{ mousePointerX }}; y={{ mousePointerY }}</p>
  </section>
</template>

