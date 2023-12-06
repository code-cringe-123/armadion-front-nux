<template>
    <div class="container-product-page">
        <div class="wrapper-product-page">
            <div class="product-page-title">
                {{ product && product.title }} {{ product && product.number }}
            </div>
            <div class="product-page-body">
                <div class="product-page-body-left">
                    <!-- <VueSlickCarousel :options="slickOptions">
            <div v-for="(slide, index) in product.imgs" :key="index">
              <img :src="slide" alt="Slide Image" />
            </div>
          </VueSlickCarousel> -->
                    <div class="carousel">
                        <div
                            class="carousel__item"
                            id="c_i_1"
                            style="width: 120px; height: 120px"
                            @click="changeMainImage($event)"
                        >
                            <img
                                src="../../public/svg/doors/door_card.jpg"
                                alt="door"
                            />
                        </div>
                        <div
                            class="carousel__item"
                            id="c_i_2"
                            style="width: 120px; height: 120px"
                            @click="changeMainImage($event)"
                        >
                            <img src="../../public/svg/doors/door_ch.svg" alt="door" />
                        </div>
                    </div>
                    <div class="page-body-left__img">
                        <img
                            id="pageImage"
                            src="../../public/svg/doors/door_card.jpg"
                            alt=""
                        />
                    </div>
                </div>
                <div class="product-page-body-right">
                    <div class="product-page-body-price-wrapper">
                        <div class="product-page-body-price">
                            {{ product && product.price }}
                        </div>
                        <UI-btn>Заказать</UI-btn>
                    </div>

                    <div class="product-page-body-block-wrapper">
                        <div class="product-page-body-title">Описание</div>
                        <div class="product-page-body-text">
                            {{ product && product.description }}
                        </div>
                    </div>

                    <div class="product-page-body-block-wrapper">
                        <div class="product-page-body-title">Доставка</div>
                        <div class="product-page-body-text">
                            {{ product && product.delivery }}
                        </div>
                    </div>

                    <div class="product-page-body-block-wrapper">
                        <div class="product-page-body-title">Оплата</div>
                        <div class="product-page-body-text">
                            {{ product && product.Payment }}
                        </div>
                    </div>

                    <div class="product-page-body-block-wrapper">
                        <div class="product-page-body-title">Гарантия</div>
                        <div class="product-page-body-text">
                            <div class="product-page-subtitle">
                                Гарантийный срок на дверной блок:
                            </div>
                            <ul>
                                <li
                                    class="product-page-li"
                                    v-for="(item, index) in product &&
                                    product.Guarantee"
                                    :key="index"
                                >
                                    <div class="product-page-li-dot">•</div>
                                    {{
                                        index === product.Guarantee.length - 1
                                            ? item
                                            : item + ';'
                                    }}
                                </li>
                            </ul>
                        </div>
                    </div>
                </div>
            </div>
            <div class="product-page-characteristics-container">
                <div class="product-page-characteristics-title">
                    Характеристики
                </div>
                <div class="product-page-characteristics-wrapper">
                    <div class="product-page-characteristics-left">
                        <!-- {{ product && product.title.padEnd(86, '.')  }}{{ product && product.number}} -->
                        <div class="size-fire">
                            <div class="stats">
                                <p>
                                    <span>{{
                                        product && product.whd__title
                                    }}</span>
                                    <span class="dotted__line"></span>
                                    <span class="size">{{
                                        product && product.whd
                                    }}</span>
                                </p>

                                <p>
                                    <span>{{
                                        product && product.fire__title
                                    }}</span>
                                    <span class="dotted__line"></span>
                                    <span class="size">{{
                                        product && product.fire
                                    }}</span>
                                </p>
                            </div>
                        </div>

                        <div class="stats-outside">
                            <h4>Внешняя отделка</h4>
                            <div class="stats">
                                <p>
                                    <span>{{
                                        product && product.material_out__title
                                    }}</span>
                                    <span class="dotted__line"></span>
                                    <span class="size">{{
                                        product && product.material
                                    }}</span>
                                </p>
                            </div>

                            <div class="stats">
                                <p>
                                    <span>{{
                                        product && product.color_out__title
                                    }}</span>
                                    <span class="dotted__line"></span>
                                    <span class="color-img"></span>
                                    <span class="size">{{
                                        product && product.color
                                    }}</span>
                                </p>
                            </div>
                        </div>

                        <div class="stats-inside">
                            <h4>Внутренняя отделка</h4>
                            <div class="stats">
                                <p>
                                    <span>{{
                                        product && product.material_in__title
                                    }}</span>
                                    <span class="dotted__line"></span>
                                    <span class="size">{{
                                        product && product.material
                                    }}</span>
                                </p>
                            </div>

                            <div class="stats">
                                <p>
                                    <span>{{
                                        product && product.color_in__title
                                    }}</span>
                                    <span class="dotted__line"></span>
                                    <span class="color-img"></span>
                                    <span class="size">{{
                                        product && product.color
                                    }}</span>
                                </p>
                            </div>
                        </div>

                        <div class="stats-inside">
                            <h4>Фурнитура</h4>
                            <div class="stats">
                                <p>
                                    <span>{{
                                        product && product.furn__title
                                    }}</span>
                                    <span class="dotted__line"></span>
                                    <span class="size">{{
                                        product && product.furn
                                    }}</span>
                                </p>
                            </div>

                            <div class="stats">
                                <p>
                                    <span>{{
                                        product && product.cil__title
                                    }}</span>
                                    <span class="dotted__line"></span>
                                    <span class="size">{{
                                        product && product.cil
                                    }}</span>
                                </p>
                            </div>

                            <div class="stats">
                                <p>
                                    <span>{{
                                        product && product.open__title
                                    }}</span>
                                    <span class="dotted__line"></span>
                                    <span class="size">{{
                                        product && product.open
                                    }}</span>
                                </p>
                            </div>
                        </div>
                    </div>

                    <div class="product-page-characteristics-right">
                        <div class="stats-inside">
                            <h4>Дверное полотно</h4>
                            <div class="stats">
                                <p>
                                    <span>{{
                                        product && product.material_p
                                    }}</span>
                                    <span class="dotted__line"></span>
                                    <span class="size">{{
                                        product && product.material
                                    }}</span>
                                </p>
                            </div>

                            <div class="stats">
                                <p>
                                    <span>{{
                                        product && product.filling__title
                                    }}</span>
                                    <span class="dotted__line"></span>
                                    <span class="size">{{
                                        product && product.filling
                                    }}</span>
                                </p>
                            </div>

                            <div class="stats">
                                <p>
                                    <span>{{
                                        product && product.color_p__title
                                    }}</span>
                                    <span class="dotted__line"></span>
                                    <span class="color-img"></span>
                                    <span class="size">{{
                                        product && product.color
                                    }}</span>
                                </p>
                            </div>

                            <div class="stats">
                                <p>
                                    <span>{{
                                        product && product.whd_window__title
                                    }}</span>
                                    <span class="dotted__line"></span>
                                    <span class="size">{{
                                        product && product.wh_window
                                    }}</span>
                                </p>
                            </div>

                            <div class="stats">
                                <p>
                                    <span>{{
                                        product && product.glazed_window__title
                                    }}</span>
                                    <span class="dotted__line"></span>
                                    <span class="size">{{
                                        product && product.glazed_window
                                    }}</span>
                                </p>
                            </div>

                            <div class="stats">
                                <p>
                                    <span>{{
                                        product && product.filling__title
                                    }}</span>
                                    <span class="dotted__line"></span>
                                    <span class="size">{{
                                        product && product.filling
                                    }}</span>
                                </p>
                            </div>
                        </div>

                        <div class="stats-inside">
                            <h4>Дверная коробка</h4>
                            <div class="stats">
                                <p>
                                    <span>{{
                                        product && product.material_box
                                    }}</span>
                                    <span class="dotted__line"></span>
                                    <span class="size">{{
                                        product && product.material
                                    }}</span>
                                </p>
                            </div>

                            <div class="stats">
                                <p>
                                    <span>{{
                                        product && product.filling__title
                                    }}</span>
                                    <span class="dotted__line"></span>
                                    <span class="size">{{
                                        product && product.filling
                                    }}</span>
                                </p>
                            </div>

                            <div class="stats">
                                <p>
                                    <span>{{
                                        product && product.color_box__title
                                    }}</span>
                                    <span class="dotted__line"></span>
                                    <span class="color-img"></span>
                                    <span class="size">{{
                                        product && product.color
                                    }}</span>
                                </p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <SimilarDoors />
        </div>
    </div>
