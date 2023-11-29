<script setup>
import {indexBarMockData} from "./mock/indexBar.js";
import IndexBarHorizontal from "./components/IndexBarHorizontal.vue";
</script>

<template>
  <div class="container">
    <IndexBarHorizontal :data="indexBarMockData"/>
  </div>
</template>

<style lang="scss" scoped>
.container {
  max-width: 900px;
  width: 100%;
}
</style>