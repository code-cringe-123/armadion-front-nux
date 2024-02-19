<template>
  <div class="politics__container">
    <div class="politics__wrapper">
      <h1 class="politics__title">Политика конфиденциальности</h1>
      <div
        class="politics-info__container"
        v-for="(info__subtitle, info__title) in info__list"
        :key="info__title"
      >
        <h2 class="politics-info__title">{{ info__title }}</h2>
        <p
          class="politics-info__subtitle"
          v-html="formatText(info__subtitle)"
        ></p>
      </div>
    </div>
  </div>
</template>

<script src="/static/build/app.js"></script>

   <script>
       if ('serviceWorker' in navigator) {
           window.addEventListener('load', function() {
               navigator.serviceWorker.register('/service-worker.js').then(function(registration) {
                   // Registration was successful
               console.log('ServiceWorker registration successful with scope: ', registration.scope);
             }, function(err) {
               // registration failed :(
               console.log('ServiceWorker registration failed: ', err);
             }).catch(function(err) {
               console.log(err)
             });
           });
         } else {
           console.log('service worker is not supported');
         }
   </script>

<script setup>
const info__list = {
  "Предоставление информации Клиентом":
    "При покупке товаров и регистрации на Сайте Клиент предоставляет следующую информацию: Фамилия, Имя, Адрес, Адрес электронной почты, пароль для доступа к Сайту.",
  "Использование информации предоставленной Клиентом и получаемой Продавцом": `Продавец использует информацию: 
    для регистрации Клиента на Сайте;
    для выполнения своих обязательств перед Клиентом;
    для оценки и анализа работы Сайта;
    для определения победителя в акциях, проводимых Продавцом.

    Продавец вправе направлять Клиенту сообщения рекламно-информационного характера, если клиент подписался на них. Если Клиент не желает получать рассылки от Продавца, он должен изменить соответствующие настройки подписки в личном кабинете на сайте. Для входа необходимо ввести логин и пароль.`,
  "Разглашение информации, полученной Продавцом": `Продавец обязуется не разглашать полученную от Клиента информацию.

    Не считается нарушением предоставление Продавцом информации агентам и третьим лицам, действующим на основании договора с Продавцом, для исполнения обязательств перед Клиентом.

    Не считается нарушением обязательств разглашение информации в соответствии с обоснованными и применимыми требованиями закона.

    Продавец вправе использовать технологию "cookies". "Cookies" не содержат конфиденциальную информацию и не передаются третьим лицам.

    Продавец получает информацию об ip-адресе посетителя Сайта. Данная информация не используется для установления личности посетителя.

    Продавец не несет ответственности за сведения, предоставленные Клиентом на Сайте в общедоступной форме.

    Продавец не несёт ответственность за доступ к личному кабинету клиента третьих лиц в случае, если логин и пароль от личного кабинета попал к этим лицам по вине клиента.`,
};

const formatText = (text) => {
  return text.replace(/\./g, ".<br><br>");
};
</script>

<style lang="scss">
.politics__container {
  margin-top: 150px;
  display: flex;
  align-items: center;
  justify-content: center;
  /* max-width: 1000px; */
  @media screen and (max-width: 1024px) {
    margin-top: 100px;
  }
}
.politics__wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  max-width: 1000px;
  @media screen and (max-width: 1024px) {
    padding: 0 10px;
  }
  @media screen and (max-width: 500px) {
    padding: 0 10px;
    width: 100vw;
  }
}
.politics__title {
  margin-bottom: 40px;
  font-family: Sansation;
  font-size: 64px;
  font-weight: 400;
  line-height: 67px;
  letter-spacing: 0em;
  color: var(--title-color);
  @media screen and (max-width: 1024px) {
    font-size: 44px;
  }
  @media screen and (max-width: 500px) {
    font-size: 32px;
    line-height: 34px;
    margin-bottom: 20px;
  }
  @media screen and (max-width: 350px) {
    font-size: 30px;
    line-height: 30px;
    margin-bottom: 20px;
  }
  @media screen and (max-width: 340px) {
    font-size: 28px;
  }
}

.politics-info__title {
  color: var(--title-color);
  font-size: 28px;
  font-weight: 400;
  line-height: 38px;
  margin-bottom: 20px;
  @media screen and (max-width: 1024px) {
    margin-bottom: 0;
  }
  @media screen and (max-width: 500px) {
    font-size: 20px;
    line-height: 20px;
    line-height: 19px;
    margin-bottom: 8px;
  }
}

.politics-info__subtitle {
  font-family: Sansation;
  font-size: 20px;
  font-weight: 400;
  line-height: 22px;
  letter-spacing: 0em;
  text-align: left;
  margin-bottom: 32px;
  color: #6b7280;
  @media screen and (max-width: 1024px) {
    margin-bottom: 0;
  }
  @media screen and (max-width: 500px) {
    margin-bottom: 16px;
    font-size: 16px;
    font-weight: 400;
    line-height: 22px;
  }
}
</style>
