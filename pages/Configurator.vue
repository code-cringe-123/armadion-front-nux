<template>
  <div class="configurator__wrapper">
    <iframe
      id="configurator"
      src="https://tourmaline-alfajores-cbb3b1.netlify.app/"
      frameborder="0"
    >
    </iframe>
    <!-- <button class="configurator__btn__back">жопа</button> -->
  </div>
</template>

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
.configurator__wrapper {
  margin-top: 90px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: -105px;
  width: 100vw;
  height: 100vh;
  // overflow-x: hidden;
  // overflow-y: hidden;
  @media screen and (max-width: 768px) {
    // transform: rotate(90deg);
    // margin-bottom: 0;
    margin-top: 30px;
  }
}
#configurator {
  width: 100%;
  height: 100%;
  overflow-x: hidden;
  overflow-y: hidden;
  @media screen and (max-width: 768px) {
    margin-bottom: -20px;
    width: 100vw;
    height: 100%;
  }
}
</style>
