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
        <li class="product-page-li" v-for="(item, index) in data.safeguards.split(/[:;]/).slice(1)" :key="index">
            <div class="product-page-li-dot">•</div>
            <span v-if="item.trim().startsWith('на')">{{ item.trim() }}</span>
        </li>
    </ul>
</div>


          </div>
        </div>
      </div>

      <div class="product-page-characteristics-container">
        <div class="product-page-characteristics-wrapper">
          <!-- {{ product && product.title.padEnd(86, '.')  }}{{ product && product.number}} -->
          <div
            class="stats__title"
            v-if="
              new_names[0].name.toLowerCase() !==
                'габаритные размеры (в*ш*г), мм' &&
              new_names[0].name.toLowerCase() !== 'характеристики'
            "
          >
            >
            {{ new_names[0].name }}
          </div>
          <div class="stats" v-for="(category,categoryIndex) in new_names" :key="categoryIndex">
            <h4>{{ category.name }}</h4>
            <p v-if="categoryIndex == 0" v-for="(feature, featureIndex_temp) in category.features" :key="featureIndex_temp">
              <div style="display: flex; flex-direction: column; gap: 8px; width: 100%;">
                <span style="display: flex; width: 100%;">
                  <span class="span-characteristics">{{ 
                    sizeMesName
                  }}</span>
                  <span class="dotted__line"></span>
                  <span class="size">{{ 
                    sizeMesValue
                  }}</span>
                </span>

                <span style="display: flex; width: 100%;">
                  <span class="span-characteristics">{{ 
                    feature.name
                  }}</span>
                  <span class="dotted__line"></span>
                  <span class="size">{{ 
                    feature.value
                  }}</span>
                </span>
                
              </div>  
            </p>

            <p v-else v-for="(feature, featureIndex) in category.features" :key="featureIndex">
              <span style="display: flex; width: 100%;">
                <span class="span-characteristics">{{ 
                  feature.name
                }}</span>
                <span class="dotted__line"></span>
                <span class="size">{{ 
                  feature.value
                }}</span>
              </span>
            </p>
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
import { ref } from "vue";

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
  `https://api-armadion.ru/doors/${route.params.prduct_id}/`,
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

// Характеристики для h4
const new_names = [];
const errors_names = [];
let sizeMesName;
let sizeMesValue;
for (let i = 0; i < data.value.feature_categories.length; i++) {
  const currentName = data.value.feature_categories[i].name.toLowerCase();
  if (
    !errors_names.includes(currentName) &&
    currentName !== "габаритные размеры (в*ш*г), мм".toLowerCase()
  ) {
    errors_names.push(currentName);
    new_names.push(data.value.feature_categories[i]);
  } else if (currentName === "габаритные размеры (в*ш*г), мм".toLowerCase()){
    sizeMesName = data.value.feature_categories[i].features[0].name;
    sizeMesValue = data.value.feature_categories[i].features[0].value;
  }
}
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
  width: 220px;
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
  width: 65px;
  height: 112px;
}

.active__icon {
  border: 2px solid #38bdf8;
}

.stats h4 {
  margin: 0;
  padding-bottom: 12px;
  color: var(--gray-700, #374151);
}

.stats > p {
  margin: 0;
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
  color: #9ca3af;
  padding-bottom: 8px;
}
.stats:nth-child(2) {
  margin-top: 68px;
}
.dotted__line {
  flex: 1;
  border-bottom: 1px dashed #e5e7eb;
  margin: auto 0 3.5px;
  vertical-align: middle;
  display: inline-block;
}
.size {
  display: block;
  text-align: right;
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

.product-page-characteristics-wrapper {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-template-rows: repeat(4, auto) repeat(2, auto);
  gap: 20px;
}

.product-page-characteristics-wrapper .stats:first-of-type h4 {
  font-family: Sansation;
  font-size: 24px;
  font-weight: 400;
  line-height: 29px;
  margin-bottom: 30px;
  letter-spacing: 0em;
  text-align: left;
  color: #374151;
}

.product-page-characteristics-container {
  margin: 60px 0;
  display: flex;
  flex-direction: column;
  gap: 20px;
}
.stats__title {
  font-family: Sansation;
  font-size: 24px;
  font-weight: 400;
  line-height: 29px;
  margin-bottom: 30px;
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

  .stats:first-child h4 {
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
@media screen and (max-width: 455px) {
  .product-page-body-right {
    width: 100vw;
    padding: 0 10px;
  }
  .product-page-characteristics-wrapper {
    width: 100vw;
    padding: 0 10px;  
  }
  .span-characteristics {
    font-size: 14px;
  }
  .size {
    font-size: 14px;
    /* max-width: 197px; */
  }
  .stats:nth-child(2) {
    margin-top: 0px;
  }
}
</style>
