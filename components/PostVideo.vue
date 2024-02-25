<template>
  <div class="postVideo-wrapper">
    <video
      controls="controls"
      class="postVideo-img"
      :src="postvideo.src"
      alt="Post Video"
    ></video>
    <div class="postVideo-body">
      <span class="postVideo-title" href="#">{{ postvideo.title }}</span>
      <span class="postVideo-text">{{ postvideo.text }}</span>
    </div>
  </div>
</template>

<script setup>
const props = defineProps(["postvideo"]);
</script>

<style lang="scss">
.postVideo-wrapper {
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

  @media screen and (max-width: 525px) {
    width: 355px;
    height: 532px;
    overflow-x: hidden;
  }
}

.postVideo-img {
  width: 100%;
  height: 284px;
  margin-bottom: 24px;

  @media screen and (max-width: 525px) {
    margin-top: -40px;
  }

  @media screen and (max-width: 425px) {
    margin-top: -40px;
    width: 355px;
    height: 284px;
    margin-bottom: 16px;
  }
}

.postVideo-body {
  display: flex;
  flex-direction: column;
  align-items: start;
  height: 145px;

  // @media screen and (max-width: 425px) {
  //   height: 145px;
  // }
}

.postVideo-title {
  text-decoration: none;
  font-size: 24px;
  font-weight: 400;
  line-height: 29px;
  color: #111827;
  margin: 0 0 12px 20px;

  @media screen and (max-width: 425px) {
    margin: 0 10px 12px 10px;
    font-size: 24px;
    font-weight: 400;
    line-height: 29px;
  }
}

.postVideo-text {
  font-size: 16px;
  font-weight: 400;
  line-height: 22px;
  color: #9ca3af;
  padding: 0 20px;

  @media screen and (max-width: 425px) {
    padding: 0 10px;
    font-size: 16px;
    font-weight: 400;
    line-height: 22px;
  }
}
</style>
