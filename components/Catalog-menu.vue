<template>
  <!-- мобилка -->
  <div class="catalog-page-menu-mobile">
    <div class="catalog-filters">
      <svg
        class="catalog-filters-img"
        width="30"
        height="30"
        viewBox="0 0 30 30"
        fill="none"
        xmlns="http://www.w3.org/2000/svg"
        @click="toggleSlideFilters"
      >
        <path
          d="M7.5 11.25H22.5"
          stroke="#374151"
          stroke-width="1.5"
          stroke-linecap="round"
          stroke-linejoin="round"
        />
        <path
          d="M10 16.25H20"
          stroke="#374151"
          stroke-width="1.5"
          stroke-linecap="round"
          stroke-linejoin="round"
        />
        <path
          d="M12.5 21.25H17.5"
          stroke="#374151"
          stroke-width="1.5"
          stroke-linecap="round"
          stroke-linejoin="round"
        />
        <path
          d="M15 27.5C8.09644 27.5 2.5 21.9035 2.5 15C2.5 8.09644 8.09644 2.5 15 2.5C21.9035 2.5 27.5 8.09644 27.5 15C27.5 21.9035 21.9035 27.5 15 27.5Z"
          stroke="#374151"
          stroke-width="1.5"
          stroke-linecap="round"
          stroke-linejoin="round"
        />
        <circle
          class="circle-count-filters"
          cx="24px"
          cy="6px"
          r="6"
          fill="#38BDF8"
        />
        <text
          x="24"
          y="5.5"
          text-anchor="middle"
          dy="4"
          fill="#fff"
          class="active-count-filters"
        >
          2
        </text>
      </svg>
      <div @click="toggleSlideFilters" class="catalog-filters-name">
        Фильтры
      </div>
    </div>
    <!-- выезжающий блок -->
    <div
      :class="[
        'catalog-page-filters-mobile',
        { show: isSlideOutVisibleFilters },
      ]"
    >
      <div class="close-filters">
        <div class="close-filters-img-container">
          <img
            class="close-filters-img"
            src="../svg/close-img-2.svg"
            alt=""
            @click="closeSlideFilters"
          />
        </div>
      </div>
      <div class="catalog-mobile-price-container">
        <div class="catalog-mobile-price-container-up">
          <div class="catalog-mobile-price-title">Цена</div>
          <div class="price-range-mobile">
            <input
              class="price-box-mobile-1 price-box"
              placeholder="От 900₽"
              v-maska
              data-maska="От ###₽"
              v-model="priceRange[0]"
            />
            <input
              class="price-box-mobile-2 price-box"
              placeholder="До"
              v-maska
              data-maska="До ####₽"
              v-model="priceRange[1]"
            />
          </div>
          <div class="catalog-mobile-price-container-buttom">
            <div class="catalog-mobile-price-title">Габаритные размеры</div>
            <div class="sizes-BTN-mobile-wrapper">
              <div
                v-for="size in sizes"
                :key="size"
                class="catalog-menu-mobile-item"
                @click="handleTableClick(size)"
                :class="{
                  'size-btn-active': sizeActiveCheck(size),
                  'size-btn': !sizeActiveCheck(size),
                }"
              >
                <button class="size-btn">
                  <span class="size-btn-slot">{{ size }}</span>
                </button>
              </div>
            </div>
          </div>
        </div>
        <div class="catalog-mobile-btn-container" @click="closeSlideFilters">
          <button class="catalog-mobile-filter-button">
            Показать 2 товаров
          </button>
        </div>
      </div>
    </div>
  </div>
  <!-- ------- -->
  <div class="catalog-page-menu">
    <div class="menu" :style="{ maxWidth: '280px' }">
      <!-- Настройки цены -->
      <div class="price-settings">
        <div class="catalog-menu-title">Цена</div>
        <div class="price-range">
          <input
            class="price-box-1 price-box"
            placeholder="От 900₽"
            v-maska
            data-maska="От ###₽"
            v-model="priceRange[0]"
          />
          <input
            class="price-box-2 price-box"
            placeholder="До"
            v-maska
            data-maska="До #####₽"
            v-model="priceRange[1]"
          />
        </div>
      </div>

      <!-- Настройки габаритных размеров -->
      <div class="dimension-settings">
        <div class="catalog-menu-title">Габаритные размеры</div>

        <div class="dimension-item" v-for="size in sizes" :key="size">
          <label class="label-checkbex">
            <input class="catalog-checkbox" type="checkbox" />
            {{ size }}
          </label>
        </div>
      </div>

      <!-- Настройки модели внутренней отделки -->
      <div class="interior-settings">
        <div class="catalog-menu-title">Модель внутренней отделки</div>
        <input
          class="catalog-menu-search"
          v-model="searchQuery"
          @input="performSearch"
          placeholder="Найти"
        />
        <div
          class="interior-item"
          v-for="result in searchResults"
          :key="result.item"
        >
          <input class="catalog-checkbox" type="checkbox" />
          {{ result.item }}
        </div>
        <div class="interior-item" v-for="model in interiorModels" :key="model">
          <label class="label-checkbex">
            <input class="catalog-checkbox" type="checkbox" />
            {{ model }}
          </label>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, watchEffect, computed } from "vue";
