<template>
  <div class="SimilarDoors-title">Похожие Двери</div>
  <div class="similar-slider-mobile">
    <swiper class="mySwiper" :slidesPerView="1" loop loopAddBlankSlides>
      <swiper-slide v-for="door in similardoors" :key="door.id">
        <PopularProduct :product="door" />
      </swiper-slide>
    </swiper>
  </div>
  <div class="similar-slider">
    <swiper class="mySwiper" :slidesPerView="2" loop loopAddBlankSlides>
      <swiper-slide v-for="door in similardoors" :key="door.id">
        <PopularProduct :product="door" />
      </swiper-slide>
    </swiper>
  </div>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue";
import { Swiper, SwiperSlide } from "swiper/vue";
const props = defineProps(["similardoors"]);
</script>

<style lang="scss">
.similar-slider {
  display: block;
  @media screen and (max-width: 700px) {
    display: none;
  }
}

.similar-slider-mobile {
  display: none;
  @media screen and (max-width: 700px) {
    display: block;
  }
}

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

/* .product-wrapper {
  width: 100%;
  display: contents
} */

.SimilarDoors-title {
  text-align: center;
  margin-bottom: 20px;
}
</style>
