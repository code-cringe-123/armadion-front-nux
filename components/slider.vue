<template>
  <div class="SimilarDoors-title">Похожие Двери</div>
  <div class="swiper-mobu">
    <swiper class="mySwiper-mobile" :slidesPerView="1" loop loopAddBlankSlides>
      <swiper-slide v-for="door in similardoors" :key="door.id">
        <PopularProduct :product="door" />
      </swiper-slide>
    </swiper>
  </div>
  <div class="swiper">
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
.swiper {
  display: block;
  @media screen and (max-width: 700px) {
    display: none;
  }
}

.swiper-mobu {
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
