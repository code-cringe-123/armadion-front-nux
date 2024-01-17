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
          {{ countFilters }}
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
            src="../public/svg/close-img-2.svg"
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
              ref="priceBoxMobile1"
              class="price-box-1 price-box"
              placeholder="От 900₽"
              v-maska
              data-maska="От #####₽"
              @keyup="emitFilterRequestMobile1"
            />
            <input
              ref="priceBoxMobile2"
              class="price-box-2 price-box"
              placeholder="До"
              v-maska
              data-maska="До #####₽"
              @keyup="emitFilterRequestMobile2"
            />
          </div>
          <div class="catalog-mobile-price-container-buttom">
            
            <div class="sizes-BTN-mobile-wrapper">
              <div
                v-for="(mobKey, mobValue) in  unique_values"
                :key="mobIndex"
                class="catalog-menu-mobile-item"
              >
                <!-- <h3 class="catalog-mobile-price-title">{{ mobValue }}</h3> -->
                  
                <div v-for="(mobKey_key, mobValue_value) in mobKey">
                  <h4 class="catalog-mobile-price-title">{{ mobValue_value }}</h4>

                  <div style="display: flex; flex-wrap: wrap; gap: 5px;">
                    <div v-for="(mobKey_key_key, mobValue_value_value) in mobKey_key" @click="handleTableClick(mobValue_value_value)">
                      <button @click="$emit('filterRequest', mobKey_key_key[0], mobKey_key_key[1])" style="flex: 1 0 calc(33.33% - 5px); max-width: 100px; height: 35px; margin-bottom: 5px;" :class="{'size-btn-active': sizeActiveCheck(mobValue_value_value), 'size-btn': !sizeActiveCheck(mobValue_value_value)}">
                        <span style="font-size: 10px;" class="size-btn-slot">{{ mobValue_value_value }}</span>
                      </button>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="catalog-mobile-btn-container" @click="closeSlideFilters">
          <button class="catalog-mobile-filter-button">
            Показать товары
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
            ref="priceBox1"
            class="price-box-1 price-box"
            placeholder="От 900₽"
            v-maska
            data-maska="От #####₽"
            @keyup="emitFilterRequest1"
          />

          <input
            ref="priceBox2"
            class="price-box-2 price-box"
            placeholder="До"
            v-maska
            data-maska="До #####₽"
            @keyup="emitFilterRequest2"
          />
        </div>
      </div>

      <!-- Настройки габаритных размеров -->
      <!-- второй подзаголовок -->

      <!-- Подзаголовок -->

      <div class="dimension-settings">
        <div
          style="display: flex; flex-direction: column"
          class="dimension-item"
          v-for="(key, value) in unique_values"
          :key="size"
        >
          <h2 class="filter__title">{{ value }}</h2>
          <div class="full-filter" v-for="(key_key, value_value) in key">
            <h4 class="filter__subtitle">{{ value_value }}</h4>
            <div
              class="list__filters"
              v-for="(key_key_key, value_value_value) in key_key"
            >
              <label class="checkbox__label">
                <input
                  class="catalog-checkbox"
                  type="checkbox"
                  @click="$emit('filterRequest', key_key_key[0], key_key_key[1])"
                />

                <!-- @change="(event) => handleChange(event, value_value_value)" -->
                <span class="filter__value">{{ value_value_value }}</span>
              </label>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!-- @click="onFilterUpdate(size)"  сверху было-->

    <!-- Настройки модели внутренней отделки 2 -->
    <!-- <div class="interior-settings">
        <div class="catalog-menu-title">
          {{ data?.filters?.[5]?.features[0].name }}
        </div>
        <input
          class="catalog-menu-search"
          v-model="searchQuery"
          @input="performSearch"
          placeholder="Найти"
        />
        {{ searchQuery }}
        <div
          class="interior-item"
          v-for="result in searchResults"
          :key="result.item"
        >
          <input class="catalog-checkbox" type="checkbox" />
          {{ result.item }}
        </div>
        <div
          class="interior-item"
          v-for="model in data?.filters?.[5]?.features"
          :key="model"
        >
          <label class="label-checkbex">
            <input class="catalog-checkbox" type="checkbox" />
            {{ model.value }}
          </label>
        </div>
      </div> -->
  </div>
</template>

<script setup>
import { ref, watchEffect, computed } from "vue";
import Fuse from "fuse.js";
import { vMaska } from "maska";
import { defineEmits } from "vue";
let countDoors = 0;
const priceBoxMobile1 = ref(null)
const priceBoxMobile2 = ref(null)
const priceBox1 = ref(null);
const priceBox2 = ref(null);

const emit = defineEmits(["filterRequest"]);
const { filters,doors } = defineProps(["filters", "doors"]);
const sizeActive = ref([]);

let countFilters = 0;

const checkingSizeAvailability = (size) => {
  if (sizeActiveCheck(size)) {
    sizeActive.value = sizeActive.value.filter((item) => item !== size);
    countFilters -= 1;
  } else {
    sizeActive.value.push(size);
    countFilters += 1;

    }
};


