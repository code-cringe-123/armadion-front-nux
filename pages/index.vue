<template>
  <div>
    <Hero />
    <Catalog-landing :products="products" />
    <Measurements />
    <Blog />
    <Form />
  </div>
</template>

<script setup>
import { ref } from "vue";

const products = ref([]);
const { data } = await useFetch(`http://185.244.51.158/doors/popular/`);
products.value = data.value;
</script>
