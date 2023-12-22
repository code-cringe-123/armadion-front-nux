<template>
  <div class="catalog-container">
    <div class="catalog-wrapper">
      <div class="catalog-title">Готовые конфигурации</div>
      <div class="products-wrapper-landing">
        <div class="products" v-for="product in products" :key="product.id">
          <PopularProduct :product="product" />
        </div>
      </div>
      <ViewMoreButton>Смотреть все</ViewMoreButton>
    </div>
  </div>
</template>

<script setup>
const props = defineProps(["products"]);
</script>

<style lang="scss">
.catalog-container {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 80px;

  @media screen and (max-width: 768px) {
    width: 100vw;
  }
}

.catalog-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  max-width: 1180px;

  @media screen and (max-width: 1024px) {
    width: 100vw;
  }

  @media screen and (max-width: 768px) {
    width: 355px;
  }
}

.products-wrapper-landing {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 20px;

  @media screen and (max-width: 1200px) {
    width: 100vw;
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 15px;
  }

  @media screen and (max-width: 960px) {
    width: 100vw;
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 15px 10px;
  }

  @media screen and (max-width: 768px) {
    width: 100vw;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 10px;
  }
}

.products {
  display: flex;
  align-items: center;
  justify-content: center;
}

.catalog-title {
  font-size: 36px;
  font-weight: 400;
  width: 1180px;
  margin-bottom: 40px;
  color: #111827;
  line-height: 38px;

  @media screen and (max-width: 1200px) {
    width: 96vw;
  }

  @media screen and (max-width: 768px) {
    width: 355px;
    font-size: 24px;
    font-weight: 400;
    line-height: 25px;
    margin: 0 0 30px 0;
  }
}
</style>
