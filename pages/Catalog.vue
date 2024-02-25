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
// let uniqueValues = {};
let uniqueValues = {}; // для отслеживания всех фильтров

async function onFilterUpdate(key, value) {
  // Добавляем значение в массив uniqueValues, если его еще нет там
  if (!uniqueValues[key]) {
    uniqueValues[key] = [];
  }

  if (key === "min_price" || key === "max_price") {
    value = parseInt(value); // Преобразуем значение в число
    if (value >= 9000) {
      // Удаляем старое значение из массива, если оно существует
      uniqueValues[key] = uniqueValues[key].filter((item) => item >= 9000);
      // Добавляем новое значение в массив
      if (!uniqueValues[key].includes(value)) {
        uniqueValues[key] = [value];
      }
      // Обновляем filterQuery.value[key]
      filterQuery.value[key] = uniqueValues[key].join(",");
    } else {
      // Удаляем значения меньше 9000 из массива и обновляем filterQuery.value[key]
      uniqueValues[key] = uniqueValues[key].filter((item) => item >= 9000);
      // Если массив стал пустым, удаляем ключ из filterQuery.value
      if (uniqueValues[key].length === 0) {
        delete filterQuery.value[key];
      } else {
        filterQuery.value[key] = uniqueValues[key].join(",");
      }
    }
  } else {
    if (!uniqueValues[key].includes(value)) {
      uniqueValues[key].push(value);
      filterQuery.value[key] = uniqueValues[key].join(",");
    } else {
      uniqueValues[key] = uniqueValues[key].filter((item) => item !== value);
      filterQuery.value[key] = uniqueValues[key].join(",");
    }
  }

  // Удаляем ключ из filterQuery.value, если его значение пусто
  if (filterQuery.value[key].length === 0) {
    delete filterQuery.value[key];
  }
}

let { data, refresh } = await useFetch(`https://api-armadion.ru/doors/filter`, {
  query: filterQuery.value,
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
