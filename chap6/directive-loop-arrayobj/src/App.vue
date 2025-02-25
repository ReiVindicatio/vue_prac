<script setup lang="ts">
import {ref} from "vue";

const cocktailDataListInit: Cocktail[] = [
  {id: 2345, name: "white lady", price: 1200},
  {id: 4412, name: "blue hawaii", price: 1500},
  {id: 6792, name: "new york", price: 1100},
  {id: 8492, name: "martini", price: 1500}
];
const cockatilDataList = ref(cocktailDataListInit);

interface Cocktail {
  id: number;
  name: string;
  price: number;
};
</script>

<template>
  <ul>
    <li v-for="cocktailItem in cockatilDataList" v-bind:key="cocktailItem.id">{{ cocktailItem.name }}の値段は{{ cocktailItem.price }}</li>
  </ul>
</template>
