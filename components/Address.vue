<template>
  <div class="address-container">
    <div class="address-wrapper">
      <div class="address-inf-wrapper">
        <div class="contacts-text">Адресс</div>
        <div class="contacts-title">Россия, г. Йошкар-Ола, ул. Мира, д. 30</div>
      </div>
      <div class="contact-map-wrapper">
        <a
          href="https://yandex.ru/maps/41/yoshkar-ola/?utm_medium=mapframe&utm_source=maps"
          style="color: #eee; font-size: 12px; position: absolute; top: 0px"
          >Йошкар‑Ола</a
        ><a
          href="https://yandex.ru/maps/41/yoshkar-ola/house/ulitsa_mira_30/YE4YfwJgSEwFQFtsfXpyd39kZg==/?ll=47.951263%2C56.635983&source=serp_navig&utm_medium=mapframe&utm_source=maps&z=17.64"
          style="color: #eee; font-size: 12px; position: absolute; top: 14px"
          >Яндекс Карты — транспорт, навигация, поиск мест</a
        >
        <iframe
          class="contact-map"
          src="https://yandex.ru/map-widget/v1/?ll=47.951263%2C56.635983&mode=search&ol=geo&ouri=ymapsbm1%3A%2F%2Fgeo%3Fdata%3DCgo1Mjg1NzIyNzI2EmDQoNC-0YHRgdC40Y8sINCg0LXRgdC_0YPQsdC70LjQutCwINCc0LDRgNC40Lkg0K3Quywg0JnQvtGI0LrQsNGALdCe0LvQsCwg0YPQu9C40YbQsCDQnNC40YDQsCwgMzAiCg0AzT9CFaWLYkI%2C&source=serp_navig&z=17.64"
          frameborder="0"
          allowfullscreen="true"
          style="position: relative"
        ></iframe>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
// .contact-map-wrapper {
//     display: flex;
//     align-items: center;
//     justify-content: center;
// }

.contact-map {
  width: 1180px;
  height: 664px;

  @media screen and (max-width: 1240px) {
    width: 95vw;
    height: 664px;
  }

  @media screen and (max-width: 768px) {
    width: 95vw;
    height: 664px;
  }

  @media screen and (max-width: 425px) {
    width: 95vw;
    height: 664px;
  }

  // @media screen and (max-width: 370) {
  //     width: 80vw;
  //     height: 664px;
  // }
}

.address-container {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;

  @media screen and (max-width: 768px) {
    width: 100vw;
  }
}

.address-wrapper {
  // max-width: 1180px;
  @media screen and (max-width: 768px) {
    width: 100vw;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
}

.address-inf-wrapper {
  // padding-left: 20px;
  // padding-right: 20px;
  width: 100%;
}

.address-inf-wrapper .contacts-text {
  margin-bottom: 4px;

  @media screen and (max-width: 768px) {
    font-family: Sansation;
    font-size: 16px;
    font-weight: 400;
    line-height: 19px;
    letter-spacing: 0em;
    text-align: left;
    width: 100vw;
    padding-left: 10px;
    padding-right: 10px;
  }
}

.address-inf-wrapper .contacts-title {
  margin-bottom: 26px;

  @media screen and (max-width: 768px) {
    margin-bottom: 20px;
    font-family: Sansation;
    font-size: 24px;
    font-weight: 400;
    line-height: 25px;
    letter-spacing: 0em;
    text-align: left;
    // width: 354px;
    width: 100vw;
    padding-left: 10px;
    padding-right: 10px;
  }

  @media screen and (max-width: 425px) {
    margin-bottom: 20px;
    font-family: Sansation;
    font-size: 24px;
    font-weight: 400;
    line-height: 25px;
    letter-spacing: 0em;
    text-align: left;
    width: 354px;
  }
  @media screen and (max-width: 360px) {
    width: 100%;
  }
}
</style>
