<template>
  <div class="catalog-wrapper">
    <div class="products-wrapper">
      <!-- <div class="products" v-for="product in products" :key="product.id">
          <Product :product="product" />
        </div> -->
      <div class="products" v-for="product in products" :key="product.id">
        <Product :product="product" />
      </div>
    </div>
  </div>
</template>

<script setup>
const { products, select_left__range, select_right__range, searchQuery } =
  defineProps(["products", "select_left__range", "select_right__range"]);
// const FilteredItems = ref([]);
// отслеживание каждого нажатия на клавишу в js`е и передача этих данных
// console.log(products[0].title);
const filteredCards = () => {
  var self = this;
  const filtered = this.products.filter(function (product) {
    return product.title;
  });

  return filtered;
};
// const applyFilters = () => {
//   FilteredItems.value = products.filter(product => {
//     return (
//       product.price >= select_left__range &&
//       product.price <= select_right__range
//     );
//   });
// };
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
