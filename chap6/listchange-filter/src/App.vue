<script setup lang="ts">
import {ref, computed} from "vue";

const cocktailDataListInit: Cocktail[] = [
  {id: 1, name: 'Margarita', price: 1200},
  {id: 2, name: 'Mojito', price: 1500},
  {id: 3, name: 'Sunset', price: 1100},
  {id: 3, name: 'Martini', price: 1500}
];
const cocktailDataList = ref(cocktailDataListInit);
const cocktail1500 = computed(
  (): Cocktail[] => {
    const newList = cocktailDataList.value.filter(
      (cocktailItem: Cocktail): boolean => {
        return cocktailItem.price == 1500;
      }
    );
    return newList;
  }
);

interface Cocktail {
  id: number;
  name: string;
  price: number;
};
</script>

<template>
  <section>
    全てのカクテルリスト
    <ul>
      <li v-for="cocktailItem in cocktailDataList" v-bind:key="cocktailItem.id">{{ cocktailItem.name }}の値段は{{ cocktailItem.price }}</li>
    </ul>
  </section>
  <section>
    値段が1500円のカクテルリスト
    <ul>
      <li v-for="cocktailItem in cocktail1500" v-bind:key="'cocktail1500' + cocktailItem.id">{{ cocktailItem.name }}の値段は{{ cocktailItem.price }}円</li>
    </ul>
  </section>
</template>
