<template>
  <div class="location__container">
    <div class="location__wrapper">
      <div class="location-title_div">
        <h2 class="location__title">Наши магазины</h2>
        <a href="#" class="location__link">
          Смотреть на карте
          <span class="map__i"
            ><img src="../public/svg/map_icon.svg" alt=""
          /></span>
        </a>
      </div>

      <div class="location-info">
        <div class="location-info_div__l">
          <div class="location-info__block">
            <!--  -->
            <iframe
              v-if="selectedStore"
              :src="selectedStore.link"
              width="500"
              height="400"
              frameborder="0"
            ></iframe>
            <!--  -->
            <div class="info-b">
              <h3 class="info-b__title" v-if="selectedStore">
                {{ selectedStore.title }}
              </h3>
              <p class="info-b__subtitle" v-if="selectedStore">
                {{ selectedStore.address }}
              </p>
            </div>
            <div class="contact-us-b">
              <ul class="contacts__list" v-if="selectedStore">
                <li
                  class="contact__item"
                  v-for="(value, key) in selectedStore"
                  :key="key"
                >
                  <p
                    class="contact-i_l"
                    v-if="
                      key !== 'title' && key !== 'address' && key !== 'link'
                    "
                  >
                    {{ key }}:
                  </p>
                  <p
                    class="contact-i_r"
                    v-if="
                      key !== 'title' && key !== 'address' && key !== 'link'
                    "
                  >
                    {{ value }}
                  </p>
                </li>
              </ul>
            </div>
          </div>
        </div>

        <div class="location-choose_list__r">
          <ul class="store__list">
            <li
              class="store__item"
              v-for="(value, key) in contactsWhere"
              :key="key"
              @click="showStoreInfo(value)"
              style="cursor: pointer;"
            >
              <p
                class="store_t__l"
                :class="{
                  selected:
                    selectedStore.title === value.title &&
                    selectedStore.address === value.address,
                }"
              >
                {{ value["title"] }}
              </p>
              <p class="store_st__r">{{ value["address"] }}</p>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
// const contactsWhere = {
//   "Телефон администратора:": "+7 (8362) 64-24-88",
//   "Рабочие часы:": "По будням с 9:00 до 18:00",
//   "E-mail:": "armadionzakaz@gmail.com",
// };
import { ref } from "vue";

