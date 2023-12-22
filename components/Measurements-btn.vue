<template>
  <button class="measurements-btn" type="button">
    <slot></slot>
  </button>
</template>

<style lang="scss">
.measurements-btn {
  width: 230px;
  height: 51px;
  padding: 16px, 30px, 16px, 30px;
  border-radius: 12px;
  border: 1px solid #4b5563;
  gap: 10px;
  color: #4b5563;
  background-color: transparent;
  font-family: Sansation;
  font-size: 16px;
  font-weight: 400;
  line-height: 19px;
  letter-spacing: 0em;
  text-align: center;
  cursor: pointer;
  transition: 0.3s;

  @media screen and (max-width: 768px) {
    width: 100%;
    height: 51px;
  }
}

.measurements-btn:hover {
  background-color: #374151;
  color: #f9fafb;
  transition: 0.3s;
}

.measurements-btn:active {
  color: #4b5563;
  background-color: transparent;
  transition: 0.3s;
}
</style>
