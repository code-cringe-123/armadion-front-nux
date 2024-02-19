<template>
  <section class="dilers-info">
    <div class="dilers-info__container">
      <h1 class="dilers-info__title">Информация для диллеров</h1>
      <h5>Доходы наших диллеров</h5>
      <div class="dilers-finance">
        <DilersFinance
          v-for="(item, index) in financeData"
          :key="index"
          :item="item"
        />
      </div>
      <div class="dilers-delivery">
        <DeliveryBlock />
      </div>
      <div class="dilers-info__additional">
        <h5>Что вам еще важно знать.</h5>
        <ol class="additional-info">
          <li>
            Оптовые цены начинаются от <strong>5 дверей</strong>. Чтобы узнать
            оптовые цены, заполните<NuxtLink to="#dilers-form">
              форму обратной связи</NuxtLink
            >
          </li>
          <li>
            Образцы дверей мы предоставляем со скидкой<strong>
              25% от оптовой цены.</strong
            >
          </li>
          <li>
            Мы размещаем информацию о вашей точки продаж на нашем сайте, чтобы у
            вас был дополнительный поток клиентов
          </li>
          <li>
            Мы предоставим вам все необходимые образцы(примеры цветов, печатные
            каталоги с продукцией)
          </li>
        </ol>
      </div>
      <div class="thanks-section">
        <h5>Письма благодарности от наших дилеров</h5>
        <div class="thanks-section__content">
          <img
            src="/thanksLatter/letter1.png"
            alt="Благодарственное письмо №1"
          />
          <img
            src="/thanksLatter/letter2.png"
            alt="Благодарственное письмо №1"
          />
          <img
            src="/thanksLatter/letter3.png"
            alt="Благодарственное письмо №1"
          />
        </div>
      </div>
    </div>
  </section>
  <Form id="dilers-form" />
</template>
<script>
import DilersFinance from "~/components/DilersFinance.vue";

export default {
  name: "App",
  components: {
    DilersFinance,
  },
  data() {
    return {
      financeData: [
        {
          price: "1 миллион ₽",
          description: "Магазин продает 100 дверей в месяц",
          city: "город Уссурийск",
        },
        {
          price: "100 тыс ₽",
          description: "Магазин продает 10 дверей в месяц",
          city: "город Кострома",
        },
        {
          price: "500 тыс ₽",
          description: "Магазин продает 50 дверей в месяц",
          city: "город Ярославль",
        },
      ],
    };
  },
};
</script>

<style>
.dilers-info {
  padding-top: 160px;
}
.dilers-info__container {
  max-width: 1180px;
  margin: 0 auto;
}
.dilers-info__title {
  font-size: 3.5rem;
  line-height: 105%;
  font-weight: 400;
  color: #111827;
  margin-bottom: 80px;
}
.dilers-info h5 {
  font-size: 1.5rem;
  line-height: 120%;
  color: #111827;
  font-weight: 400;
  margin-bottom: 20px;
}
.dilers-finance {
  display: flex;
  gap: 20px;
  flex-wrap: wrap;
  width: 100%;
  align-items: start;
}
.dilers-delivery,
.dilers-finance,
.dilers-info__additional {
  margin-bottom: 130px;
}
.additional-info {
  padding-left: 20px;
  font-weight: 400;
  font-size: 1.5rem;
  list-style: decimal;
  line-height: 120%;
  color: #111827;
}
.additional-info a {
  text-decoration: none;
  color: #38bdf8;
}
.thanks-section__content {
  width: 100%;
  display: flex;
  align-items: flex-start;
  overflow: scroll;
  overflow-y: hidden;
  gap: 20px;
  margin: 0 auto;
}
.thanks-section img {
  height: 800px;
  object-fit: contain;
}
@media (max-width: 1300px) {
  .dilers-info__container {
    max-width: 899px;
  }
  .dilers-delivery,
  .dilers-finance,
  .dilers-info__additional {
    margin-bottom: 105px;
  }
  .thanks-section img {
    height: 600px;
  }
}
@media (max-width: 990px) {
  .dilers-info__container {
    max-width: 568px;
  }
  .dilers-info__title {
    font-size: 2.2rem;
    font-weight: 600;
    margin-bottom: 40px;
  }
  .dilers-info h5 {
    font-size: 1.3rem;
  }
  .additional-info {
    font-size: 1.2rem;
  }
  .thanks-section img {
    height: 800px;
  }
}
@media (max-width: 768px) {
  .dilers-info {
    padding-top: 115px;
  }
  .dilers-info__container {
    max-width: 478px;
  }
  .dilers-delivery,
  .dilers-finance,
  .dilers-info__additional {
    margin-bottom: 85px;
  }
  .additional-info {
    font-size: 1rem;
  }
  .thanks-section img {
    height: 660px;
  }
}
@media (max-width: 568px) {
  .dilers-info__container {
    max-width: 325px;
  }
  .dilers-info {
    padding-top: 95px;
  }
  .dilers-info__title {
    font-size: 2rem;
  }
  .dilers-delivery,
  .dilers-finance,
  .dilers-info__additional {
    margin-bottom: 65px;
  }
  .additional-info {
    font-size: 0.8rem;
    padding-left: 15px;
  }
  .thanks-section img {
    height: 500px;
  }
}
</style>
