<template>
  <swiper :pagination="true" :modules="modules" class="mySwiper">
    <swiper-slide v-for="(image, index) in images" :key="index">
      <img class="slider-image" :src="image.url" :alt="'door ' + (index + 1)" />
    </swiper-slide>
  </swiper>
</template>
<script setup>
import { defineProps } from "vue";
import { Swiper, SwiperSlide } from "swiper/vue";
import "swiper/css";
import "swiper/css/pagination";
import { Pagination } from "swiper/modules";

const props = defineProps(["images"]);

const modules = [Pagination];
</script>
<style>
.swiper-pagination-bullet-active {
  background: #38bdf8;
}
.top__swiper > .swiper {
  width: 100%;
  height: 100%;
}

.slider-image {
  height: 95%;
  width: 45%;
  padding-bottom: 20px;
}

.top__swiper {
  width: 50%;
  margin: 0 auto;
}

.top__swiper .mySwiper {
  width: 100%;
  height: 100%;
}

.top__swiper .mySwiper .swiper-slide {
  text-align: center;
  font-size: 18px;
  display: flex;
  justify-content: center;
  align-items: center;
}

/* .swiper-slide img {
    display: block;
    width: 100%;
    height: 100%;
    object-fit: cover;
} */
</style>
