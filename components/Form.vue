<template>
  <div class="form-container">
    <div class="form-wrapper">
      <Feedback />
      <img class="form-img" src="../public/svg/Form-img.svg" alt="picture" />
    </div>
  </div>
</template>

<style lang="scss">
.form-container {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 80px;

  @media screen and (max-width: 768px) {
    width: 100vw;
    margin-top: 120px;
  }
}

.form-wrapper {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 20px;
  max-width: 1180px;

  @media screen and (max-width: 1024px) {
    width: 100vw;
    display: flex;
    flex-direction: column-reverse;
    align-items: center;
    gap: 50px;
  }

  @media screen and (max-width: 768px) {
    width: 100vw;
    display: flex;
    flex-direction: column-reverse;
    align-items: center;
    gap: 50px;
  }
}

// .form-img {
//     // min-width: 580px;
//     // min-height: 404px;
//     // @media screen and (max-width: 425px) {

//     // }
// }
</style>

<script setup>
// import Feedback from '../components/Feedback.vue'
// import router from '../router'
</script>
