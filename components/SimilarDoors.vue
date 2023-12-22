<template>
  <div class="SimilarDoors-container">
    <div class="SimilarDoors-title">Похожие Двери</div>
    <div class="SimilarDoors-wrapper">
      <div class="SimilarDoors" v-for="product in products" :key="product.id">
        <Product :product="product" />
      </div>
    </div>
  </div>
</template>

<style lang="scss">
.SimilarDoors-title {
  font-family: Sansation;
  font-size: 24px;
  font-weight: 400;
  line-height: 29px;
  letter-spacing: 0em;
  text-align: left;
  color: #374151;
}

.SimilarDoors-container {
  display: flex;
  flex-direction: column;
  align-items: start;
  justify-content: center;
  max-width: 1180px;
  gap: 20px;
  //   @media screen and (max-width: 1024px) {
  //     width: 100vw;
  //   }
  //   @media screen and (max-width: 768px) {
  //     width: 355px;
  //   }
}

.SimilarDoors-wrapper {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 20px;
  //   @media screen and (max-width: 1200px) {
  //     width: 100vw;
  //     display: grid;
  //     grid-template-columns: repeat(3, 1fr);
  //     gap: 15px;
  //   }
  //   @media screen and (max-width: 960px) {
  //     width: 100vw;
  //     display: grid;
  //     grid-template-columns: repeat(2, 1fr);
  //     gap: 15px 10px;
  //   }
  //   @media screen and (max-width: 768px) {
  //     width: 100vw;
  //     display: flex;
  //     flex-direction: column;
  //     align-items: center;
  //     gap: 10px;
  //   }
}

.SimilarDoors {
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
<script setup>
// import Product from './Product.vue'
import { ref, onMounted } from "vue";

const products = ref([]);

// загрузка данных из products.json
const loadProducts = async () => {
  try {
    const response = await fetch("/SimilarDoors.json");
    const data = await response.json();
    products.value = data;
  } catch (error) {
    console.error("Ошибка загрузки данных:", error);
  }
};

onMounted(() => {
  loadProducts();
});
</script>
