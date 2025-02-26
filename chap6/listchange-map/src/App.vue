<script setup lang="ts">
import {ref} from "vue";

const cocktailListInit = new Map<number, string>();
cocktailListInit.set(2345, "white lady");
cocktailListInit.set(4412, "blue hawaii");
cocktailListInit.set(6792, "new york");
const cocktailList = ref(cocktailListInit);
const changeCocktailList = (): void => {
  cocktailList.value.clear();
  cocktailList.value.set(3416, "martini");
  cocktailList.value.set(5517, "xyz");
  cocktailList.value.set(7415, "manhattan");
};
const addCocktailList = (): void => {
  cocktailList.value.set(8894, "blue moon");
};
const deleteFromCocktailList = (): void => {
  cocktailList.value.delete(5517);
}
</script>

<template>
  <ul>
    <li v-for="[id, cocktailName] in cocktailList" v-bind:key="id">IDが{{ id }}のカクテルは{{ cocktailName }}</li>
  </ul>
  <p>CocktailListを<button v-on:click="changeCocktailList">変更</button></p>
  <p>CocktailListに「ブルームーン」を<button v-on:click="addCocktailList">追加</button></p>
  <p>CocktailListからxyzを<button v-on:click="deleteFromCocktailList">削除</button></p>
</template>

