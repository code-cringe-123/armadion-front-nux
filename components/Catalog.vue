<template>
  <div class="catalog-wrapper">
    <div class="products-wrapper">
      <div class="products" v-for="product in products" :key="product.id">
        <Product :product="product" />
      </div>
    </div>
  </div>
</template>

<script setup>
const props = defineProps(["products"]);
</script>

<style lang="scss">
.catalog-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  max-width: 1180px;

  @media screen and (max-width: 1024px) {
    width: 70%;
  }

  @media screen and (max-width: 920px) {
    width: 355px;
  }
}

.products-wrapper {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
  // @media screen and (max-width: 1200px) {
  //     width: 100%;
  //     display: grid;
  //     grid-template-columns: repeat(2, 1fr);
  //     gap: 15px;
  // }

  @media screen and (max-width: 1200px) {
    width: 100%;
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 15px;
  }

  @media screen and (max-width: 920px) {
    width: 100%;
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
</style>