</template>

<script setup>
import { onMounted, ref } from 'vue'

const product = ref(null)

const changeMainImage = (event) => {
    const pageImage = document.getElementById('pageImage')
    const newSrc = event.currentTarget.querySelector('img').src
    pageImage.src = newSrc
}

const loadProducts = async () => {
    try {
        const response = await fetch('/product.json')
        const data = await response.json()
        product.value = data
        product.value.Guarantee = product.value.Guarantee.split('; ')
    } catch (error) {
        console.error('Ошибка загрузки данных:', error)
    }
}

onMounted(() => {
    loadProducts()
})
// uncomment
// import VueSlickCarousel from "vue-slick-carousel";
// import "vue-slick-carousel/dist/vue-slick-carousel.css";

const productImg = ref({
    imgs: ['/svg/doors/door.svg', '/svg/doors/door.svg', '/svg/doors/door.svg'],
    // Add more product properties as needed
})

const slickOptions = {
    dots: true,
    infinite: true,
    speed: 500,
    slidesToShow: 1,
    slidesToScroll: 1,
    initialSlide: 0,
    arrows: false,
}
</script>

<style>
/*  */
.slick-slide img {
    width: 120px;
    height: 120px;
    object-fit: cover;
}

.slick-slide.slick-active img {
    border-radius: 8px;
    border: 2px solid #38bdf8;
}
/* stats styles */
.product-page-body-left {
    display: flex;
}
.page-body-left__img {
    background-repeat: no-repeat;
    margin: 0 auto;
}
.page-body-left__img > img {
    width: 280px;
    height: 415px;
}
.carousel {
    margin: 0 0 auto;
}

