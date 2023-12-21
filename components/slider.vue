<template>
    <div class="SimilarDoors-title">Похожие Двери</div>
    <swiper class="mySwiper" :slidesPerView="3" loop loopAddBlankSlides>
        <swiper-slide v-for="door in similarDoors" :key="door.id">
            <Product :product="door" />
        </swiper-slide>
    </swiper>
</template>

<script setup>
import { ref } from 'vue'
import { Swiper, SwiperSlide } from 'swiper/vue'
const props = defineProps(['similarDoors'])
// import Product from '../components/Product.vue'

// const products = ref([])

// // Загрузка данных из SimilarDoors.json
// const loadProducts = async () => {
//     try {
//         const response = await fetch('/SimilarDoors.json')
//         const data = await response.json()
//         products.value = data
//     } catch (error) {
//         console.error('Ошибка загрузки данных:', error)
//     }
// }
// const products = ref([])
// const loadProducts = async () => {
//     try {
//         const response = await fetch('http://185.244.51.158/doors/popular/')
//         const data = await response.json()
//         products.value = data
//     } catch (error) {
//         console.error('Ошибка загрузки данных:', error)
//     }
// }

// onMounted(() => {
//     loadProducts()
// })

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
