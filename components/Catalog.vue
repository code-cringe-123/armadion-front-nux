<template>
  <div class="catalog-wrapper">
    <div class="products-wrapper">
      <!-- <div class="products" v-for="product in products" :key="product.id">
          <Product :product="product" />
        </div> -->
      <div class="products" v-for="product in FilteredItems" :key="product.id">
        <Product :product="product" />
      </div>
    </div>
  </div>
</template>

<script setup>
const { products, select_left__range, select_right__range } = defineProps([
  "products",
  "select_left__range",
  "select_right__range",
]);
const FilteredItems = ref([]);

const applyFilters = () => {
  FilteredItems.value = products.filter((product) => {
    return (
      product.price >= select_left__range &&
      product.price <= select_right__range
    );
  });
};
watch([select_left__range, select_right__range], () => {
  applyFilters();
});

const unwatchProducts = watch(
  () => products,
  () => {
    applyFilters();
  },
);

onMounted(() => {
  applyFilters();
});

onBeforeUnmount(() => {
  unwatchProducts();
});
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
