<template>
  <div class="container-product-page">
    <div class="wrapper-product-page">
      <div class="product-page-title">
        {{ data && data.title }}
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
              v-for="(image, index) in data?.images"
              :key="index"
              class="carousel__item"
              :id="'ci' + (index + 1)"
              style="width: 120px; height: 120px"
              @click="changeMainImage($event, index)"
            >
              <img :src="data && data?.images?.[index]?.url" alt="door" />
            </div>
          </div>
          <div class="page-body-left__img">
            <img id="pageImage" :src="data && data?.images?.[0]?.url" alt="" />
          </div>
          <div class="top__swiper">
            <slider-pag :images="images" />
          </div>
        </div>
        <div class="product-page-title product-page-title__media">
          {{ data && data.title }}
        </div>
        <div class="product-page-body-right">
          <div class="product-page-body-price-wrapper">
            <div class="product-page-body-price">
              {{ data && data.price }} ₽
            </div>
            <UI-btn>Заказать</UI-btn>
          </div>

          <div class="product-page-body-block-wrapper">
            <div class="product-page-body-title">Описание</div>
            <div class="product-page-body-text">
              {{ data && data.description }}
            </div>
          </div>

          <div class="product-page-body-block-wrapper">
            <div class="product-page-body-title">Доставка</div>
            <div class="product-page-body-text">
              {{ data && data.delivery }}
            </div>
          </div>

          <div class="product-page-body-block-wrapper">
            <div class="product-page-body-title">Оплата</div>
            <div class="product-page-body-text">
              {{ data && data.payment }}
            </div>
          </div>

          <div class="product-page-body-block-wrapper">
            <div class="product-page-body-title">Гарантия</div>
            <div class="product-page-body-text">
              <div class="product-page-subtitle">
                Гарантийный срок на дверной блок:
              </div>
              <ul>
                <!-- v-for="(item, index) in product &&
                                    product.Guarantee"
                                    :key="index" -->
                <li class="product-page-li">
                  <div class="product-page-li-dot">•</div>
                  {{ data && data.safeguards }}
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>

      <div class="product-page-characteristics-container">
        <h3 class="product-page-characteristics-title">Характеристики</h3>
        <div class="product-page-characteristics-wrapper">
          <div class="product-page-characteristics-left">
            <!-- {{ product && product.title.padEnd(86, '.')  }}{{ product && product.number}} -->
            <div class="size-fire">
              <div class="stats">
                <p>
                  <span>{{
                    data?.feature_categories?.[0]?.features?.[0]?.name
                  }}</span>
                  <span class="dotted__line"></span>
                  <span class="size">{{
                    data?.feature_categories?.[0]?.features?.[0]?.value
                  }}</span>
                </p>

                <p>
                  <span>{{
                    data?.feature_categories?.[0]?.features?.[1]?.name
                  }}</span>
                  <span class="dotted__line"></span>
                  <span class="size">{{
                    data?.feature_categories?.[0]?.features?.[1]?.value
                  }}</span>
                </p>
              </div>
            </div>

            <div class="stats-outside">
              <h4>Внешняя отделка</h4>
              <div class="stats">
                <p>
                  <span>{{
                    data?.feature_categories?.[1]?.features?.[0]?.name
                  }}</span>
                  <span class="dotted__line"></span>
                  <span class="size">{{
                    data?.feature_categories?.[1]?.features?.[0]?.value
                  }}</span>
                </p>
              </div>

              <div class="stats">
                <p>
                  <span>{{
                    data?.feature_categories?.[1]?.features?.[1]?.name
                  }}</span>
                  <span class="dotted__line"></span>
                  <span class="color-img"></span>
                  <span class="size">{{
                    data?.feature_categories?.[1]?.features?.[1]?.value
                  }}</span>
                </p>
              </div>
            </div>

            <div class="stats-inside">
              <h4>Внутренняя отделка</h4>
              <div class="stats">
                <p>
                  <span>{{
                    data?.feature_categories?.[2]?.features?.[0]?.name
                  }}</span>
                  <span class="dotted__line"></span>
                  <span class="size">{{
                    data?.feature_categories?.[2]?.features?.[0]?.value
                  }}</span>
                </p>
              </div>

              <div class="stats">
                <p>
                  <span>{{
                    data?.feature_categories?.[2]?.features?.[1]?.name
                  }}</span>
                  <span class="dotted__line"></span>
                  <span class="color-img"></span>
                  <span class="size">{{
                    data?.feature_categories?.[2]?.features?.[1]?.value
                  }}</span>
                </p>
              </div>
            </div>

            <div class="stats-inside">
              <h4>Фурнитура</h4>
              <div class="stats">
                <p>
                  <span>{{
                    data?.feature_categories?.[5]?.features?.[0]?.name
                  }}</span>
                  <span class="dotted__line"></span>
                  <span class="size">{{
                    data?.feature_categories?.[5]?.features?.[0]?.value
                  }}</span>
                </p>
              </div>

              <div class="stats">
                <p>
                  <span>{{
                    data?.feature_categories?.[5]?.features?.[1]?.name
                  }}</span>
                  <span class="dotted__line"></span>
                  <span class="size">{{
                    data?.feature_categories?.[5]?.features?.[1]?.value
                  }}</span>
                </p>
              </div>

              <div class="stats">
                <p>
                  <span>{{
                    data?.feature_categories?.[5]?.features?.[2]?.name
                  }}</span>
                  <span class="dotted__line"></span>
                  <span class="size">{{
                    data?.feature_categories?.[5]?.features?.[2]?.value
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
                    data?.feature_categories?.[3]?.features?.[0]?.name
                  }}</span>
                  <span class="dotted__line"></span>
                  <span class="size">{{
                    data?.feature_categories?.[3]?.features?.[0]?.value
                  }}</span>
                </p>
              </div>

              <div class="stats">
                <p>
                  <span>{{
                    data?.feature_categories?.[3]?.features?.[1]?.name
                  }}</span>
                  <span class="dotted__line"></span>
                  <span class="size">{{
                    data?.feature_categories?.[3]?.features?.[1]?.value
                  }}</span>
                </p>
              </div>

              <div class="stats">
                <p>
                  <span>{{
                    data?.feature_categories?.[3]?.features?.[2]?.name
                  }}</span>
                  <span class="dotted__line"></span>
                  <span class="color-img"></span>
                  <span class="size">{{
                    data?.feature_categories?.[3]?.features?.[2]?.value
                  }}</span>
                </p>
              </div>

              <div class="stats">
                <p>
                  <span>{{
                    data?.feature_categories?.[3]?.features?.[3]?.name
                  }}</span>
                  <span class="dotted__line"></span>
                  <span class="size">{{
                    data?.feature_categories?.[3]?.features?.[3]?.value
                  }}</span>
                </p>
              </div>

              <div class="stats">
                <p>
                  <span>{{
                    data?.feature_categories?.[3]?.features?.[4]?.name
                  }}</span>
                  <span class="dotted__line"></span>
                  <span class="size">{{
                    data?.feature_categories?.[3]?.features?.[4]?.value
                  }}</span>
                </p>
              </div>

              <div class="stats">
                <p>
                  <span>{{
                    data?.feature_categories?.[3]?.features?.[5]?.name
                  }}</span>
                  <span class="dotted__line"></span>
                  <span class="size">{{
                    data?.feature_categories?.[3]?.features?.[5]?.value
                  }}</span>
                </p>
              </div>
            </div>

            <div class="stats-inside">
              <h4>Дверная коробка</h4>
              <div class="stats">
                <p>
                  <span>{{
                    data?.feature_categories?.[4]?.features?.[0]?.name
                  }}</span>
                  <span class="dotted__line"></span>
                  <span class="size">{{
                    data?.feature_categories?.[4]?.features?.[0]?.value
                  }}</span>
                </p>
              </div>

              <div class="stats">
                <p>
                  <span>{{
                    data?.feature_categories?.[4]?.features?.[1]?.name
                  }}</span>
                  <span class="dotted__line"></span>
                  <span class="size">{{
                    data?.feature_categories?.[4]?.features?.[1]?.value
                  }}</span>
                </p>
              </div>

              <div class="stats">
                <p>
                  <span>{{
                    data?.feature_categories?.[4]?.features?.[2]?.name
                  }}</span>
                  <span class="dotted__line"></span>
                  <span class="color-img"></span>
                  <span class="size">{{
                    data?.feature_categories?.[4]?.features?.[2]?.value
                  }}</span>
                </p>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- <div class="doors__cont">
                <SimilarDoors />
            </div> -->
      <div class="doors__slider">
        <slider :similardoors="similardoors" />
      </div>
    </div>
  </div>
