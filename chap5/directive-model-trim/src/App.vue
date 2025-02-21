<script setup lang="ts">
import {ref} from "vue";

const trimmedText = ref("");
</script>

<template>
  <section>
    <input type="text" v-model.trim="trimmedText">
    <p>にゅうりょくもじれつ：{{ trimmedText }}</p>
  </section>
</template>

