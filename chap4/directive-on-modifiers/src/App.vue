<script setup lang="ts">
import {ref} from "vue";

const msg = ref("still");
const onEnterKey = (): void => {
  msg.value = "Enter key pressed";
};
const onRightButtonClick = (): void => {
  msg.value = "Right button clicked";
};
const onShiftClick = (): void => {
  msg.value = "Shift key clicked";
};
</script>

<template>
  <p>{{ msg }}</p>
  <input type="text" v-on:keydown.enter="onEnterKey"><br>
  <button v-on:click.right="onRightButtonClick">右クリック</button>
  <button v-on:click.shift="onShiftClick">シフトを押しながらクリック</button>
</template>