</template>

<script setup>
// import SimilarDoors from '../components/SimilarDoors.vue'
import { ref } from "vue";
// import swiper from './slider.vue'
// import TopSwiper from './slider-pag.vue'

const changeMainImage = (event) => {
  const pageImage = document.getElementById("pageImage");

  const allItems = document.querySelectorAll(".carousel__item");
  allItems.forEach((item) => item.classList.remove("active__icon"));

  const clickedItem = event.currentTarget;
  clickedItem.classList.add("active__icon");

  const newSrc = clickedItem.querySelector("img").src;
  pageImage.src = newSrc;
};

const route = useRoute();

const { data } = await useFetch(
  `http://185.244.51.158/doors/${route.params.prduct_id}/`,
);

const images = ref([]);
images.value = data.value.images;
const similardoors = ref([]);
similardoors.value = data.value.similar_doors;

// uncomment
// import VueSlickCarousel from "vue-slick-carousel";
// import "vue-slick-carousel/dist/vue-slick-carousel.css";

const productImg = ref({
  imgs: ["/svg/doors/door.svg", "/svg/doors/door.svg", "/svg/doors/door.svg"],
  // Add more product properties as needed
});

const slickOptions = {
  dots: true,
  infinite: true,
  speed: 500,
  slidesToShow: 1,
  slidesToScroll: 1,
  initialSlide: 0,
  arrows: false,
};
</script>

