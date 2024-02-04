<template>
  <div class="SimilarDoors-title">Похожие Двери</div>
  <div class="similar-slider-mobile">
    <div class="slider__wrapper" v-for="door in similardoors" :key="door.id">
      <PopularProduct :product="door" />
    </div>
  </div>
  <div class="similar-slider">
    <div class="slider__wrapper" v-for="door in similardoors" :key="door.id">
      <PopularProduct :product="door" />
    </div>
  </div>
</template>

<script setup>
// import { ref, onMounted, onBeforeUnmount } from "vue";
// import { Swiper, SwiperSlide } from "swiper/vue";
const props = defineProps(["similardoors"]);
</script>

<style lang="scss">
.similar-slider {
  display: flex;
  overflow-x: scroll;

  scrollbar-color: inherit #e0e0e0;
  scrollbar-width: thin;
  padding-bottom: 100px;
  margin-bottom: 50px;
  @media screen and (max-width: 1190px) {
    max-width: 60%;
    margin: 0 auto;
  }
  @media screen and (max-width: 700px) {
    display: none;
  }
}

.slider__wrapper:first-child {
  margin-left: 0;
  @media screen and (max-width: 1190px) {
    margin-left: 100px;
  }
  @media screen and (max-width: 981px) {
    margin-left: 200px;
  }
}

.slider__wrapper {
  margin-left: 500px;
  @media screen and (max-width: 1190px) {
    margin-left: 100px;
  }
  @media screen and (max-width: 981px) {
    margin-left: 100px;
  }
}
.similar-slider-mobile {
  display: none;
  @media screen and (max-width: 700px) {
    display: flex;
    overflow-x: scroll;
    scrollbar-color: inherit #e0e0e0;
    scrollbar-width: thin;
    padding-bottom: 100px;
    margin-bottom: 50px;
    max-width: 30%;
    margin: 0 auto;
    .slider__wrapper:first-child {
      margin-left: 0;
    }
  }
  @media screen and (max-width: 375px) {
    width: 100%;
  }
}

.SimilarDoors-title {
  color: var(--gray-700, #374151);
  font-family: Sansation;
  font-size: 24px;
  font-style: normal;
  font-weight: 400;
  line-height: 120%; /* 28.8px */
  margin-bottom: 20px;
  // margin-right: 56%;
  @media screen and (max-width: 1190px) {
    text-align: center;
    margin-right: 0;
  }
  @media screen and (max-width: 700px) {
  }
}
</style>
