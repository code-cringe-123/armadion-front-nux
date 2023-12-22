<template>
  <button
    class="catalog-btn-more"
    :style="{ width: width, height: height, borderRadius: br }"
    type="button"
  >
    <slot></slot>
  </button>
</template>

<script setup>
const props = defineProps({
  width: {
    type: String,
    required: false,
  },
  height: {
    type: String,
    required: false,
  },
  borderRadius: {
    type: String,
    required: false,
  },
});
</script>
<style lang="scss">
.catalog-btn-more {
  margin-top: 24px;
  width: 236px;
  height: 35px;
  padding: 8px 66px 8px 66px;
  border-radius: 50px;
  border: 1px solid #d1d5db;
  color: #4b5563;
  background-color: transparent;
  font-weight: 400;
  font-style: 16px;
  transition: 0.3s;
  cursor: pointer;
  line-height: 19px;

  @media screen and (max-width: 425px) {
    margin-top: 16px;
  }
}

.catalog-btn-more:hover {
  background-color: #4b5563;
  color: #d1d5db;
  transition: 0.3s;
}

.catalog-btn-more:active {
  background-color: #d1d5db;
  color: #4b5563;
  transition: 0.3s;
}
</style>