import Fuse from "fuse.js";
import { vMaska } from "maska";
const props = defineProps(["filters"]);
import { defineEmits } from "vue";

const changePriceRange = (newValue) => {
  priceRange.value = newValue;
};

const updatePriceRange = () => {
  // Отправляем измененный диапазон цен в родительский компонент
  defineEmits().emit("updatePriceRange", priceRange.value);
};

//
const sizeActive = ref([]);

let priceRange = ref([0, 1000000]);

const checkingSizeAvailability = (size) => {
  if (sizeActiveCheck(size)) {
    sizeActive.value = sizeActive.value.filter((item) => item !== size);
  } else {
    sizeActive.value.push(size);
  }
};

const sizeActiveCheck = (size) => {
  return sizeActive.value.includes(size);
};

const handleTableClick = (size) => {
  checkingSizeAvailability(size);
};

const isSlideOutVisibleFilters = ref(false);

const toggleSlideFilters = () => {
  isSlideOutVisibleFilters.value = !isSlideOutVisibleFilters.value;
};

const closeSlideFilters = () => {
  isSlideOutVisibleFilters.value = false;
};

const sizes = ref([
  "2100*1000*24",
  "2100*1010*14",
  "2100*1300*34",
  "2000*900*48",
  "2100*100*24",
  "2100*1010*4",
  "210*1300*34",
]);

const interiorModels = ref([
  "10(6)мм Гладкая 1",
  "10(6)мм Гладкая 2",
  "10(6)мм Гладкая 2",
  "10(6)мм Гладкая 2",
  "10(6)мм Гладкая 2",
  "10(6)мм Гладкая 2",
  "10(6)мм Гладкая 2",
  "10(6)мм Гладкая 2",
]);

const searchQuery = ref("");
const searchResults = ref([]);

const performSearch = () => {
  const fuse = new Fuse([...interiorModels.value]);
  searchResults.value = fuse.search(searchQuery.value);
};

watchEffect(() => {
  performSearch();
});
</script>
<style lang="scss">
.price-range {
  width: 100%;
  accent-color: #38bdf8;
}
.price-range::-webkit-slider-runnable-track {
  height: 2px;
  background-color: #bae6fd;
}
.price-range::-webkit-slider-thumb {
  position: relative;
  /* width: 20px;
    height: 20px; */
  top: -7px;
  border: 2px solid inherit;
}

//
.active-count-filters {
  font-family: Sansation;
  font-size: 10px;
  font-weight: 400;
  line-height: 16px;
  letter-spacing: 0em;
  text-align: center;
}
.circle-count-filters {
  position: fixed;
  top: 5px; /* или другое значение, чтобы задать отступ сверху */
  right: 5px; /* или другое значение, чтобы задать отступ справа */
  z-index: 10; /* или любое другое высокое значение */
}

// .catalog-filters-img {
//     position: relative;
//     z-index: 0;
// }
.catalog-filters-img {
  position: relative;
}

.circle-badge {
  position: absolute;
  top: 0;
  right: 0;
}

.catalog-mobile-btn-container {
  // width: 100vw;
  padding: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  position: absolute;
  margin-left: auto;
  margin-right: auto;
  bottom: 30px;
  left: 0;
  text-align: center;
  right: 0;
}

.catalog-mobile-filter-button {
  font-family: Sansation;
  font-size: 24px;
  font-weight: 400;
  line-height: 29px;
  letter-spacing: 0em;
  // text-align: center;
  color: #f9fafb;

  background-color: #38bdf8;
  border-radius: 5px;
  border: none;
  width: 100%;
  height: 45px;
  transition: 0.3s;
}

