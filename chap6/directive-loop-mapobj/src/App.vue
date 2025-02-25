<script setup lang="ts">
import {ref} from "vue";

const cocktailDataListInit = new Map<number, Cocktail>();
cocktailDataListInit.set(2345, {id: 2345, name: "white lady", price: 1200});
cocktailDataListInit.set(4412, {id: 4412, name: "blue hawaii", price: 1200});
cocktailDataListInit.set(6792, {id: 6792, name: "new york", price: 1200});
cocktailDataListInit.set(8429, {id: 8429, name: "martini", price: 1200});
const cocktailDataList = ref(cocktailDataListInit);

interface Cocktail {
  id: number;
  name: string;
  price: number;
};
</script>

<template>
  <ul>
    <li v-for="[id, cocktailItem] in cocktailDataList" v-bind:key="id">{{ cocktailItem.name }}の値段は{{ cocktailItem.price }}</li>
  </ul>
</template>
