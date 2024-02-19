<template>
  <div class="deliv__container">
    <div class="deliv__wrapper">
      <!-- <img src="../public/svg/zz.svg" alt="" class="deliv__img"> -->
      <div class="deliv-text__block">
        <h2 class="deliv__title">Доставка и оплата</h2>
        <!-- <p class="deliv__subtitle">
                    Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст 
                </p> -->
        <section class="first__section">
          <h3 class="section-f__title">Доставка</h3>
          <p class="section-f__subtitle" style="margin-bottom: 12px">
            Доставка с завода осуществляется за счёт заказчика и оплачивается
            отдельно.
            <br /><br />
            - По Йошкар-Оле 350 - 400 р. <br />
            - По республике Марий Эл 15-20 р./км. Расстояние считается от склада
            фабрики. <br />
            - В другие регионы – наши менеджеры оказывают помощь в поиске
            транспорта до Москвы и Московской области, Санкт-Петербурга,
            Екатеринбурга и других городов России. <br />
            - Возможен самовывоз входных дверей и фурнитуры со склада. <br />
            - Возможен оптовый заказ. <br />
            Адрес склада: Г. Йошкар-Ола, ул. Мира д. 30
            <br /><br />

            ПН-ПТ. с 8.00-17.00 (обед 12.00-13.00).
          </p>
          <!-- <p class="section-f__subtitle" style="margin-bottom: 32px;">
                        Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст 
                    </p> -->
        </section>

        <section class="first__section">
          <h3 class="section-f__title">Оплата</h3>
          <p class="section-f__subtitle" style="margin-bottom: 12px">
            Оплата только по выставленному счету для всех.
          </p>
          <!-- <p class="section-f__subtitle">
                        Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст Просто текст 
                    </p> -->
        </section>
      </div>
    </div>
  </div>
</template>

<script setup></script>

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
</style>
