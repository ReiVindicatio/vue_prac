<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: "App",
  data() {
    return {
      height: Math.round(Math.random() * 10),
      width: Math.round(Math.random() * 10)
    }
  },
  computed: {
    area(): number {
      return this.height * this.width;
    }
  },
  methods: {
    change(): void {
      this.height = Math.round(Math.random() * 10);
      this.width = Math.round(Math.random() * 10);
    }
  }
});
</script>

<template>
  <p>height: {{ height }}, width: {{ width }}, area: {{ area }}</p>
  <button v-on:click="change">change value</button>
</template>
