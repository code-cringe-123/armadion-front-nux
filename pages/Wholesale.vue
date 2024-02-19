<template>
  <section class="wholesale">
    <div class="wholesale__wrapper">
      <h1 class="wholesale-title">
        Входные металлические двери оптом в Йошкар-Оле
      </h1>
      <p class="wholesale-subtitle">
        Интернет-магазин «Армада» предлагает купить в Йошкар-Оле входные
        металлические двери оптом по заводским ценам от производителя, гарантия
        качества. Изготовление входных дверей выполняется на заказ по ГОСТ
        31173-2016 на заводе Йошкар-Олы. Осуществляем доставку товаров по всей
        России.
        <br />
        Вы можете оформить оптовый заказ стальных полотен по своим размерам, с
        выбранной фурнитурой и покрытием или выбрать модели из каталога.
        <br />
      </p>
      <div class="wholesale-examples">
        Ознакомьтесь с примерами
        <span
          ><NuxtLink to="/Catalog" class="wholesale-examples__link"
            >каталога</NuxtLink
          ></span
        >. (Оптовая стоимость ниже)
      </div>
      <div class="wholesale-order">
        <h3 class="wholesale-title wholesale-order__title">Как заказать?</h3>
        <p
          class="wholesale-order__subtitle wholesale-subtitle"
          style="margin-bottom: 12px"
        >
          Чтобы оформить оптовый заказ или заявку на изготовления входных
          металлических дверей по своим размерам, свяжитесь с менеджерами нашей
          компании по телефону +7 (8362) 64-24-88 или отправьте запрос на
          электронную почту
          <a
            href="mailto:armadionzakaz@gmail.com"
            class="wholesale-order__email"
            >armadionzakaz@gmail.com</a
          >.
          <br />
          <br />
          Мы находимся по адресу: Россия, г. Йошкар-Ола, ул. Мира, 30. Время
          работы: по будням с 9 до 18 часов.
        </p>
      </div>
      <div class="wholesale-advantages">
        <h3 class="wholesale-advantages__title wholesale-title">
          Выгодные условия и преимущества
        </h3>
        <p class="wholesale-advantages__subtitle wholesale-subtitle">
          Учитывая большой спрос на модели из качественной стали, строительные
          организации и региональные дилеры всегда испытывают заинтересованность
          в надежном и стабильном поставщике продукции.
          <br /><br />
          Преимущество поставок крупных объемов стальных дверей:
          <ul style="list-style-type: disc; padding-left: 40px; margin-bottom: 12px;">
            <li><span class="wholesale-advantages__subtitle wholesale-subtitle">более низкая стоимость, чем при штучном приобретении товаров. Сумма заказа зависит от: конкретных моделей, комплектности фурнитуры и покрытий, объема партии;</span></li>
            <li><span class="wholesale-advantages__subtitle wholesale-subtitle">Застройщик или продавец получает товар со скидкой, производитель увеличивает свою прибыль за счет больших объемов, а расширение географии сбыта, повышая деловой имидж предприятия;</span></li>
            <li><span class="wholesale-advantages__subtitle wholesale-subtitle">Условия сотрудничества включают гибкую систему скидок для постоянных заказчиков, информационно-техническую поддержку на всех стадиях взаимодействия, размещение информации о вашем магазине на нашем сайте, совместное участие выставках, семинарах, рекламных кампаниях с целью увеличения продаж.</span></li>
          </ul>
        </p>
         <p class="wholesale-advantages__subtitle wholesale-subtitle" style="margin-bottom: 32px;">
            Компания «Армада» на строительном рынке более 10 лет. В настоящее время годовые объемы выпуска железных дверей превышают показатель 25 тысяч единиц. На производстве установлено инновационное оборудование с ЧПУ, что позволяет изготавливать разные конструкции с высокой точностью исполнения. Модельный ряд регулярно расширяется. Вы можете оформить оптовый заказ на изготовление стальных входных, уличных, противопожарных дверей для дома, квартиры, офисного или производственного помещения.
        </p>
        <h3 class="wholesale-advantages__title wholesale-title">Характеристики</h3>
        <p class="wholesale-advantages__subtitle wholesale-subtitle" style="margin-bottom: 12px;">
            <ul style="list-style-type: disc; padding-left: 40px; margin-bottom: 12px;">
                <li><span class="wholesale-advantages__subtitle wholesale-subtitle">дизайнерская наружная и внутренняя отделка;</span></li>
                <li><span class="wholesale-advantages__subtitle wholesale-subtitle">фурнитура популярных брендов «Гардиан», «Фуаро», «Armadillo», «Apecs, «Кале», «Моттура», «Чиза»;</span></li>
                <li><span class="wholesale-advantages__subtitle wholesale-subtitle">полотна выполнены из качественной стали толщиной от 1,5 мм и профильного проката.</span></li>
            </ul>
        </p>
      </div>
      <Feedback/>
    </div>
  </section>
</template>

<script></script>

<style>
.wholesale {
  width: 100%;
  padding: 70px 0 0;
  @media screen and (max-width: 1024px) {
    padding-top: 50px;
    padding-left: 10px;
    padding-right: 10px;
  }
}
.wholesale__wrapper {
  max-width: 1010px;
  margin: 0 auto 100px;
  @media screen and (max-width: 880px) {
    max-width: 350px;
  }
}
.wholesale-title {
  color: var(--gray-700, #374151);
  font-family: Sansation;
  font-size: 64px;
  font-weight: 400;
  line-height: 105%;
  margin: 60px 0 52px;
}
.wholesale-subtitle {
  margin-bottom: 32px;
  color: var(--gray-500, #6b7280);
}
.wholesale-examples {
  font-weight: 700;
  margin-bottom: 10px;
}
.wholesale-examples__link {
  text-decoration: none;
  color: #007bff;
  transition: all 0.1s;
}
.wholesale-order__title,
.wholesale-advantages__title {
  font-size: 36px;
  font-style: normal;
  margin: 0;
  margin-bottom: 16px;
}
.wholesale-order__email {
  color: var(--gray-500, #6B7280);
  transition: 0.1s;
}
.wholesale-order__email:hover {
  color: #0052aa;
  transition: 0.1s;
}
@media (max-width: 1280px) {
  .wholesale__wrapper {
    max-width: 900px;
  }
}
@media (max-width: 1024px) {
  .wholesale__wrapper {
    max-width: 768px;
  }
  .wholesale-title {
    font-size: 3.125rem;
    margin-bottom: 40px;
  }
  .wholesale-order__title,
  .wholesale-advantages__title {
    font-size: 36px;
  }
}
@media (max-width: 899px) {
  .wholesale__wrapper {
    max-width: 568px;
  }
  .wholesale-title {
    font-size: 2.625rem;
    margin-top: 40px;
    margin-bottom: 30px;
  }
  .wholesale-order__title,
  .wholesale-advantages__title {
    font-size: 30px;
  }
}
@media (max-width: 768px) {
  .wholesale__wrapper {
    max-width: 450px;
  }
  .wholesale-title {
    font-size: 2rem;
  }
  .wholesale-order__title,
  .wholesale-advantages__title {
    font-size: 28px;
  }
}
@media (max-width: 568px) {
  .wholesale__wrapper {
    max-width: 330px;
  }
  .wholesale-title {
    font-size: 1.3rem;
    margin-bottom: 20px;
  }
  .wholesale-subtitle,
  .wholesale-examples {
    font-size: .8125rem;
  }
  .wholesale-order__title,
  .wholesale-advantages__title {
    font-size: 28px;
  }
}
</style>
