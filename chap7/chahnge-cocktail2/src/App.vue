<script lang="ts">
import {ref, computed, defineComponent} from "vue";

export default defineComponent({
  name: "App",
  setup() {
    const cocktailDataInit = new Map<number, Cocktail>();
    cocktailDataInit.set(1, {id: 1, name: "white lady", price: 1200});
    cocktailDataInit.set(2, {id: 2, name: "blue hawaii", price: 1500});
    cocktailDataInit.set(3, {id: 3, name: "new york", price: 1100});
    cocktailDataInit.set(4, {id: 4, name: "martini", price: 1500});
    const cocktailNo = ref(1);
    const priceMsg = computed(
      (): string => {
        const cocktail = cocktailDataInit.get(cocktailNo.value);
        let msg = "Cocktail not found.";
        if (cocktail != undefined) {
          msg = `The price of ${cocktail.name} is ${cocktail.price}.`;
        }
        return msg;
      }
    );
    setInterval(
      (): void => {
        cocktailNo.value = Math.round(Math.random() * 3) + 1;
      }
    , 1000);
    return {
      cocktailNo,
      priceMsg,
    }
  }
});

interface Cocktail {
  id: number;
  name: string;
  price: number;
};
</script>

<template>
  <p>CocktailNo: {{ cocktailNo }}</p>
  <p>{{ priceMsg }}</p>
</template>

