<template>
    <div class="deliv__container">
        <div class="deliv__wrapper">
            <div class="deliv-text__block">
                <h2 class="deliv__title">Входные металлические двери оптом в Йошкар-Оле</h2>
                <p class="deliv__subtitle">
                    Интернет-магазин «Армада» предлагает купить в Йошкар-Оле входные металлические двери оптом по заводским ценам от производителя, гарантия качества. Изготовление входных дверей выполняется на заказ по ГОСТ 31173-2016 на заводе Йошкар-Олы. Осуществляем доставку товаров по всей России.
                    <br>
                    Вы можете оформить оптовый заказ стальных полотен по своим размерам, с выбранной фурнитурой и покрытием или выбрать модели из каталога.
                    <br>
                </p>
                <div class="doors__wholesale__catalog__link__text">
                        Ознакомьтесь с примерами <span><NuxtLink to="/Catalog" class="doors__wholesale__catalog__link">каталога</NuxtLink></span>. (Оптовая стоимость ниже)
                </div>
                <br>
                <section class="first__section">
                    <h3 class="section-f__title">Как заказать?</h3>
                    <p class="section-f__subtitle" style="margin-bottom: 12px;">
                        Чтобы оформить оптовый заказ или заявку на изготовления входных металлических дверей по своим размерам, свяжитесь с менеджерами нашей компании по телефону +7 (8362) 64-24-88 или отправьте запрос на электронную почту <a href="mailto:armadionzakaz@gmail.com" class="doors__wholesale__email">armadionzakaz@gmail.com</a>.
                        <br>
                        <br>
                        Мы находимся по адресу:  Россия, г. Йошкар-Ола, ул. Мира, 30. Время работы: по будням с 9 до 18 часов.
                    </p>
                    <h3 class="section-f__title">Выгодные условия и преимущества</h3>
                    <p class="section-f__subtitle" style="margin-bottom: 12px;">
                        Учитывая большой спрос на модели из качественной стали, строительные организации и региональные дилеры всегда испытывают заинтересованность в надежном и стабильном поставщике продукции.
                        <br>
                        <br>
                        Преимущество поставок крупных объемов стальных дверей:
                        <ul style="list-style-type: disc; padding-left: 40px; margin-bottom: 12px;">
                            <li><span class="section-f__subtitle">более низкая стоимость, чем при штучном приобретении товаров. Сумма заказа зависит от: конкретных моделей, комплектности фурнитуры и покрытий, объема партии;</span></li>
                            <li><span class="section-f__subtitle">Застройщик или продавец получает товар со скидкой, производитель увеличивает свою прибыль за счет больших объемов, а расширение географии сбыта, повышая деловой имидж предприятия;</span></li>
                            <li><span class="section-f__subtitle">Условия сотрудничества включают гибкую систему скидок для постоянных заказчиков, информационно-техническую поддержку на всех стадиях взаимодействия, размещение информации о вашем магазине на нашем сайте, совместное участие выставках, семинарах, рекламных кампаниях с целью увеличения продаж.</span></li>
                        </ul>
                    </p>
                    <p class="section-f__subtitle" style="margin-bottom: 32px;">
                        Компания «Армада» на строительном рынке более 10 лет. В настоящее время годовые объемы выпуска железных дверей превышают показатель 25 тысяч единиц. На производстве установлено инновационное оборудование с ЧПУ, что позволяет изготавливать разные конструкции с высокой точностью исполнения. Модельный ряд регулярно расширяется. Вы можете оформить оптовый заказ на изготовление стальных входных, уличных, противопожарных дверей для дома, квартиры, офисного или производственного помещения.
                    </p>
                    <h3 class="section-f__title">Характеристики</h3>
                    <p class="section-f__subtitle" style="margin-bottom: 12px;">
                        <ul style="list-style-type: disc; padding-left: 40px; margin-bottom: 12px;">
                            <li><span class="section-f__subtitle">дизайнерская наружная и внутренняя отделка;</span></li>
                            <li><span class="section-f__subtitle">фурнитура популярных брендов «Гардиан», «Фуаро», «Armadillo», «Apecs, «Кале», «Моттура», «Чиза»;</span></li>
                            <li><span class="section-f__subtitle">полотна выполнены из качественной стали толщиной от 1,5 мм и профильного проката.</span></li>
                        </ul>
                    </p>
                </section>
                <Feedback/>
            </div>
        </div>
    </div>
</template>

<script setup>

</script>
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
<style>
<style>
.deliv__container {
  padding: 160px 0 0;
  @media screen and (max-width: 1024px) {
    padding-top: 50px;
    padding-left: 10px;
    padding-right: 10px;
  }
}

.deliv__img {
  display: block;

  margin: 0 auto;
  @media screen and (max-width: 880px) {
    min-width: 100%;
  }
  @media screen and (max-width: 425px) {
    width: 100vw;
  }
}

.deliv-text__block {
  max-width: 980px;
  margin: 0 auto 100px;
  @media screen and (max-width: 880px) {
    max-width: 350px;
  }
}

.deliv__title {
  color: var(--gray-700, #374151);

  font-family: Sansation;
  font-size: 64px;
  font-weight: 400;
  line-height: 105%;
  margin: 60px 0 52px;
  @media screen and (max-width: 880px) {
    color: var(--gray-700, #374151);

    font-family: Sansation;
    font-size: 32px;
    font-style: normal;
    font-weight: 400;
    line-height: 105%;
  }
}

.deliv__subtitle {
  margin-bottom: 32px;
  color: var(--gray-500, #6b7280);
  @media screen and (max-width: 880px) {
    color: var(--gray-500, #6b7280);

    font-family: Sansation;
    font-size: 16px;
    font-style: normal;
    font-weight: 400;
    line-height: 120%;
  }
}

.section-f__title {
  color: var(--gray-700, #374151);
  font-family: Sansation;
  font-size: 36px;
  font-style: normal;
  font-weight: 400;
  line-height: 105%;
  margin-bottom: 16px;
  @media screen and (max-width: 880px) {
    color: var(--gray-700, #374151);
    font-family: Sansation;
    font-size: 24px;
    font-style: normal;
    font-weight: 400;
    line-height: 105%;
  }
}

.section-f__subtitle {
  color: var(--gray-500, #6b7280);
  font-family: Sansation;
  font-size: 16px;
  font-style: normal;
  font-weight: 400;
  line-height: 120%;

  @media screen and (max-width: 880px) {
    color: var(--gray-500, #6b7280);

    font-family: Sansation;
    font-size: 16px;
    font-style: normal;
    font-weight: 400;
    line-height: 120%;
  }
}

.doors__wholesale__email {
    color: var(--gray-500, #6B7280);
    transition: 0.1s;
}
.doors__wholesale__email:hover {
    color: #0052aa;
    transition: 0.1s;
}
.doors__wholesale__catalog__link__text {
    font-weight: bold;
}
.doors__wholesale__catalog__link {
    text-decoration: none;
    color: #007BFF;
    transition: 0.1s;
}
.doors__wholesale__catalog__link:hover {
    color: #0052aa;
    text-decoration: underline;
    transition: 0.1s;
}
</style>