.carousel__item {
    background-color: transparent;
    margin-bottom: 12px;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 8px;
}
.carousel__item img {
    position: block;
    width: 82px;
    height: 112px;
}

#c_i_1:hover,
#c_i_2:hover {
    border: 2px solid #38bdf8;
}

h4 {
    margin: 0;
    padding-bottom: 12px;
}
.stats > p {
    margin: 0;
    display: flex;
    align-items: center;
    color: #9ca3af;
    padding-bottom: 8px;
}
.dotted__line {
    flex: 1;
    border-bottom: 1px dashed #e5e7eb; /* Измените цвет по необходимости */
    margin: auto 0 3.5px; /* Регулирует расстояние между точками и текстом */
    vertical-align: middle;
    display: inline-block;
}
.size {
    display: block;
    color: #6b7280;
}
.color-img {
    display: block;
    width: 12px;
    height: 12px;
    background-color: #949ba3;
    border-radius: 2px;
    margin-right: 4px;
}
/*  */

/*  */
.product-page-li-dot {
    display: flex;
    justify-content: center;
    height: 20px;
    min-width: 20px;
}

.product-page-li {
    display: flex;
}

.product-page-subtitle {
    font-family: Sansation;
    font-size: 16px;
    font-weight: 400;
    line-height: 22px;
    letter-spacing: 0em;
    text-align: left;
    color: #6b7280;
}

.product-page-characteristics-right {
    display: flex;
    flex-direction: column;
    gap: 20px;
    width: 580px;
    height: 400px;
}

.product-page-characteristics-left {
    display: flex;
    flex-direction: column;
    gap: 20px;
    width: 580px;
    height: 400px;
}

.product-page-characteristics-wrapper {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 20px;
}

.product-page-characteristics-container {
    margin: 60px 0;
    display: flex;
    flex-direction: column;
    gap: 20px;
}

.product-page-characteristics-title {
    font-family: Sansation;
    font-size: 24px;
    font-weight: 400;
    line-height: 29px;
    letter-spacing: 0em;
    text-align: left;
    color: #374151;
}

.product-page-body-text {
    font-family: Sansation;
    font-size: 16px;
    font-weight: 400;
    line-height: 22px;
    letter-spacing: 0em;
    text-align: left;
    color: #6b7280;
}

.product-page-body-title {
    font-family: Sansation;
    font-size: 16px;
    font-weight: 700;
    line-height: 22px;
    letter-spacing: 0em;
    text-align: left;
    color: #374151;
}

.product-page-body-block-wrapper {
    display: flex;
    flex-direction: column;
    gap: 10px;
}

.product-page-body-price {
    font-family: Sansation;
    font-size: 36px;
    font-weight: 400;
    line-height: 38px;
    letter-spacing: 0em;
    text-align: left;
    color: #374151;
}

.product-page-body-price-wrapper {
    width: 100%;
    height: 56px;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.product-page-body-right {
    width: 580px;
    display: flex;
    flex-direction: column;
    gap: 20px;
}

.product-page-body {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 20px;
}

.product-page-body-left {
    width: 580px;
    height: 413px;
}

.product-page-title {
    font-family: Sansation;
    font-size: 36px;
    font-weight: 400;
    line-height: 38px;
    letter-spacing: 0em;
    text-align: left;
    color: #374151;

    margin-bottom: 60px;
}

.container-product-page {
    margin-top: 195px;
    width: 100vw;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}

.wrapper-product-page {
    width: 1180px;
}
</style>
