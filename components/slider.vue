<template>
    <swiper class="mySwiper" :slidesPerView="2" loop loopAddBlankSlides>
        <swiper-slide v-for="product in products" :key="product.id">
            <Product :product="product" />
        </swiper-slide>
    </swiper>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { Swiper, SwiperSlide } from 'swiper/vue'
// import Product from '../components/Product.vue'

const products = ref([])

// Загрузка данных из SimilarDoors.json
const loadProducts = async () => {
    try {
        const response = await fetch('/SimilarDoors.json')
        const data = await response.json()
        products.value = data
    } catch (error) {
        console.error('Ошибка загрузки данных:', error)
    }
}

onMounted(() => {
    loadProducts()
})
</script>

<style>
.swiper-wrapper {
    display: flex;
    margin-left: 10px;
    gap: 80px;
}

.swiper {
    width: 50%;
    display: block;
    margin: 0 0 0 22%;
}

.swiper-slide {
    text-align: center;
    font-size: 18px;
    background: #fff;

    /* Center slide text vertically */
    display: flex;
    justify-content: center;
    align-items: center;
}

.product {
    width: 280px;
}
</style>
