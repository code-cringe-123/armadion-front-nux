<template>
  <div class="SimilarDoors-title">Похожие Двери</div>
  <swiper
    v-if="isWideScreen"
    class="mySwiper"
    :slidesPerView="4"
    loop
    loopAddBlankSlides
  >
    <swiper-slide v-for="door in similardoors" :key="door.id">
      <PopularProduct :product="door" />
    </swiper-slide>
  </swiper>
  <swiper v-else class="mySwiper" :slidesPerView="2" loop loopAddBlankSlides>
    <swiper-slide v-for="door in similardoors" :key="door.id">
      <PopularProduct :product="door" />
    </swiper-slide>
  </swiper>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue";
import { Swiper, SwiperSlide } from "swiper/vue";
const props = defineProps(["similardoors"]);
</script>

<style>
.doors__slider .swiper .swiper-wrapper {
  display: flex;
  margin-left: 10px;
}

.doors__slider .swiper {
  width: 50%;
  display: block;
}

.doors__slider .swiper .swiper-wrapper .swiper-slide {
  text-align: center;
  font-size: 18px;
  background: #fff;

  /* Center slide text vertically */
  display: flex;
  justify-content: center;
  align-items: center;
}

.product-wrapper {
  width: 100%;
}

.SimilarDoors-title {
  text-align: center;
  margin-bottom: 20px;
}
</style>
