<template>
  <div class="catalog-page-container">
    <Catalog-menu
      :filters="data.filters"
      :doors="data.doors"
      @filterRequest="onFilterUpdate"
    />
    <Catalog :products="data.doors" :products_filtered="data.doors" />
  </div>
</template>

<script setup>
import { ref } from "vue";
const filterQuery = ref({});

async function onFilterUpdate(key_key, value_value_value) {
  console.log(filterQuery);
  // Проверяем, существует ли уже ключ в filterQuery.value
  if (filterQuery.value.hasOwnProperty(key_key)) {
    // Если ключ существует, удаляем его
    delete filterQuery.value[key_key];
  } else {
    // Если ключ не существует, добавляем его
    filterQuery.value[key_key] = value_value_value;
  }
  //  refresh();
}

let { data, refresh } = await useFetch(`https://api-armadion.ru/doors/filter`, {
  query: filterQuery.value,
});
// let { data } = await useFetch(
//   `https://api-armadion.ru/doors/filter?min_price=20650.0`
// );
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