const sizeActiveCheck = (size) => {
  
  return sizeActive.value.includes(size);
};

const handleTableClick = (size) => {
  
  checkingSizeAvailability(size);
};
console.log(sizeActive)
const isSlideOutVisibleFilters = ref(false);

const toggleSlideFilters = () => {
  isSlideOutVisibleFilters.value = !isSlideOutVisibleFilters.value;
};

const closeSlideFilters = () => {
  isSlideOutVisibleFilters.value = false;
};

const inner_values = new Set();
const unique_values = {};

if (filters && filters.length) {
  for (let i = 0; i < filters.length; i++) {
    if (
      filters[i].name !== "Цена" &&
      filters[i].name !== "Дверное полотно" &&
      filters[i].name !== "Дверная коробка" && 
      filters[i].name !== "Характеристики"
    ) {
      if (!unique_values[filters[i].name]) {
        unique_values[filters[i].name] = {};
      }
      if (filters[i].features && filters[i].features.length) {
        for (let j = 0; j < filters[i].features.length; j++) {
          if (
            filters[i].features[j].name !== "Глазок" &&
            filters[i].features[j].name !== "Задвижка" &&
            filters[i].features[j].name !== "Материал внутренней отделки" &&
            filters[i].features[j].name !== "Броненакладка" &&
            filters[i].features[j].name !== "Материал внешней отделки" &&
            filters[i].features[j].name !== "Ручка" &&
            filters[i].features[j].name !== "Накладки"
            ){
            const feature = filters[i].features[j];
            if (!inner_values.has(feature.value)) {
              inner_values.add(feature.value);

              const innerMap = unique_values[filters[i].name];
              if (!innerMap[feature.name]) {
                innerMap[feature.name] = {};
              }

              const featureMap = innerMap[feature.name];
              featureMap[feature.value] = [feature.name_slug, feature.value_slug];
            }
          }
          
        }
      }
    }
    
  }
} else {
  console.error("filters is undefined or has no length");
};


const emitFilterRequestMobile1 = () => {
 let value = priceBoxMobile1.value.value;
 if (!value.includes("₽")) {
   priceBoxMobile1.value.value = value + "₽";
 }
 const numericValue = value.slice(3, 8);
 emit('filterRequest', 'min_price', numericValue);
};


const emitFilterRequestMobile2 = () => {
 let value = priceBoxMobile2.value.value;
 if (!value.includes("₽")) {
   priceBoxMobile2.value.value = value + "₽";
 }
 const numericValue = value.slice(3, 8);
 emit('filterRequest', 'max_price', numericValue);
};

const emitFilterRequest1 = () => {
 let value = priceBox1.value.value;
 if (!value.includes("₽")) {
   priceBox1.value.value = value + "₽";
 }
 const numericValue = value.slice(3, 8);
 emit('filterRequest', 'min_price', numericValue);
};

const emitFilterRequest2 = () => {
 let value = priceBox2.value.value;
 if (!value.includes("₽")) {
   priceBox2.value.value = value + "₽";
 }
 const numericValue = value.slice(3, 8);
 emit('filterRequest', 'max_price', numericValue);
};

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
  top: 5px;
  right: 5px;
  z-index: 10;
}

.catalog-filters-img {
  position: relative;
}

.circle-badge {
  position: absolute;
  top: 0;
  right: 0;
}

.catalog-mobile-btn-container {
  padding: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  position: absolute;
  margin-left: auto;
  margin-right: auto;
  bottom: 10px;
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

.size-btn {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 4px 8px;
  border-radius: 8px;
  background-color: #f3f4f6;
  border: none;
  transition: background-color 0.3s;
}

.size-btn-active {
  border: none;
  border-radius: 8px;
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
  grid-template-rows: repeat(3, 1fr);
}

.catalog-menu-mobile-item {
  width: 100%; 
  
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
}

.catalog-mobile-price-title {
  color: #374151;
  font-family: Sansation;
  font-size: 10px;
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
  // margin-bottom: 16px;
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
  background-image: url("../public/svg/checkbox.svg");
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

.catalog-page-menu {
  display: flex;
  margin-right: 20px;

  @media screen and (max-width: 666px) {
    display: none;
  }
}

.menu {
  max-width: 280px;
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
  justify-content: flex-start;
}

// filters
.full-filter {
  margin-left: 15px;
  display: flex;
  flex-direction: column;
}

.filter__title {
  margin: 0;
  color: var(--gray-700, #374151);
}

.filter__subtitle {
  margin: 10px 0 5px;
  color: var(--gray-700, #374151);

  font-family: Sansation;
  font-size: 16px;
  font-style: normal;

  line-height: 140%;
}

.list__filters {
  margin-left: 20px;
}

.checkbox__label {
  padding-bottom: 5px;
  cursor: pointer;
  display: flex;
  align-items: center;
}
</style>
