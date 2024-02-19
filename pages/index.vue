<template>
  <link rel="manifest" href="{% static "/manifest.json" %}">
  <div>
    <Hero />
    <Catalog-landing :products="products" />
    <Measurements />
    <Blog />
    <Form id="form-scroll" />
  </div>
</template>
<script src="../static/build/app.js"></script>

<script setup>
import { ref } from "vue";

const products = ref([]);
const { data } = await useFetch(`https://api-armadion.ru/doors/popular`);
products.value = data.value;

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
