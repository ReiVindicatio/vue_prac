<script setup lang="ts">
import {ref, watch} from "vue";

const cocktailNo = ref(1);
const priceMsg = ref("");
watch(cocktailNo,
  (newVal: number, oldVal: number): void => {
    let msg = "prev cocktail: ";
    msg += getCocktailInfo(oldVal);
    msg += "\n now cocktail: ";
    msg += getCocktailInfo(newVal);
    priceMsg.value =msg;
  }
);

function getCocktailInfo(cocktailNo: number): string {
  const cocktailDataListInit = new Map<number, Cocktail>();
  cocktailDataListInit.set(1, {id: 1, name: "white lady", price: 1200});
  cocktailDataListInit.set(2, {id: 2, name: "blue hawaii", price: 1500});
  cocktailDataListInit.set(3, {id: 3, name: "new york", price: 1100});
  cocktailDataListInit.set(4, {id: 4, name: "martini", price: 1500});
  const cocktail = cocktailDataListInit.get(cocktailNo);
  let msg = "Cocktail not found.";
  if (cocktail != undefined) {
    msg = `The price of ${cocktail.name} is ${cocktail.price}.`;
  }
  return msg;
}

setInterval(
  (): void => {
    cocktailNo.value = Math.round(Math.random() * 3) + 1;
  }
, 1000);
interface Cocktail {
  id: number;
  name: string;
  price: number;
};

</script>

<template>
  <p>Cocktail Number: {{ cocktailNo }}</p>
  <p>{{ priceMsg }}</p>
</template>
