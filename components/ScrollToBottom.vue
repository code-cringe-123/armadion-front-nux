<template>
  <div class="scroll-btn-wrapper">
    <img
      class="scroll-btn-img"
      src="../public/svg/scroll_to_bottom.svg"
      alt="scroll to bottom"
    />
    <div class="btn-name">scroll to bottom</div>
  </div>
</template>

<style>
.scroll-btn-wrapper {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: start;
  cursor: pointer;
}

.scroll-btn-img {
  margin-right: 8px;
}

.btn-name {
  font-family: Sansation;
  font-size: 14px;
  font-weight: 400;
  line-height: 16px;
  color: #d1d5db;
}
</style>
