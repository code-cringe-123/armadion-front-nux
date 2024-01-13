<template>
  <div>
    <Hero />
    <Catalog-landing :products="products" />
    <Measurements />
    <Blog />
    <Form id="form-scroll"/>
  </div>
</template>

<script setup>
import { ref } from "vue";

const products = ref([]);
const { data } = await useFetch(`https://api-armadion.ru/doors/popular/`);
products.value = data.value;
</script>
