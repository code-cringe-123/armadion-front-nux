<template>
  <div class="footer-wrapper">
    <div class="footer-wrapper__container">
      <div class="footer-img-wrapper">
        <img
          class="footer-logo"
          src="../public/svg/armadion-logo.svg"
          alt="armadion"
        />
      </div>
      <div class="footer-col-container">
        <div class="footer-col">
          <div class="footer-title">ОПТОВИКАМ</div>
          <div class="footer-catalog">
            <ul class="footer-catalog-list">
              <li
                class="footer-catalog-list__list-item color-hover footer-otstup-str"
              >
                <NuxtLink to="#">Дилерам</NuxtLink>
              </li>
              <li
                class="footer-catalog-list__list-item color-hover footer-otstup-str"
              >
                <NuxtLink to="#">Застройщикам</NuxtLink>
              </li>
              <li class="footer-catalog-list__list-item color-hover">
                <NuxtLink to="#">Где купить</NuxtLink>
              </li>
              <li class="footer-catalog-list__list-item color-hover">
                <NuxtLink to="#">Двери оптом</NuxtLink>
              </li>
            </ul>
          </div>
        </div>
        <div class="footer-col">
          <div class="footer-title">ИНФОРМАЦИЯ</div>
          <div class="footer-catalog">
            <ul class="footer-catalog-list">
              <li
                class="footer-catalog-list__list-item color-hover footer-otstup-str"
              >
                <NuxtLink to="#">Завод Армада</NuxtLink>
              </li>
              <li
                class="footer-catalog-list__list-item color-hover footer-otstup-str"
              >
                <NuxtLink to="#">Доставка и оплата</NuxtLink>
              </li>
              <li class="footer-catalog-list__list-item color-hover">
                <NuxtLink to="#">Наша гарантия</NuxtLink>
              </li>
              <li class="footer-catalog-list__list-item color-hover">
                <NuxtLink to="#">Политика <br />конфиденциальности</NuxtLink>
              </li>
            </ul>
          </div>
        </div>
        <div class="footer-col">
          <div class="footer-title">НАША ПРОДУКЦИЯ</div>
          <div class="footer-catalog">
            <ul class="footer-catalog-list">
              <li
                class="footer-catalog-list__list-item color-hover footer-otstup-str"
              >
                <NuxtLink to="#">Входные двери</NuxtLink>
              </li>
              <li
                class="footer-catalog-list__list-item color-hover footer-otstup-str"
              >
                <NuxtLink to="#">Противопожарные двери</NuxtLink>
              </li>
              <li class="footer-catalog-list__list-item color-hover">
                <NuxtLink to="#">Фурнитура</NuxtLink>
              </li>
              <li class="footer-catalog-list__list-item color-hover">
                <NuxtLink to="#">Внешняя отделка</NuxtLink>
              </li>
              <li class="footer-catalog-list__list-item color-hover">
                <NuxtLink to="#">Отделка панелью</NuxtLink>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
    <div class="footer-bottom">
      <!-- <div class="footer-bottom-title">© 2010—2023. Все права защищены.</div>
              <div class="footer-bottom-text">Интернет-сайт ARMADION.shop носит исключительно информационный характер и ни при каких условиях не является публичной офертой, определяемой положениями Статьи 437 Гражданского кодекса Российской Федерации. Цены в салонах могут отличатся от цен на сайте. Чтобы получить актуальную и подробную информацию о стоимости продукции, условиях поставки, монтажа, акциях и иных условиях, пожалуйста, обращайтесь к менеджерам по телефону, указанному на сайте</div>
              <div class="footer-bottom-conf">Политика конфиденциальности</div> -->
    </div>
  </div>
</template>

<style lang="scss">
.footer-otstup-str {
  line-height: 16px;
}

.footer-wrapper {
  background-color: #1f2937;
  width: 100vw;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding-top: 30px;
  margin-top: 100px;

  @media screen and (max-width: 768px) {
    padding: 0;
    margin-top: 115px;
  }
}

.footer-col {
  padding: 0 15px;

  @media screen and (max-width: 768px) {
    margin-bottom: 50px;

    &:last-child {
      margin-bottom: 0;
    }
  }
  @media screen and (max-width: 375px) {
    padding: 0;
  }
}

.footer-wrapper__container {
  display: flex;
  flex-direction: row;
  align-items: flex-start;
  justify-content: space-between;
  margin-bottom: 30px;
  max-width: 1180px;
  width: 100vw;

  @media screen and (max-width: 768px) {
    width: 100vw;
    height: 711px;
    padding: 20px;
    margin-bottom: 55px;
    display: flex;
    flex-direction: column;
    align-items: stretch;
    justify-content: start;
  }
}

.footer-img-wrapper {
  min-width: 111px;
  min-height: 142px;

  @media screen and (max-width: 768px) {
    margin-bottom: 60px;
  }
}

.footer-logo {
  width: 111px;
  height: 142px;
}

.footer-col-container {
  display: grid;
  justify-items: start;
  grid-template-columns: repeat(3, 1fr);

  @media screen and (max-width: 768px) {
    grid-template-columns: repeat(2, 1fr);
    // margin-bottom: 80px;
  }
}

.footer-bottom {
  background-color: #111827;
  width: 100%;
  padding: 18px 0;
}

.footer-bottom-title {
  font-size: 14px;
  color: white;
  margin-bottom: 5px;
}

.footer-bottom-text {
  font-size: 10px;
  color: white;
  margin-bottom: 10px;
}

.footer-bottom-conf {
  color: white;
  text-decoration: underline;
  cursor: pointer;
  width: 300px;
}

.footer-bottom-conf:hover {
  color: #0693d4;
  transition: 0.3s;
}

.color-hover a:hover {
  color: #0693d4;
  transition: 0.3s;
}

.footer-catalog-list__list-item a {
  text-decoration: none;
  color: #9ca3af;
  font-size: 14px;
  font-weight: 400;
  transition: 0.3s;
}

.footer-title {
  color: #f3f4f6;
  margin-bottom: 25px;
  font-size: 14px;
  font-weight: 400;
}

.footer-catalog-list__list-item {
  margin-bottom: 14px;
}
</style>
