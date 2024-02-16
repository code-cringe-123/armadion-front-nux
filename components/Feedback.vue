<template>
  <div class="form">
    <div class="form-title">Оставить заявку</div>
    <div class="form-text">
      Вам позвонит менеджер, который поможет сделать выбор.
    </div>
    <div class="zayavka-title">Ваше имя и фамилия</div>
    <input
      class="form-input form-name"
      placeholder="Григорий Григорьев"
      type="text"
      v-model="name"
      @input="validateName"
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
      @input="validatePhone"
    />
    <!-- <button class="form-btn blue-btn">Заказать звонок</button> -->
    <br />
    <!-- <button @click="sendPostRequest" class="form-btn blue-btn">Отправить</button> -->

    <UI-btn
      @click="sendPostRequestAndShowPopup"
      mb="8px"
      type="feedback"
      class="feedback-btn"
    >
      Отправить
    </UI-btn>
    <div class="privacy">
      <div class="privacy-text">
        Нажимая “Отправить” вы соглашаетесь с
        <NuxtLink class="privacy-link" to="/Politics">
          политикой конфиденциальности</NuxtLink
        >
      </div>
    </div>
  </div>

  <div class="PopUp" v-if="showPopup && submitClicked" @click="closePopup">
    <!-- Попап с подтверждением -->
    <div class="Pop ActivePopUp">
      <img class="PopImg" src="../public/svg/approvePopup.svg" alt="" />
      <p class="describe">
        Ваш заказ оформлен, в течение 24 часов с вами свяжется менеджер
      </p>
    </div>
  </div>

  <div class="PopUp" v-else-if="submitClicked" @click="closePopup">
    <!-- Попап с предупреждением -->
    <div class="Pop ActivePopUp">
      <img class="PopImg" src="../public/svg/closepopUp.svg" alt="" />
      <p class="describe">
        Пожалуйста, введите валидные данные, чтобы мы могли с вами связаться!
      </p>
    </div>
  </div>
</template>
<!-- pattern="[0-9]{3}-[0-9]{3}-[0-9]{4}" -->
<script setup>
import { ref } from "vue";
import axios from "axios";
import { vMaska } from "maska";

// Дата пользователя
const currentDate = new Date();
const day = currentDate.getDate().toString().padStart(2, "0");
const month = (currentDate.getMonth() + 1).toString().padStart(2, "0"); // Месяцы в JavaScript начинаются с 0
const year = currentDate.getFullYear();
const formattedDate = `${day}/${month}/${year}`;
console.log(formattedDate);

// Время пользователя
const hours = currentDate.getHours().toString().padStart(2, "0");
const minutes = currentDate.getMinutes().toString().padStart(2, "0");
const seconds = currentDate.getSeconds().toString().padStart(2, "0");

const formattedTime = `${hours}:${minutes}:${seconds}`;
console.log(formattedTime);

const name = ref("");
const phone = ref("");
const showPopup = ref(false);

const nameValid = ref(false);
const phoneValid = ref(false);

const validateName = () => {
  const nameWithoutSpaces = name.value.replace(/\s/g, "");
  const isNameValid = nameWithoutSpaces.length >= 2;
  nameValid.value = isNameValid;
};

const validatePhone = () => {
  const phoneDigitsOnly = phone.value.replace(/\D/g, "");
  const isPhoneValid = phoneDigitsOnly.length >= 11;
  phoneValid.value = isPhoneValid;
};
const submitClicked = ref(false); // Переменная состояния для отслеживания нажатия на кнопку "Отправить"

const sendPostRequestAndShowPopup = async () => {
  if (nameValid.value && phoneValid.value) {
    await sendPostRequest(); // Выполнить отправку запроса
    submitClicked.value = true;
    showPopup.value = true;
  } else {
    submitClicked.value = true;
    showPopup.value = false;
  }
};

const sendPostRequest = async () => {
  if (nameValid.value && phoneValid.value) {
    try {
      const response = await axios({
        method: "post",
        url: "https://sheet.best/api/sheets/48a0e185-2f27-4b56-960e-eddfd2a3a70b",
        data: {
          Date: formattedDate,
          Time: formattedTime,
          Name: name.value,
          "Phone number": phone.value.slice(1),
          "Status of application": "в обработке",
        },
      });

      console.log(response);
    } catch (error) {
      console.error(error);
    }
  }
};

const closePopup = () => {
  showPopup.value = false;
  submitClicked.value = false;
};
</script>

<style lang="scss">
.required-field {
  background-color: #f8d7da;
}
.required-field:hover {
  background-color: #fbc2cc;
}
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

// popup
.PopUp {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: rgba(0, 0, 0, 0.3);
  z-index: 1;
}

.DisabledPopUp {
  display: none;
}

.Pop.ActivePopUp {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: center;
  text-align: center;
  width: 392px;
  height: 229px;
  border-radius: 16px;
  background: #fff;

  .PopImg {
    padding-top: 15px;
    display: block;
    margin: 0 auto;
  }
  .describe {
    color: var(--gray-500, #6b7280);
    font-family: Sansation;
    font-size: 16px;
    font-style: normal;
    font-weight: 400;
    padding: 0 5px;
    line-height: 120%;
  }
}

.form-btn-div {
  display: flex;
  color: var(--gray-400, #9ca3af);
}

.arrow {
  position: relative;
  top: 3px;
}
</style>
