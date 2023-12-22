<template>
  <div class="container">
    <div class="content">
      <Theheader />
      <slot></slot>
    </div>
    <Thefooter />
  </div>
</template>

<style>
.container {
  margin: auto;
  background-color: #f9fafb;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  width: 100vw;
}

.content {
  flex: 1;
}
</style>