const contactsWhere = {
  1: {
    title: "Стальные двери «Армада» в Москве",
    address: "г. Йошкар-Ола, ул. Мира, д. 30",
    "Телефон администратора:": "+7 (8362) 64-24-88",
    "Рабочие часы:": "По будням с 9:00 до 18:00",
    "E-mail:": "armadionzakaz@gmail.com",
    link: "https://yandex.ru/map-widget/v1/?um=constructor%3A2b109d5a9625129114897c28aa1d22cd1505eecbee4689d4a3258e30872ec96f&amp;source=constructor",
  },
  2: {
    title: "Двери Форт",
    address: "г. Самара, Заводское шоссе 17, 2-й этаж, офис 5",
    "Телефон администратора:": "+7 (846) 207-23-20",
    "Рабочие часы:": "ПН-ВС с 9:00-18:00",
    link: "https://yandex.ru/map-widget/v1/?um=constructor%3A260c0e063a014cb682ae3856c0f426f7857a3302438861e76e8529abffd0ec29&amp;source=constructor",
  },
  3: {
    title: "Домовой",
    address: "Рязанская область, г. Ряжск, пл. Советская 7А",
    "Телефон администратора:": "+7 (915) 613-30-00",
    "Рабочие часы:": "ПН-ПТ с 9:00-18:00, СБ-ВС с 9:00-15:00",
    link: "https://yandex.ru/map-widget/v1/?um=constructor%3A895867b74cd091f963ee83ea19a11d2d5389ada1eb83feca4b64c0a868f8b3a0&amp;source=constructor",
  },
  4: {
    title: "Домовой",
    address: "Рязанская область, г. Рыбное, Малое шоссе, д.4, ТЦ «МАКС»",
    "Телефон администратора:": "+7 (903) 839-99-00",
    "Рабочие часы:": "ПН-ПТ с 9:00-19:00, СБ-ВС с 9:00-16:00",
    link: "https://yandex.ru/map-widget/v1/?um=constructor%3Aadd8044acd039f0957ed45e88f7352595af953808a5f3e5096798fc2ad679579&amp;source=constructor",
  },
  5: {
    title: "Магазин Двери",
    address:
      "Республика Татарстан, пгт Рыбная-Слобода, ул. Заки-Шаймарданова, 1А",
    "Телефон администратора:": "+7 (927) 677-02-55",
    "Рабочие часы:": "ПН-ПТ с 8:00-17:00, СБ-ВС с 8:00-14:00",
    link: "https://yandex.ru/map-widget/v1/?um=constructor%3Ab1b3089c92777ad86b03b02428b06ad6f15e2e6b1ffe388439e6981c5122991a&amp;source=constructor",
  },
  6: {
    title: "Мир дверей",
    address:
      "Самарская обл., г. Тольятти, ул. Коммунальная, д.32. ТЦ «Арбуз», 1 этаж",
    "Телефон администратора:": "+7 (848) 257-03-10",
    "Рабочие часы:": "ПН-ПТ с 9:00-19:00, СБ с 9:00-18:00, ВС с 10:00-17:00",
    link: "https://yandex.ru/map-widget/v1/?um=constructor%3Addaa07970f2d42197fa66ab9b6cf9fafc05b02f7ae60654b3b2decb3a1fc3ee3&amp;source=constructor",
  },
  7: {
    title: "Мир дверей",
    address: "г. Котлас, Болтинское шоссе, 8. «Строй-Сити»",
    "Телефон администратора:": "+7 (911) 598-56-59",
    "Рабочие часы:": "ПН-ПТ с 9:00-18:00, СБ-ВС с 10:00-18:00",
    link: "https://yandex.ru/map-widget/v1/?um=constructor%3Af81203d8167c37e8a2d39c2d0ada1ded558f351a7b65c877ab3de73e91b18d6f&amp;source=constructor",
  },
  8: {
    title: "Мир дверей",
    address: "г. Котлас, склад Новая ветка, д.3, корпус 17",
    "Телефон администратора:": "+7 (911) 878-53-08",
    "Рабочие часы:": "ПН-ПТ с 10:00-16:00, Сб, Вс - выходные",
    link: "https://yandex.ru/map-widget/v1/?um=constructor%3A95cedcd334efc7d091936d668191408909cc7aca01f1f99420c6e7433d524820&amp;source=constructor",
  },
  9: {
    title: "Окошко",
    address: "Рязанская область, г. Касимов, ул. Советская, д. 99",
    "Телефон администратора:": "+7 (952) 122-00-17",
    "Рабочие часы:": "ПН-ПТ с 9:00-18:00, СБ-ВС с 9:00-15:00",
    link: "https://yandex.ru/map-widget/v1/?um=constructor%3A4dec9729b5ba366adec3f288fd94cf2cd45fbd9186166312fff767e92db5ca07&amp;source=constructor",
  },
  10: {
    title: "Салон дверей «АВАНДОР»",
    address: 'г. Казань, пр. Х. Ямашева, д. 93, ТК "САВИНОВО", 2 этаж',
    "Телефон администратора:": "+7 (917) 233-98-88",
    "Рабочие часы:": "ПН-ВС с 10:00-21:00",
    link: "https://yandex.ru/map-widget/v1/?um=constructor%3A756f9a9ef46b78560492a0190329fb2da13d4aa5e6aaa735eac140ab83f49a48&amp;source=constructor",
  },
  11: {
    title: "Салон дверей «Армада»",
    address: "г. Балашиха, ул. Советская 35, офис 402",
    "Телефон администратора:": "+7 (495) 135-13-74",
    link: "https://yandex.ru/map-widget/v1/?um=constructor%3A14d1cc417e4427eeab6eefcfd12cfdb59a667183f5e78d21959057ad28600d16&amp;source=constructor",
  },
  12: {
    title: "Салон дверей «Армада»",
    address:
      "г. Москва, Северо-Восточный административно-территориальный округ, ул. Шереметьевская, д.85, стр.1, этаж 5, пом.1, комн. № 2а",
    "Телефон администратора:": "+7 (495) 928-07-38",
    link: "https://yandex.ru/map-widget/v1/?um=constructor%3A4e59224313f83eb7887ed966a72dee43e8fc8f37b69775cbb9d485e12963a3be&amp;source=constructor",
  },
  13: {
    title: "Салон дверей «Армада»",
    address:
      "г. Москва, Волгоградский проспект, 32 к. 25, ТЦ «Метр Квадратный», 1 этаж, павильон 172",
    "Телефон администратора:": "+7 (495) 005-55-95",
    "Рабочие часы:": "ПН-ВС с 9:00-20:00",
    link: "https://yandex.ru/map-widget/v1/?um=constructor%3Aca0e19e2cf0d2023d5028ca51ae50946910391ae2ff361fa028a1bd302a0d7b4&amp;source=constructor",
  },
  14: {
    title: "Салон дверей «Армада»",
    address:
      "г. Реутов, Улица имени Академика В.Н. Челомея, 12, ТЦ «Аладин», 1 этаж",
    "Телефон администратора:": "+7 (495) 101-23-07",
    "Рабочие часы:": "ПН-ВС с 9:00-20:00",
    link: "https://yandex.ru/map-widget/v1/?um=constructor%3A6a942e05c7d2a1391edd2e42596d9c8b8357188ba1438cd5ededb05d4f69becc&amp;source=constructor",
  },
  15: {
    title: "Салон дверей «Армада»",
    address:
      "г. Москва, Симферопольский бульвар, 11, ТЦ «Москворецкий рынок», 1 этаж, А 2060",
    "Телефон администратора:": "+7 (499) 391-01-55",
    "Рабочие часы:": "ПН-ВС с 9:00-20:00",
    link: "https://yandex.ru/map-widget/v1/?um=constructor%3A4cbc2a5c665f7efcf202cd8b0bdc42598bc04598e61fcb1edd75748637718e77&amp;source=constructor",
  },
  16: {
    title: "Салон дверей «Армада»",
    address:
      "г. Реутов, Северный проезд, 1, Строительный рынок «Владимирский тракт», линия 1, П-2, 2 этаж, павильон 16",
    "Телефон администратора:": "+7 (977) 334-38-34",
    "Рабочие часы:": "ПН-ВС с 9:00-20:00",
    link: "https://yandex.ru/map-widget/v1/?um=constructor%3A72dc26b7ed8681e90b1719fcc2b9beb5d9c0db3aab53378cdd5a2cb7d50a01d1&amp;source=constructor",
  },
  17: {
    title: "Салон дверей «Армада»",
    address:
      "г. Раменское, Донинское шоссе, 20, Строительный рынок «Радуга», эт. 2, пав. Б-5",
    "Телефон администратора:": "+7 (962) 999-32-72",
    "Рабочие часы:": "ПН-ВС с 9:00-20:00",
    link: "https://yandex.ru/map-widget/v1/?um=constructor%3Abf5979e1cc38a2849e00fa7f79c4e84a414974f8626f14e1df547abddd627fa9&amp;source=constructor",
  },
  18: {
    title: "Салон дверей «Армада»",
    address:
      "г. Люберцы, Инициативная улица, 8, Строительный рынок «Эстакада», ряд 2, пав. В-21",
    "Телефон администратора:": "+7 (925) 855-84-81",
    "Рабочие часы:": "ПН-ВС с 9:00-20:00",
    link: "https://yandex.ru/map-widget/v1/?um=constructor%3Ace96221bcd38d19d689a1ba3b3625d7da639b82ea02fbf88404e219415f104a2&amp;source=constructor",
  },
  19: {
    title: "Салон дверей «Армада»",
    address:
      "г. Красногорск, М-9 Балтия, 21-й километр, с1, Строительный двор «Петровский», магазин Б-52",
    "Телефон администратора:": "+7 (926) 224-02-27",
    "Рабочие часы:": "ПН-ВС с 9:00-20:00",
    link: "https://yandex.ru/map-widget/v1/?um=constructor%3Af96dbbb19886fb27cadcb80f95abc67f5c53f50f559fb705fb0b0153dd377e87&amp;source=constructor",
  },
  20: {
    title: "Салон дверей «Армада»",
    address: "г. Москва, Осташковское шоссе, 1б, Строй двор «Яуза», ТСК 2-23",
    "Телефон администратора:": "+7 (919) 773-32-35",
    "Рабочие часы:": "ПН-ВС с 9:00-20:00",
    link: "https://yandex.ru/map-widget/v1/?um=constructor%3A2a2e99c3d83d45d0dc9c8ef2eb872fff1b947bd5fbdc4d815d58dfb687491907&amp;source=constructor",
  },
  21: {
    title: "Салон дверей «Армада»",
    address: "г. Москва, ул. Салтыковская, д.26, стр.2",
    "Телефон администратора:": "+7 (495) 125-42-05",
    link: "https://yandex.ru/map-widget/v1/?um=constructor%3A2b8aefa26e4c8a8ea01c240f4dadcbb6b126f0fc5e6937e11a475993d18f2e4a&amp;source=constructor",
  },
};

