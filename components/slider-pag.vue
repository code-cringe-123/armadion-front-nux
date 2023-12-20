<template>
    <swiper :pagination="true" :modules="modules" class="mySwiper">
        <swiper-slide>
            <img
                id="img-slider"
                src="../../svg/doors/door_card.jpg"
                alt="door"
            />
        </swiper-slide>
        <swiper-slide>
            <img id="img-slider" src="../../svg/doors/door_ch.svg" alt="door" />
        </swiper-slide>
    </swiper>
</template>
<script>
import { Swiper, SwiperSlide } from 'swiper/vue'

import 'swiper/css'

import 'swiper/css/pagination'

import { Pagination } from 'swiper/modules'

export default {
    components: {
        Swiper,
        SwiperSlide,
    },
    setup() {
        return {
            modules: [Pagination],
        }
    },
}
</script>
<style scoped>
.top__swiper > .swiper {
    width: 100%;
    height: 100%;
}

#img-slider {
    height: 98%;
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
