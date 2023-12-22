<template>
  <div class="contacts-wrapper">
    <div class="contacts-telephone-wrapper">
      <div class="contacts-text">Телефон</div>
      <div class="contacts-title">
        <a class="contacts-a" href="tel:+78362642488">+7 (8362) 64-24-88</a>
      </div>
    </div>
    <div class="contacts-telephone-wrapper">
      <div class="contacts-text">Whatsapp</div>
      <div class="contacts-title">
        <a class="contacts-a" href="tel:+79379326000">+7 (937) 932-60-00</a>
      </div>
    </div>
    <div class="contacts-telephone-wrapper">
      <div class="contacts-text">E-mail</div>
      <div class="contacts-title">
        <a
          class="contacts-a contacts-gmail"
          href="mailto:armadionzakaz@gmail.com"
          >armadionzakaz@gmail.com</a
        >
      </div>
    </div>
  </div>
</template>

<style lang="scss">
.contacts-gmail {
  width: 95vw;
}
.contacts-a {
  color: #111827;
  text-decoration: none;
}

.contacts-wrapper {
  padding: 0 10px;
  width: 459px;

  @media screen and (max-width: 768px) {
    width: 100%;
  }
}

.contacts-telephone-wrapper {
  // width: 100vw;
  @media screen and (max-width: 768px) {
  }
}

.contacts-text {
  font-family: Sansation;
  font-size: 16px;
  font-weight: 400;
  line-height: 19px;
  letter-spacing: 0em;
  text-align: left;
  margin-bottom: 8px;
  color: #9ca3af;

  @media screen and (max-width: 768px) {
    margin-bottom: 4px;
    font-family: Sansation;
    font-size: 14px;
    font-weight: 400;
    line-height: 16px;
    letter-spacing: 0em;
    text-align: left;
  }
}

.contacts-title {
  font-family: Sansation;
  font-size: 36px;
  font-weight: 400;
  line-height: 38px;
  letter-spacing: 0em;
  text-align: left;
  margin-bottom: 40px;

  @media screen and (max-width: 425px) {
    font-family: Sansation;
    font-size: 24px;
    font-weight: 400;
    line-height: 25px;
    letter-spacing: 0em;
    text-align: left;
    margin-bottom: 20px;
  }
}
</style>
