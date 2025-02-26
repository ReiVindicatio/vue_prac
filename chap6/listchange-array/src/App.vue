<script setup lang="ts">
import {ref} from "vue";

const cocktailListInit: string[] = ["white lady", "blue hawaii", "new york"];
const cocktailList = ref(cocktailListInit);
const changeCocktailList = (): void => {
  cocktailList.value = ["Martini", "XYZ", "Manhattan"];
};
const addCocktailList = (): void => {
  cocktailList.value.push("blue moon");
};
const deleteFromCocktailList = (): void => {
  cocktailList.value.pop();
};
</script>

<template>
  <ul>
    <li v-for="(cocktailName, index) in cocktailList" v-bind:key="cocktailName">{{ cocktailName }}(インデックス{{ index }})</li>
  </ul>
  <p>
    CocktailListを<button v-on:click="changeCocktailList">変更</button>
  </p>
  <p>
    CocktailListの末尾に「ブルームーン」を<button v-on:click="addCocktailList">追加</button>
  </p>
  <p>
    CocktailListの末尾の要素を<button v-on:click="deleteFromCocktailList">削除</button>
  </p>
</template>

