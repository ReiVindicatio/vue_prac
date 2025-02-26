<script setup lang="ts">
import {ref, computed} from "vue";

const cocktailDataListInit = new Map<number, Cocktail>();
cocktailDataListInit.set(2345, {id: 2345, name: "white lady", price: 1200});
cocktailDataListInit.set(4412, {id: 4412, name: "blue hawaii", price: 1200});
cocktailDataListInit.set(6792, {id: 6792, name: "new york", price: 1500});
cocktailDataListInit.set(8429, {id: 8429, name: "martini", price: 1200});
const cocktailDataList = ref(cocktailDataListInit);
const cocktail1500 = computed(
  (): Map<number, Cocktail> => {
    const newList = new Map<number, Cocktail>();
    cocktailDataList.value.forEach(
      (value: Cocktail, ley: number): void => {
        if (value.price == 1500) {
          newList.set(ley, value);
        }
      }
    );
    return newList;
  }
);

const changeWhiteLadyPriceInList = (): void => {
  const whiteLady = cocktailDataList.value.get(2345) as Cocktail;
  if (whiteLady.price != 1500) {
    whiteLady.price = 1500;
  } else {
    whiteLady.price = 1200;
  }
}

interface Cocktail {
  id: number;
  name: string;
  price: number;
};
</script>

<template>
  <section>
    <ul>
      <li v-for="[id, cocktailItem] in cocktailDataList" v-bind:key="id">{{ cocktailItem.name }}の値段は{{ cocktailItem.price }}</li>
    </ul>
  </section>
  <section>
    値段が1500円のカクテルリスト
    <ul>
      <li v-for="[id, cocktailItem] in cocktail1500" v-bind:key="'cocktail1500' + id">{{ cocktailItem.name }}の値段は{{ cocktailItem.price }}</li>
    </ul>
  </section>
  <p>
    CocktailDataList内のwhite ladyの価格を変更
    <button v-on:click="changeWhiteLadyPriceInList">変更</button>
  </p>
</template>
