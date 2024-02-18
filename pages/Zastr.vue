<template>
    <div class="zastr__container">
        <div class="zastr__wrapper">
            <!-- <img src="../public/svg/zz.svg" alt="" class="zastr__img"> -->
            <div class="zastr-text__block">
                <h2 class="zastr__title">Входные! двери из Йошкар-Олы: специальные условия для застройщиков</h2>
                <p class="zastr__subtitle">
                    Компания «Армадион» предлагает оптом двери для застройщиков. Конструкции выпускаются в соответствии с требованиями ГОСТ 31173-2016. Мы изготавливаем входные металлические двери на собственном предприятии, предоставляем большой выбор моделей и гарантии качества.
                </p>
                <section class="first__section">
                    <h3 class="section-f__title">Характеристики</h3>
                    <p class="section-f__subtitle" style="margin-bottom: 12px;">
                        временные. Получив квартиру, жильцы обычно стремятся установить новые в соответствии со своими пожеланиями. Иногда они ограничиваются дополнительной облицовкой, утеплением, заменой запорных механизмов. Для подрядчика же важным критерием является цена. Учитывая эти факторы, для строительных дверей характерны:
                        <ul style="list-style-type: disc; padding-left: 40px; margin-bottom: 12px;">
                            <li><span class="section-f__subtitle">простота конструкции;</span></li>
                            <li><span class="section-f__subtitle">легкость установки и демонтажа;</span></li>
                            <li><span class="section-f__subtitle">минимум декора, гладкие поверхности.</span></li>
                        </ul>
                    </p>
                    <p class="section-f__subtitle" style="margin-bottom: 32px;">
                        В то же время конструкции должны обладать набором эксплуатационных параметров и обеспечивать свое назначение. Требования к габаритам, прочности, материалам, устойчивости к взлому, фурнитуре, тепло- и звукоизоляции регламентируются ГОСТ 31173-2016, а также рядом других нормативных документов: СП 50.13330.2012, СП 50.13330.2011, СП 54.13330.2011.
                        <br>
                        <br>
                        Двери для застройщиков изготавливаются по размерам типовых проемов, комплектуются монтажными элементами, ручками, глазками, запирающими механизмами.
                    </p>
                </section>

                <section class="first__section">
                    <h3 class="section-f__title">Наши предложения</h3>
                    <p class="section-f__subtitle" style="margin-bottom: 12px;">
                        Компания «Армадион» на строительном рынке более 10 лет. В настоящее время годовые объемы выпуска дверей превышают показатель 25 тысяч единиц. На производстве установлено инновационное оборудование с ЧПУ, что позволяет изготавливать разные модели с высокой точностью исполнения.
                        <br>
                        <br>
                        Мы заинтересованы в сотрудничестве со строительными организациями и готовы изготавливать оптовые партии дверных конструкций для новостроек на взаимовыгодных условиях. Преимущество поставок крупных объемов продукции заключается в более низкой цене, чем при штучном приобретении товаров. Окончательная стоимость зависит от конкретных моделей, комплектности фурнитуры и объема партии. Условия сотрудничества включают гибкую систему скидок для постоянных заказчиков и информационно-техническую поддержку на всех стадиях взаимодействия.
                    </p>
                </section>
                <Feedback/>
            </div>
        </div>
    </div>
</template>
<script setup>

</script>

<style>

.zastr__container {
  padding: 160px 0 0;
  @media screen and (max-width: 1024px) {
    padding-top: 50px;
    padding-left: 10px;
    padding-right: 10px;
  }
}

.zastr__img {
  display: block;

  margin: 0 auto;
  @media screen and (max-width: 880px) {
    min-width: 100%;
  }
  @media screen and (max-width: 425px) {
    width: 100vw;
  }
}

.zastr-text__block {
  max-width: 980px;
  margin: 0 auto 100px;
  @media screen and (max-width: 880px) {
    max-width: 350px;
  }
}

.zastr__title {
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

.zastr__subtitle {
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
