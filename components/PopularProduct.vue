<template>
  <router-link :to="`/product/${product.id}`" class="product-link">
    <div class="product">
      <div class="product-wrapper">
        <router-link :to="`/product/${product.id}`" class="img-product-wrapper">
          <img
            class="product-img"
            :src="product.image[0].url"
            alt="Product Image"
          />
        </router-link>
        <div class="card-body">
          <router-link :to="`/product/${product.id}`" class="product-name">{{
            product.title
          }}</router-link>
          <span class="product-price">{{ product.price }} ₽</span>
        </div>
      </div>
      <div class="product-number">
        {{ product.article }} <span class=""> (Армада)</span>
      </div>
    </div>
  </router-link>
</template>

<script setup>
const props = defineProps(["product"]);
</script>

<style lang="scss">
.product-link {
  text-decoration: none;
}

.product {
  cursor: pointer;
  width: 280px;
  height: 381px;
  display: flex;
  align-items: center;
  // justify-content: center;
  flex-direction: column;
  background-color: #f3f4f6;
  border-radius: 8px;

  @media screen and (max-width: 768px) {
    width: 355px;
  }
}

.product-number {
  position: relative;
  transform: rotate(270deg);
  font-family: Sansation;
  font-size: 12px;
  font-weight: 400;
  line-height: 13px;
  letter-spacing: 0em;
  text-align: center;
  top: -239px;
  left: 125px;
  color: #9ca3af;

  @media screen and (max-width: 768px) {
    top: -239px;
    left: 160px;
  }
}

// .product:hover {
//     box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
//     transition: 0.3s;
// }
.product-wrapper {
  width: 217px;
  height: 315px;
}

.img-product-wrapper {
  width: auto;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 43px 0 20px 0;
}

.product-img {
  width: 130px;
  height: 233px;
}

.card-body {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 210px;
}

.product-name {
  text-decoration: none;
  font-size: 16px;
  font-weight: 400;
  line-height: 19px;
  text-align: center;
  color: #111827;
  margin-bottom: 8px;
}

.product-price {
  font-size: 14px;
  font-weight: 400;
  line-height: 16px;
  text-align: center;
  color: #6b7280;
}
</style>
