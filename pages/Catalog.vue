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

const { data, refresh } = await useFetch(
  `https://api-armadion.ru/doors/filter?${filterQuery.toString()}`,
);

watchEffect(() => {
  for (let [key, value] of filterQuery.entries()) {
    console.log(key, value);
    
    products.value.push(
      ...`https://api-armadion.ru/doors/filter?${filterQuery.toString()}`.value
        .doors,
    );
  }
  // products.value = [...data.value.doors];

  filters.value = data.value.filters;
  // try {
  //   products.value = [...data.value.doors];
  //   console.log(products)
  // } catch (error) {
  //   console.error("Произошла ошибка:", error);
  // }
  // // products.value.push(...data.value.doors);
  // console.log("HERE");
  // // console.log( `https://api-armadion.ru/doors/filter?${filterQuery.toString()}`)
  // console.log(data);
  // console.log(products);
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