.catalog-mobile-filter-button:active {
  background-color: #0284c7;
  transition: 0.3s;
}

.label-checkbex {
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
}

.size-btn > button {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 110px;
  height: 24px;
  padding: 4px 8px;
  border-radius: 8px;
  background-color: #f3f4f6;
  border: none;
  transition: background-color 0.3s;
}

// add classes to btn-active
.size-btn-active > button {
  border: none;
  border-radius: 8px;
  width: 110px;
  height: 24px;
  background: rgba(rgb(56, 189, 248), 0.7);
  transition: background-color 0.3s;
  .size-btn-slot {
    color: #f3f4f6;
    transition: color 0.3s;
  }
}

.size-btn-inactive {
  background-color: #f3f4f6;
}

.catalog-menu-mobile-item {
  width: 110px;
  height: 24px;
}

// .sizes-BTN-item-mobile {
//   display: flex;
//   align-items: center;
//   justify-content: center;
// }

// add transition and border

.size-btn-slot {
  font-family: Sansation;
  font-size: 14px;
  font-weight: 400;
  line-height: 16px;
  letter-spacing: 0em;
  text-align: center;
  color: #9ca3af;
}

.sizes-BTN-mobile-wrapper {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 8px;
}

.catalog-mobile-price-container-up {
  margin-bottom: 20px;
}

.price-range-mobile {
  width: 100vw;
  display: flex;
  justify-content: space-between;
  padding: 0 20px 0 0;
}

.price-box-mobile-1,
.price-box-mobile-2 {
  width: 167px;
  height: 32px;
  background-color: #f3f4f6;
  border: none;
  box-sizing: border-box;
  outline: none;
  cursor: pointer;
  border-radius: 4px;
  margin-bottom: 20px;
  padding-top: 8px;
  padding-right: 6px;
  padding-bottom: 8px;
  padding-left: 6px;
}

.catalog-mobile-price-container {
  padding: 0 10px 0 10px;
  width: 100vw;
  height: 98px;
  // height: 100vw;
  // display: flex;
  // flex-direction: column;
  // justify-content: space-evenly;
}

.catalog-mobile-price-title {
  color: #374151;
  font-family: Sansation;
  font-size: 16px;
  font-weight: 400;
  line-height: 22px;
  letter-spacing: 0em;
  margin-bottom: 12px;
}

