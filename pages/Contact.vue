<template>
  <div class="form-contacts-container">
    <div class="form-contacts-wrapper-monitor">
      <div class="form-contacts-title">Контакты</div>
      <div class="contacts-form">
        <div class="form-contacts">
          <Feedback />
          <Contacts />
        </div>
        <Address />
      </div>
    </div>
    <!-- мобилка -->
    <div class="form-contacts-wrapper-mobile">
      <div class="form-contacts-title">Контакты</div>
      <div class="contacts-form">
        <div class="form-contacts">
          <Contacts />
          <Address />
        </div>
        <Feedback />
      </div>
    </div>
    <!-- ------ -->
  </div>
</template>

<script setup>
// компоненты
// import Feedback from '../components/Feedback.vue'
// import Contacts from '../components/Contacts.vue'
// import Address from '../components/Address.vue'
</script>

<style lang="scss">
.contacts-form {
  @media screen and (max-width: 768px) {
    width: 100vw;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
}

.form-contacts-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding-top: 195px;

  // padding-left: 10px;
  @media screen and (max-width: 768px) {
    // width: 100vw;
    padding-top: 110px;
    margin-bottom: 5px;
  }
}

.form-contacts-wrapper-monitor {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding: 0 10px;

  // @media screen and (max-width: 768px) {
  //   display: none;
  // }
  @media screen and (max-width: 768px) {
    display: none;
  }
}

.form-contacts-wrapper-mobile {
  display: none;

  @media screen and (max-width: 768px) {
    display: block;
    display: flex;
    flex-direction: column;
    // align-items: center;
    // justify-content: center;
    width: 100vw;
    // padding: 0 10px;
    // padding-left: 10px;
  }
}

.form-contacts-title {
  margin-bottom: 60px;
  font-family: Sansation;
  font-size: 64px;
  font-weight: 400;
  line-height: 67px;
  letter-spacing: 0em;
  // text-align: left;
  color: #111827;

  @media screen and (max-width: 768px) {
    padding: 0 10px;
    margin-bottom: 40px;
  }

  @media screen and (max-width: 425px) {
    width: 100vw;
    font-family: Sansation;
    font-size: 32px;
    font-weight: 400;
    line-height: 34px;
    letter-spacing: 0em;
    // text-align: left;
    margin-bottom: 40px;
  }
}

.form-contacts {
  // display: grid;
  // grid-template-columns: repeat(2, 1fr);
  // gap: 120px;
  display: flex;
  justify-content: space-between;
  // align-items: center;
  // width: 1180px;
  height: auto;
  margin-bottom: 60px;

  @media screen and (max-width: 768px) {
    // display: grid;
    // grid-template-columns: repeat(1, 1fr);
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 20px;
    margin-bottom: 40px;
    width: 100vw;
  }
}

.form-contacts .form-container {
  margin: 0;
}
</style>
