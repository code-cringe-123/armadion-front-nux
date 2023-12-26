<template>
  <div class="measurements-container">
    <div class="measurements-wrapper">
      <div class="measurements-left-side">
        <div class="measurements-title">Сделать замеры</div>
        <div class="measurements-text-wrapper">
          <div class="measurements-text">
            Вы можете вызвать замерщика, если не уверены, что наши двери
            подойдут в ваши проемы.<span class="measurements-text-bold"
              >Это Бесплатно.</span
            >
          </div>
        </div>
        <div class="measurements-options">
          Замерщик: <br />
          - сделает замеры <br />
          - предложит подходящие модели <br />
          - поможет оформить заказ
        </div>
        <Measurements-btn>Вызвать установщика</Measurements-btn>
      </div>
      <div class="measurements-right-side">
        <img
          class="measurements-img-1"
          src="../public/svg/measurements-img-1.svg"
          alt="measurements-img"
        />
        <img
          class="measurements-img-2"
          src="../public/svg/measurements-img-2.svg"
          alt="measurements-img"
        />
      </div>
    </div>
  </div>
</template>

<style lang="scss">
.measurements-text-wrapper {
  display: flex;
}

.measurements-left-side {
  width: 579px;
  display: flex;
  flex-direction: column;
  justify-content: start;
  margin-right: 20px;

  @media screen and (max-width: 768px) {
    // width: 335px;
    width: 100%;
    padding: 0 10px;
    // height: 176px;
    // padding: 0 10px;
    display: flex;
    align-items: center;
    margin-right: 0;
  }
}

.measurements-img-1 {
  border-radius: 8px;
  width: 521px;
  height: 413px;

  @media screen and (max-width: 1024px) {
    height: 225px;
  }

  @media screen and (max-width: 768px) {
    display: none;
  }
}

.measurements-right-side {
  height: 354px;
}

.measurements-img-2 {
  border-radius: 0px;
  width: 355px;
  // height: 216px;
  display: none;

  @media screen and (max-width: 768px) {
    display: block;
    margin-bottom: 24px;
  }
}

.measurements-options {
  font-family: Sansation;
  font-size: 16px;
  font-weight: 400;
  line-height: 22px;
  letter-spacing: 0em;
  text-align: left;
  margin-bottom: 24px;
  color: #6b7280;

  @media screen and (max-width: 768px) {
    // width: 335px;
    width: 100%;
    margin-bottom: 50px;
    font-family: Sansation;
    font-family: Sansation;
    font-size: 16px;
    font-weight: 700;
    line-height: 22px;
    letter-spacing: 0em;
    text-align: left;
    font-family: Sansation;
    font-size: 16px;
    font-weight: 400;
    line-height: 22px;
    letter-spacing: 0em;
    text-align: left;
  }
  @media screen and (max-width: 340px) {
    margin-bottom: 25px;
  }
}

.measurements-text-bold {
  font-family: Sansation;
  font-size: 16px;
  font-weight: 700;
  line-height: 22px;
  letter-spacing: 0em;
  text-align: left;
  margin-left: 4px;

  @media screen and (max-width: 768px) {
  }
}

.measurements-text {
  font-family: Sansation;
  font-size: 16px;
  font-weight: 400;
  line-height: 22px;
  letter-spacing: 0em;
  text-align: left;
  margin-bottom: 32px;
  color: #6b7280;

  /* display: flex;
    flex-direction: row; */
  @media screen and (max-width: 768px) {
    margin-bottom: 30px;
    font-family: Sansation;
    font-size: 16px;
    font-weight: 700;
    line-height: 22px;
    letter-spacing: 0em;
    text-align: left;

    //styleName: base;
    font-family: Sansation;
    font-size: 16px;
    font-weight: 400;
    line-height: 22px;
    letter-spacing: 0em;
    text-align: left;
  }
}

.measurements-title {
  color: #111827;
  font-family: Sansation;
  font-size: 36px;
  font-weight: 400;
  line-height: 38px;
  letter-spacing: 0em;
  text-align: left;
  margin-bottom: 12px;

  @media screen and (max-width: 768px) {
    width: 100%;
    font-family: Sansation;
    font-size: 24px;
    font-weight: 400;
    line-height: 25px;
    letter-spacing: 0em;
    text-align: left;
  }
}

.measurements-wrapper {
  width: 1180px;
  height: 473px;
  background-color: #f3f4f6;
  display: flex;
  border-radius: 24px;
  padding: 30px;

  @media screen and (max-width: 1024px) {
    height: 414px;
    width: 800px;
  }

  @media screen and (max-width: 768px) {
    width: 355px;
    height: 586px;
    border-radius: 8px;
    display: flex;
    flex-direction: column-reverse;
    align-items: center;
    justify-content: flex-end;
    overflow: hidden;
    padding: 0 0 24px 0;
  }
}

.measurements-container {
  width: 100vw;
  margin-top: 180px;
  display: flex;
  align-items: center;
  justify-content: center;

  @media screen and (max-width: 1024px) {
    padding: 0 65px;
  }

  @media screen and (max-width: 768px) {
    height: 586px;
  }
}
</style>

<script setup>
// import btn from '../components/btns/Measurements-btn.vue'
</script>
