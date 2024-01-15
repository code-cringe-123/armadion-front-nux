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

<style>
.configurator__btn__back {
  position: relative;
  z-index: 100;
  width: 100px;
  height: 100px;
}
.configurator__wrapper {
  margin-bottom: -103px;
}
#configurator {
  width: 1920px;
  height: 750px;
  margin-top: 90px;
}
</style>
