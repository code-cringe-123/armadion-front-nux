<template>
  <div>
    <NuxtLayout>
      <NuxtPage />
    </NuxtLayout>
  </div>
  <!-- <link rel="manifest" href="manifest.json"> -->
</template>

<script setup>
// if (‘serviceWorker’ in navigator) {
// window.addEventListener(‘load’, function() {  
//  navigator.serviceWorker.register(‘/sw.js’).then(
//    function(registration) {
//      // Registration was successful
//      console.log(‘ServiceWorker registration successful with scope: ‘, registration.scope); },
//    function(err) {
//      // registration failed :(
//      console.log(‘ServiceWorker registration failed: ‘, err);
//    });
// });
// }
</script>


<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

:root {
  --title-color: #111827;
}

@font-face {
  font-family: Sansation;
  font-weight: 700;
  src: local("Sansation"), url("../fonts/Sansation/Sansation-Bold.ttf");
}

@font-face {
  font-family: Sansation;
  font-weight: 300;
  src: local("Sansation"), url("../fonts/Sansation/Sansation-Light.ttf");
}

@font-face {
  font-family: Sansation;
  font-weight: 400;
  src: local("Sansation"), url("../fonts/Sansation/Sansation-Regular.ttf");
}

* {
  box-sizing: border-box;
}

html {
  height: 100%;
  width: 100vw;
  box-sizing: border-box;
  /* overflow-x: hidden; */
}

body {
  height: 100%;
  font-family: "Sansation", "sans-serif";
  margin: 0;
  padding: 0;
  font-size: 16px;
  overflow-x: hidden;
  box-sizing: border-box;
}

ol,
ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

/* // for blue buttons............................................................................ */
.blue-btn:hover {
  background-color: black;
  color: white;
  transition: 0.3s;
}

.blue-btn:active {
  background-color: white;
  color: black;
  border: 2px solid black;
  transition: 0.3s;
}

/* // imgs.............................................................................................. */
img {
  max-width: 100%;
}
</style>
