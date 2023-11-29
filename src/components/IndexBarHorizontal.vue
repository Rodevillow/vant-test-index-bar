<script setup>
import {IndexBar, IndexAnchor, Cell} from 'vant';
import {computed} from "vue";

const props = defineProps({
  data: {
    type: Array,
    default: [],
  }
})

const categoriesList = computed(() => Array.from(new Set(props.data.map(p => p.category))));
const getCategoryProducts = category => props.data.filter(p => p.category === category)
</script>

<template>
  <div class="index-bar">
    <IndexBar :index-list="categoriesList">
      <template
          v-for="category in categoriesList"
          :key="category"
      >
        <IndexAnchor :index="category"/>

        <template
            v-for="product in getCategoryProducts(category)"
            :key="product.title"
        >
          <Cell :title="product.title"/>
        </template>

      </template>

    </IndexBar>
  </div>
</template>

<style lang="scss">
.van-index-anchor {
  color: white;
  font-weight: bold;
  text-transform: uppercase;
}

.van-index-bar {
  &__sidebar {
    position: sticky;
    background-color: #3c3c3c;

    top: 15px;

    width: 100%;
    height: 30px;

    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: flex-start;

    overflow-x: auto;
    -ms-overflow-style: none;
    scrollbar-width: none;

    &::-webkit-scrollbar {
      display: none;
    }
  }
}
</style>