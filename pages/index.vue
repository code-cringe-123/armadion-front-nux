<template>
  <!-- <link rel="manifest" href="manifest.json">
  <link rel="apple-touch-icon" sizes="180x180" href="/icons/apple-touch-icon.png">
  <link rel="icon" type="image/png" sizes="32x32" href="/icons/favicon-32x32.png">
  <link rel="icon" type="image/png" sizes="16x16" href="/icons/favicon-16x16.png">
  <link rel="manifest" href="/site.webmanifest">
  <link rel="mask-icon" href="/icons/safari-pinned-tab.svg" color="#5bbad5">
  <meta name="msapplication-TileColor" content="#da532c">
  <meta name="theme-color" content="#ffffff">
  <script src="/static/build/app.js"></script> -->
  <div>
    <Hero />
    <Catalog-landing :products="products" />
    <Measurements />
    <Blog />
    <Form id="form-scroll" />
  </div>
</template>

<script setup>
import { ref } from "vue";

const products = ref([]);
const { data } = await useFetch(`https://api-armadion.ru/doors/popular`);
products.value = data.value;

// if ('serviceWorker' in navigator) {
//            window.addEventListener('load', function() {
//                navigator.serviceWorker.register('/service-worker.js').then(function(registration) {
//                    // Registration was successful
//                console.log('ServiceWorker registration successful with scope: ', registration.scope);
//              }, function(err) {
//                // registration failed :(
//                console.log('ServiceWorker registration failed: ', err);
//              }).catch(function(err) {
//                console.log(err)
//              });
//            });
//          } else {
//            console.log('service worker is not supported');
//          }
</script>
