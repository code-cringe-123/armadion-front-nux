<template>
  <div class="post-wrapper">
    <img class="post-img" :src="post.img" alt="Post image" />
    <div class="post-body">
      <span class="post-title" href="#">{{ post.title }}</span>
      <span class="post-text">{{ post.text }}</span>
    </div>
  </div>
</template>

<script setup>
const props = defineProps(["post"]);
</script>

<style lang="scss">
.post-wrapper {
  max-width: 580px;
  max-height: 528px;
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: #f3f4f6;

  @media screen and (max-width: 1440px) {
    width: 500px;
    overflow-x: hidden;
  }

  @media screen and (max-width: 425px) {
    width: 355px;
    height: 532px;
    overflow-x: hidden;
  }
}

.post-img {
  max-width: 100vw;
  max-height: 383px;
  margin-bottom: 24px;

  @media screen and (max-width: 1440px) {
  }

  @media screen and (max-width: 425px) {
    // width: 355px;
    height: 377px;
    margin-bottom: 16px;
  }
}

.post-body {
  display: flex;
  flex-direction: column;
  align-items: start;
  height: 145px;

  // @media screen and (max-width: 425px) {
  //   height: 145px;
  // }
}

.post-title {
  text-decoration: none;
  font-size: 24px;
  font-weight: 400;
  line-height: 29px;
  color: #111827;
  margin: 0 0 12px 20px;

  @media screen and (max-width: 425px) {
    font-size: 24px;
    font-weight: 400;
    line-height: 29px;
  }
}

.post-text {
  font-size: 16px;
  font-weight: 400;
  line-height: 22px;
  color: #9ca3af;
  padding: 0 20px;

  @media screen and (max-width: 425px) {
    font-size: 16px;
    font-weight: 400;
    line-height: 22px;
  }
}
</style>
