
<template>
  <ul>
    <li v-for="r in 5" v-bind:key="r">半径{{r}}の円の演習：{{ 2 * r * 3.1415 }}</li>
  </ul>
</template>
