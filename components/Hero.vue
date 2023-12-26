<template>
  <div class="hero-wrapper">
    <div class="hero-container">
      <div class="inf-wrapper">
        <div class="hero-inf-title">Armadion the new way to do houses</div>
        <div class="hero-inf-text-wrapper">
          <div class="hero-inf-text">
            The insparation, that armada gives me is just incredable, if u
            choose the door diller armada is you choise.
          </div>
        </div>
        <!-- <ScrollToBottom class="scroll-btn" /> -->
      </div>
      <div class="img-wrapper">
        <img class="hero-img" src="../public/svg/hero/hero-img.svg" alt="" />
        <div class="img-text">New mebel collection</div>
      </div>
    </div>
  </div>
</template>

<script setup>
// import ScrollToBottom from "../components/btns/ScrollToBottom.vue";
</script>

<style lang="scss">
.hero-wrapper {
  padding-top: 175px;
  background-color: #f9fafb;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100vw;

  @media screen and (max-width: 768px) {
    padding: 90px;
  }
}

.hero-container {
  width: 1265px;
  height: 460px;
  display: flex;
  flex-direction: row;

  @media screen and (max-width: 1440px) {
    width: 1080px;
  }

  @media screen and (max-width: 1024px) {
    width: 100vw;
  }

  @media screen and (max-width: 768px) {
    width: 100vw;
    height: 448px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 0 10px;
  }
}

.inf-wrapper {
  position: relative;
  padding-top: 15px;
  width: 580px;
  height: 424px;
  left: 35px;
  z-index: 100;

  @media screen and (max-width: 768px) {
    width: 100vw;
    height: 448px;
    left: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
  }
}

.scroll-btn {
  display: none;
}

.hero-inf-text-wrapper {
  margin-bottom: 102px;
  width: 380px;

  @media screen and (max-width: 768px) {
    width: 343px;
    height: 97px;
    margin-bottom: 38px;
  }
}

.hero-inf-title {
  width: 600px;
  font-size: 64px;
  line-height: 67px;
  letter-spacing: 0em;
  text-align: left;
  margin-bottom: 32px;
  color: #111827;

  @media screen and (max-width: 768px) {
    font-size: 32px;
    font-weight: 400;
    line-height: 34px;
    margin-bottom: 24px;
    width: 343px;
  }
}

.hero-inf-text {
  font-size: 24px;
  line-height: 29px;
  letter-spacing: 0em;
  text-align: left;
  color: #9ca3af;
  margin-bottom: 12px;

  @media screen and (max-width: 768px) {
    font-size: 16px;
    font-weight: 400;
    line-height: 19px;
  }
}

.img-wrapper {
  width: 1215px;
  height: auto;
  position: absolute;
  z-index: 0;
  display: flex;
  flex-direction: column;
  align-items: flex-end;

  @media screen and (max-width: 1440px) {
    max-width: 1035px;
  }

  @media screen and (max-width: 1080px) {
    max-width: 985px;
  }

  @media screen and (max-width: 1024px) {
    max-width: 97.8000000000000000000000000000000001vw;
  }

  @media screen and (max-width: 768px) {
    width: auto;
    height: auto;
    position: relative;
    z-index: 100;
    display: flex;
    flex-direction: column;
  }
}

.hero-img {
  width: 780px;
  height: 460px;

  @media screen and (max-width: 1440px) {
    width: 564px;
    height: 330px;
  }

  @media screen and (max-width: 1024px) {
    width: 564px;
    height: 330px;
  }

  @media screen and (max-width: 768px) {
    width: 355px;
    height: 201px;
    margin-bottom: 4px;
  }

  /* margin-left: 444px; */
}

.img-text {
  font-size: 14px;
  font-weight: 400;
  line-height: 16px;
  color: #d1d5db;

  @media screen and (max-width: 768px) {
    width: 355px;
    text-align: right;
    font-size: 14px;
    font-weight: 400;
    line-height: 16px;
    color: #d1d5db;
  }
}
</style>
