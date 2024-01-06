<template>
  <div class="catalog-page-container">
    <Catalog-menu :filters="filters" @filterRequest="onFilterUpdate" />
    <Catalog :products="products" />
  </div>
</template>

<script setup>
import { ref } from "vue";
const products = ref([]);
const filters = ref([]);

const filterQuery = new URLSearchParams();

function onFilterUpdate(key_key, value_value_value) {
  filterQuery.set(key_key, value_value_value);
  // console.log("HERE@@@");
  // console.log(key_key, value_value_value);
  // console.log(`https://api-armadion.ru/doors/filter${filterQuery.toString()}`);
  update();
}

const { data, update } = await useFetch(
  `https://api-armadion.ru/doors/filter${filterQuery.toString()}`,
);

products.value = data.value.doors;
filters.value = data.value.filters;

// const new_sizes = [];
// console.log(data.value.filters);
// for (let i = 0; i < data.value.filters[3].features.length; i++) {
//   if (!new_sizes.includes(data.value.filters[3].features[i].value)) {
//     new_sizes.push(data.value.filters[3].features[i].value);
//   }
// }

const test = (size) => {
  console.log(size);
};
</script>

<style lang="scss">
.catalog-page-container {
  margin-top: 195px;
  display: flex;
  flex-direction: row;
  /* align-items: center; */
  justify-content: center;
  @media screen and (max-width: 1024px) {
    padding: 0 20px;
  }
  @media screen and (max-width: 666px) {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
}
</style>