.close-filters-img-container {
  width: 34px;
  height: 34px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.catalog-page-filters-mobile {
  // @media screen and (max-width: 9999px) {
  //   display: none;
  // }
  // @media screen and (max-width: 768px) {
  //   display: block;
  // }
  // height: 100%;
  position: fixed;
  background: #f9fafb;
  top: 0;
  left: -101%;
  bottom: 0;
  right: 0;
  width: 100vw;
  transition: 0.7s;
  z-index: 100000;
}

.catalog-page-filters-mobile.show {
  left: 0;
  transition: 0.7s;
}

.close-filters {
  width: 100vw;
  margin-bottom: 16px;
  padding: 10px 10px 0 0;
  display: flex;
  justify-content: flex-end;
}

.catalog-filters-name {
  font-family: Sansation;
  font-size: 24px;
  font-weight: 400;
  line-height: 25px;
  letter-spacing: 0em;
}

.catalog-filters {
  width: 355px;
  display: flex;
  align-items: center;
  justify-content: start;
  margin-bottom: 12px;
  display: none;

  @media screen and (max-width: 666px) {
    display: flex;
  }
}

.catalog-filters-img {
  margin-right: 8px;
}

// .............................
.catalog-menu-search {
  margin-bottom: 12px;
  width: 280px;
  height: 32px;
  background-color: #f3f4f6;
  border: none;
  appearance: none;
  outline: none;
  border-radius: 3px;
  padding-top: 8px;
  padding-right: 6px;
  padding-bottom: 8px;
  padding-left: 6px;
}

.catalog-menu-search::placeholder {
  color: #d1d5db;
}

.catalog-menu-search::-webkit-input-placeholder {
  opacity: 1;
  transition: opacity 0.3s ease;
}

.catalog-menu-search::-moz-placeholder {
  opacity: 1;
  transition: opacity 0.3s ease;
}

.catalog-menu-search:-moz-placeholder {
  opacity: 1;
  transition: opacity 0.3s ease;
}

.catalog-menu-search:-ms-input-placeholder {
  opacity: 1;
  transition: opacity 0.3s ease;
}

.catalog-menu-search:focus::-webkit-input-placeholder {
  opacity: 0;
  transition: opacity 0.3s ease;
}

.catalog-menu-search:focus::-moz-placeholder {
  opacity: 0;
  transition: opacity 0.3s ease;
}

.catalog-menu-search:focus:-moz-placeholder {
  opacity: 0;
  transition: opacity 0.3s ease;
}

.catalog-menu-search:focus:-ms-input-placeholder {
  opacity: 0;
  transition: opacity 0.3s ease;
}

.price-box::-webkit-input-placeholder {
  opacity: 1;
  transition: opacity 0.3s ease;
}

.price-box::-moz-placeholder {
  opacity: 1;
  transition: opacity 0.3s ease;
}

.price-box:-moz-placeholder {
  opacity: 1;
  transition: opacity 0.3s ease;
}

.price-box:-ms-input-placeholder {
  opacity: 1;
  transition: opacity 0.3s ease;
}

.price-box:focus::-webkit-input-placeholder {
  opacity: 0;
  transition: opacity 0.3s ease;
}

.price-box:focus::-moz-placeholder {
  opacity: 0;
  transition: opacity 0.3s ease;
}

.price-box:focus:-moz-placeholder {
  opacity: 0;
  transition: opacity 0.3s ease;
}

.price-box:focus:-ms-input-placeholder {
  opacity: 0;
  transition: opacity 0.3s ease;
}

.catalog-checkbox {
  margin: 0 7px 0 0;
  width: 16px;
  height: 16px;
  background-color: #f3f4f6;
  border: none;
  width: 20px;
  height: 20px;
  appearance: none;
  outline: none;
  border-radius: 2px;
  cursor: pointer;
}

.catalog-checkbox:checked::before {
  content: "";
  display: block;
  width: 16px;
  height: 16px;
  background-image: url("../../svg/checkbox.svg");
  background-size: contain;
  background-repeat: no-repeat;
  position: relative;
  top: 50%;
  left: 50%;
  transform: translate(-47%, -45%);
}

.catalog-checkbox:checked {
  background-color: #38bdf8;
}

/* .catalog-checkbox:not(:disabled):active + label::before {
  background-color: #e9950e;
  border-color: #0d58ae;
} */
.catalog-page-menu {
  display: flex;
  margin-right: 20px;

  @media screen and (max-width: 666px) {
    display: none;
  }
}

.menu {
  max-width: 280px;
  /* padding: 20px; */
}

.price-settings {
  margin-bottom: 12px;
}

.price-range {
  display: flex;
  align-items: center;
}

.catalog-menu-title {
  margin-bottom: 12px;
  font-family: Sansation;
  font-size: 16px;
  font-weight: 400;
  line-height: 22px;
  letter-spacing: 0em;
  /* text-align: center; */
}

.price-box-1,
.price-box-2 {
  width: 134px;
  height: 32px;
  background-color: #f3f4f6;
  border: none;
  box-sizing: border-box;
  outline: none;
  cursor: pointer;
  margin-right: 12px;
  border-radius: 4px;
  margin-bottom: 20px;

  padding-top: 8px;
  padding-right: 6px;
  padding-bottom: 8px;
  padding-left: 6px;
}

.price-box-2 {
  margin-right: 0;
}

.price-box-1::placeholder,
.price-box-2::placeholder {
  font-family: Sansation;
  font-size: 14px;
  font-weight: 400;
  line-height: 16px;
  letter-spacing: 0em;
  color: #d1d5db;
  /* padding-top: 8px;
  padding-right: 6px;
  padding-bottom: 8px;
  padding-left: 6px; */
}

.price-box-1::placeholder {
  color: #111827;
}

.price-box {
  font-family: Sansation;
  font-size: 14px;
  font-weight: 400;
  line-height: 16px;
  letter-spacing: 0em;
  text-align: left;
  color: #111827;
}

.dimension-item,
.interior-item {
  margin-bottom: 12px;
  font-family: Sansation;
  font-size: 14px;
  font-weight: 400;
  line-height: 16px;
  letter-spacing: 0em;
  color: #9ca3af;
  display: flex;
  align-items: center;
  justify-content: flex-start;
}
</style>
