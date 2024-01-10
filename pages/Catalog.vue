<template>
  <div class="catalog-page-container">
    <Catalog-menu :filters="filters" @filterRequest="onFilterUpdate" />
    <Catalog :products="products" :products_filtered="products_filtered" />
  </div>
</template>

<script setup>
import { ref, watchEffect } from "vue";
const products = ref([]);
const products_filtered = ref([]);
const filters = ref([]);

const filterQuery = new URLSearchParams();

function onFilterUpdate(key_key, value_value_value) {
  filterQuery.append(key_key, value_value_value);
  refresh();
}

let { data, refresh } = await useFetch(
  `https://api-armadion.ru/doors/filter?${filterQuery.toString()}`,
);

watchEffect(async () => {
  refresh();
  for (let [key, value] of filterQuery.entries()) {
    console.log(key, value);
    data = await useFetch(
    `https://api-armadion.ru/doors/filter?${filterQuery.toString()}`,
    );
  }

  
  
  // console.log(1)
  // console.log(data?.data?._value?.doors);
  // for (var key1 in data) {
  //   if (key1 === "data"){
  //     for (var key_key2 in data[key1]){
  //       if (key_key2 === "_value"){
  //         for (var key_key_key3 in data[key1][key_key2]){
  //           if (key_key_key3 === "doors"){
  //             console.log(data[key1][key_key2][key_key_key3])
  //             console.log(`${key1}, ${key_key2}, ${key_key_key3}`)
  //           }
  //         }
  //       }
  //     }
  //   }
  // }
  console.log(data)
  console.log(data?.data?._value?.doors)
  products.value = data?.data?._value?.doors;
  filters.value = data.value.filters;

});
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
