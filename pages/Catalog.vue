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

<script src="/static/build/app.js"></script>

   <script>
       if ('serviceWorker' in navigator) {
           window.addEventListener('load', function() {
               navigator.serviceWorker.register('/service-worker.js').then(function(registration) {
                   // Registration was successful
               console.log('ServiceWorker registration successful with scope: ', registration.scope);
             }, function(err) {
               // registration failed :(
               console.log('ServiceWorker registration failed: ', err);
             }).catch(function(err) {
               console.log(err)
             });
           });
         } else {
           console.log('service worker is not supported');
         }
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