<style>
/*  */
.doors__slider .swiper {
  width: 100%;
}

.doors__slider .swiper .swiper-wrapper .swiper-slide {
  background: inherit;
  width: 280px;
}

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
  height: 413px;
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
  cursor: pointer;
}

.carousel__item img {
  position: block;
  width: 76px;
  height: 112px;
}

.active__icon {
  border: 2px solid #38bdf8;
}

h4 {
  margin: 0;
  padding-bottom: 12px;
  color: var(--gray-700, #374151);
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
  gap: 12px;
  width: 580px;
  height: 400px;
}

.product-page-characteristics-left {
  display: flex;
  flex-direction: column;
  gap: 12px;
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

.product-page-title__media {
  display: none;
}

.doors__slider,
.top__swiper {
  width: 100%;
}

.top__swiper {
  display: none;
}

@media screen and (max-width: 1200px) {
  .container {
    overflow-x: hidden;
  }

  .product-page-title {
    display: none;
  }

  .container-product-page {
    margin-top: 115px;
  }

  .product-page-title__media {
    display: block;
    color: #374151;
    font-size: 24px;
    font-weight: 400;
    line-height: 105%;

    margin: 0 auto;
    max-width: 400px;
  }

  .product-page-body-price-wrapper {
    display: none;
  }

  .product-page-body {
    display: flex;
    flex-direction: column;
    width: 100%;
    padding: 0 10px;
  }
  .page-body-left__img {
    display: none;
  }
  .carousel {
    display: none;
  }

  .product-page-body-left {
    margin: 0 auto;
  }

  .top__swiper {
    display: block;
    height: 100%;
    width: 100%;
  }

  .product-page-body-right {
    margin: 0 auto;
    max-width: 450px;
  }

  .product-page-characteristics-container {
    text-align: left;
    margin-top: 40px;
    gap: 30px;
  }

  .product-page-characteristics-title {
    margin: 0 auto;
  }

  .product-page-characteristics-wrapper {
    max-width: 450px;
    margin: 0 auto;
    display: flex;
    flex-direction: column;
    gap: 20px;
  }

  .product-page-characteristics-left,
  .product-page-characteristics-right {
    width: auto;
    height: auto;
  }

  .SimilarDoors-wrapper {
    display: flex;
    flex-direction: row-reverse;
    margin: 0 auto;
  }
  .product {
    overflow: hidden;
  }

  .doors__slider {
    display: block;
  }
  .doors__cont {
    display: none;
  }
}
</style>
