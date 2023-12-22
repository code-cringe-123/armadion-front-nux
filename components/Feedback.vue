<template>
  <div class="form">
    <div class="form-title">Оставить заявку</div>
    <div class="form-text">
      Вам позвонит менеджер, который поможет сделать выбор, ля-ля-ля таполя
    </div>
    <div class="zayavka-title">Ваше имя</div>
    <input
      class="form-input form-name"
      placeholder="Григорий Григорьев"
      type="text"
      v-model="name"
    />
    <div class="zayavka-title">Телефон</div>
    <input
      class="form-input form-phone"
      placeholder="+7 (985) 233-34-21"
      type="tel"
      id="phone"
      name="phone"
      required
      v-maska
      data-maska="+7 (###) ###-##-##"
      v-model="phone"
    />
    <!-- <button class="form-btn blue-btn">Заказать звонок</button> -->
    <br />
    <!-- <button @click="sendPostRequest" class="form-btn blue-btn">Отправить</button> -->

    <UI-btn
      @click="sendPostRequest"
      mb="8px"
      type="feedback"
      class="feedback-btn"
      >Отправить</UI-btn
    >
    <div class="privacy">
      <div class="privacy-text">
        Нажимая “Отправить” вы соглашаетесь с
        <router-link class="privacy-link" to="#">
          политикой конфиденциальности</router-link
        >
      </div>
    </div>
  </div>
</template>
<!-- pattern="[0-9]{3}-[0-9]{3}-[0-9]{4}" -->
<style lang="scss">
.form {
  // max-width: 580px;
  height: 369px;

  @media screen and (max-width: 768px) {
    width: 355px;
    height: 355px;
  }

  @media screen and (max-width: 375px) {
    width: 100%;
    // height: 355px;
    padding: 0 10px;
  }
}

.form-title {
  color: #111827;
  font-size: 36px;
  font-weight: 400;
  line-height: 38px;
  margin-bottom: 20px;

  @media screen and (max-width: 768px) {
    font-size: 24px;
    font-weight: 400;
    line-height: 25px;
    margin-bottom: 16px;
  }
}

.form-text {
  color: #9ca3af;
  font-size: 16px;
  font-weight: 400;
  line-height: 22px;
  margin-bottom: 40px;

  @media screen and (max-width: 768px) {
    font-size: 16px;
    font-weight: 400;
    line-height: 22px;
    margin-bottom: 30px;
  }
}

.zayavka-title {
  color: #4b5563;
  font-size: 16px;
  font-weight: 400;
  line-height: 19px;
  margin-bottom: 4px;

  @media screen and (max-width: 768px) {
    font-size: 16px;
    font-weight: 400;
    line-height: 19px;
    margin-bottom: 8px;
  }
}

.form-input {
  width: 100%;
  height: 43px;
  padding: 12px 20px 12px 20px;
  border-radius: 4px;
  gap: 10px;
  background-color: #f3f4f6;
  border: none;
  box-sizing: border-box;
  outline: none;
  cursor: pointer;
  margin-bottom: 20px;

  @media screen and (max-width: 768px) {
    width: 355px;
    height: 43px;
    margin-bottom: 20px;
  }
  @media screen and (max-width: 375px) {
    width: 100%;
  }
}

.form-input::placeholder {
  font-size: 16px;
  font-weight: 400;
  line-height: 19px;
  color: #9ca3af;
}

.form-input::-webkit-input-placeholder {
  opacity: 1;
  transition: opacity 0.3s ease;
}

.form-input::-moz-placeholder {
  opacity: 1;
  transition: opacity 0.3s ease;
}

.form-input:-moz-placeholder {
  opacity: 1;
  transition: opacity 0.3s ease;
}

.form-input:-ms-input-placeholder {
  opacity: 1;
  transition: opacity 0.3s ease;
}

.form-input:focus::-webkit-input-placeholder {
  opacity: 0;
  transition: opacity 0.3s ease;
}

.form-input:focus::-moz-placeholder {
  opacity: 0;
  transition: opacity 0.3s ease;
}

.form-input:focus:-moz-placeholder {
  opacity: 0;
  transition: opacity 0.3s ease;
}

.form-input:focus:-ms-input-placeholder {
  opacity: 0;
  transition: opacity 0.3s ease;
}

.form-btn {
  font-size: 16px;
  font-weight: 700;
  line-height: 22px;
  width: 125px;
  height: 34px;
  padding: 6px, 10px, 6px, 10px;
  border-radius: 4px;
  gap: 10px;
  // background-color: #0EA5E9;
  border: none;
  color: white;
  cursor: pointer;
  transition: 0.3s;
  margin-bottom: 8px;

  @media screen and (max-width: 768px) {
    width: 355px;
    margin-bottom: 10px;
  }
  @media screen and (max-width: 375px) {
    width: 100%;
  }
}

.privacy {
  display: flex;
}

.privacy-text {
  font-size: 12px;
  font-weight: 400;
  line-height: 13px;
  color: #d1d5db;
  width: auto;

  @media screen and (max-width: 768px) {
    font-size: 12px;
    font-weight: 400;
    line-height: 13px;
  }
}

.privacy-link {
  font-size: 12px;
  font-weight: 400;
  line-height: 13px;
  color: #d1d5db;
  transition: 0.3s;

  @media screen and (max-width: 768px) {
    font-size: 12px;
    font-weight: 400;
    line-height: 13px;
  }
}

.privacy-link:hover {
  color: #0ea5e9;
  transition: 0.3s;
}

// .form-img {
//     @media screen and (max-width: 425px) {

//     }
// }
</style>

<script setup>
// import UIbtn from '../components/btns/UI-btn.vue'
import { ref } from "vue";
import axios from "axios";
import { vMaska } from "maska";
// import router from '../router'

// Объявите данные для привязки
const name = ref("");
const phone = ref("");

// Объявите функцию sendPostRequest
const sendPostRequest = async () => {
  try {
    // Отправьте POST-запрос
    const response = await axios({
      method: "post",
      url: "http://185.244.51.158/contact-form/",
      data: {
        user_name: name.value,
        phone_number: phone.value,
      },
    });

    // Обработайте ответ от сервера
    console.log(response);
  } catch (error) {
    // Обработайте ошибку, если она произошла
    console.error(error);
  }
};
</script>