const selectedStore = ref(null);

const showStoreInfo = (store) => {
  selectedStore.value = store;
};

// Установка первого магазина в качестве изначально выбранного
selectedStore.value = Object.values(contactsWhere)[0];
</script>
<style>
.selected {
  color: rgb(56, 189, 248);
}
.location__container {
  padding: 160px 10px 0;
  max-width: 1200px;
  margin: 0 auto;
  @media screen and (max-width: 920px) {
    padding: 160px 10px 0;
  }
  .location__wrapper {
    .location-title_div {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 52px;
      @media screen and (max-width: 920px) {
        flex-direction: column;
        align-items: flex-start;
        margin-bottom: 28px;
      }
      .location__title {
        color: #374151;

        font-family: Sansation;
        font-size: 64px;
        font-weight: 400;
        line-height: 105%;
        @media screen and (max-width: 920px) {
          font-size: 32px;
        }
      }

      .location__link {
        display: flex;
        text-decoration: none;
        align-items: center;
        border-radius: 5px;
        padding: 7px 10px;
        background: rgb(229, 231, 235);
        color: rgb(156, 163, 175);
        font-size: 14px;
        font-weight: 700;
        line-height: 140%;
        .map__i {
          padding-left: 13px;
        }
        @media screen and (max-width: 920px) {
          margin-top: 10px;
        }
      }
    }

    .location-info {
      display: grid;
      grid-template-columns: 1fr 1fr;
      max-height: 660px;
      @media screen and (max-width: 920px) {
        /* grid-template-columns: 1fr;
        grid-template-rows: 1fr 1fr; */
        max-height: 100%;
        display: flex;
        flex-direction: column-reverse;
      }
      .location-info_div__l {
        padding: 10px 10px 10px 15px;
        border: 1px solid rgb(209, 213, 219);
        @media screen and (max-width: 920px) {
          padding: 10px;
        }
        .location-info__block {
          iframe {
            width: 100%;
            margin-bottom: 10px;
          }
          margin-top: 16px;
          .info-b {
            .info-b__title {
              color: rgb(17, 24, 39);
              font-family: Sansation;
              font-size: 24px;
              font-weight: 400;
              line-height: 120%;
            }
            .info-b__subtitle {
              color: rgb(156, 163, 175);
              font-family: Sansation;
              font-size: 16px;
              font-weight: 400;
              line-height: 120%;
              padding: 8px 0 14px;
            }
          }

          .contact__item {
            display: flex;
            margin-top: 16px;
            @media screen and (max-width: 480px) {
              flex-direction: column;
            }
            .contact-i_l {
              min-width: 220px;
              color: rgb(156, 163, 175);
              font-family: Sansation;
              font-size: 16px;
              font-weight: 400;
              line-height: 120%;
            }
            .contact-i_r {
              padding-left: 13px;
              color: rgb(0, 0, 0);
              font-family: Sansation;
              font-size: 16px;
              font-weight: 400;
              line-height: 120%;
              @media screen and (max-width: 480px) {
                padding: 0;
                padding-top: 5px;
              }
            }
          }
        }
      }
    }
    .location-choose_list__r {
      max-height: 660px;
      border: 1px solid rgb(209, 213, 219);
      overflow: auto;
      width: 100%;
      .store__list {
        .store__item {
          cursor: pointer;
          display: flex;
          flex-direction: column;
          gap: 5px;
          width: 100%;
          justify-content: space-between;
          padding: 26px 26px;
          border: 1px solid rgb(209, 213, 219);
          @media screen and (max-width: 480px) {
            flex-direction: column;
          }
          &:hover {
            .store_t__l {
              color: rgb(56, 189, 248);
              transition: color 0.2s;
            }
          }
          .store_t__l {
            padding-right: 10px;
          }
          .store_st__r {
            color: rgb(156, 163, 175);
            font-family: Sansation;
            font-size: 14px;
            font-weight: 400;
            line-height: 120%;
          }
        }
      }
    }
  }
}
</style>
