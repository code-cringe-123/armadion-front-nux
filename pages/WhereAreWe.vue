<template>
  <div class="location__container">
    <div class="location__wrapper">
      <div class="location-title_div">
        <h2 class="location__title">Наши магазины</h2>
        <a href="" class="location__link">
          Смотреть на карте
          <span class="map__i"
            ><img src="../public/svg/map_icon.svg" alt=""
          /></span>
        </a>
      </div>

      <div class="location-info">
        <div class="location-info_div__l">
          <div class="location-info__block">
            <img src="../public/svg/temp.png" alt="" />

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
                    v-if="key !== 'title' && key !== 'address'"
                  >
                    {{ key }}:
                  </p>
                  <p
                    class="contact-i_r"
                    v-if="key !== 'title' && key !== 'address'"
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
  },
  2: {
    title: "Двери Форт",
    address: "г. Самара, Заводское шоссе 17, 2-й этаж, офис 5",
    "Телефон администратора:": "+7 (846) 207-23-20",
    "Рабочие часы:": "ПН-ВС с 9:00-18:00",
  },
  3: {
    title: "Домовой",
    address: "Рязанская область, г. Ряжск, пл. Советская 7А",
    "Телефон администратора:": "+7 (915) 613-30-00",
    "Рабочие часы:": "ПН-ПТ с 9:00-18:00, СБ-ВС с 9:00-15:00",
  },
  4: {
    title: "Домовой",
    address: "Рязанская область, г. Рыбное, Малое шоссе, д.4, ТЦ «МАКС»",
    "Телефон администратора:": "+7 (903) 839-99-00",
    "Рабочие часы:": "ПН-ПТ с 9:00-19:00, СБ-ВС с 9:00-16:00",
  },
  5: {
    title: "Магазин Двери",
    address:
      "Республика Татарстан, пгт Рыбная-Слобода, ул. Заки-Шаймарданова, 1А",
    "Телефон администратора:": "+7 (927) 677-02-55",
    "Рабочие часы:": "ПН-ПТ с 8:00-17:00, СБ-ВС с 8:00-14:00",
  },
  6: {
    title: "Мир дверей",
    address:
      "Самарская обл., г. Тольятти, ул. Коммунальная, д.32. ТЦ «Арбуз», 1 этаж",
    "Телефон администратора:": "+7 (848) 257-03-10",
    "Рабочие часы:": "ПН-ПТ с 9:00-19:00, СБ с 9:00-18:00, ВС с 10:00-17:00",
  },
  7: {
    title: "Мир дверей",
    address: "г. Котлас, Болтинское шоссе, 8. «Строй-Сити»",
    "Телефон администратора:": "+7 (911) 598-56-59",
    "Рабочие часы:": "ПН-ПТ с 9:00-18:00, СБ-ВС с 10:00-18:00",
  },
  8: {
    title: "Мир дверей",
    address: "г. Котлас, склад Новая ветка, д.3, корпус 17",
    "Телефон администратора:": "+7 (911) 878-53-08",
    "Рабочие часы:": "ПН-ПТ с 10:00-16:00, Сб, Вс - выходные",
  },
  9: {
    title: "Окошко",
    address: "Рязанская область, г. Касимов, ул. Советская, д. 99",
    "Телефон администратора:": "+7 (952) 122-00-17",
    "Рабочие часы:": "ПН-ПТ с 9:00-18:00, СБ-ВС с 9:00-15:00",
  },
  10: {
    title: "Салон дверей «АВАНДОР»",
    address: 'г. Казань, пр. Х. Ямашева, д. 93, ТК "САВИНОВО", 2 этаж',
    "Телефон администратора:": "+7 (917) 233-98-88",
    "Рабочие часы:": "ПН-ВС с 10:00-21:00",
  },
  11: {
    title: "Салон дверей «Армада»",
    address: "г. Балашиха, ул. Советская 35, офис 402",
    "Телефон администратора:": "+7 (495) 135-13-74",
  },
  12: {
    title: "Салон дверей «Армада»",
    address:
      "г. Москва, Северо-Восточный административно-территориальный округ, ул. Шереметьевская, д.85, стр.1, этаж 5, пом.1, комн. № 2а",
    "Телефон администратора:": "+7 (495) 928-07-38",
  },
  13: {
    title: "Салон дверей «Армада»",
    address:
      "г. Москва, Волгоградский проспект, 32 к. 25, ТЦ «Метр Квадратный», 1 этаж, павильон 172",
    "Телефон администратора:": "+7 (495) 005-55-95",
    "Рабочие часы:": "ПН-ВС с 9:00-20:00",
  },
  14: {
    title: "Салон дверей «Армада»",
    address:
      "г. Реутов, Улица имени Академика В.Н. Челомея, 12, ТЦ «Аладин», 1 этаж",
    "Телефон администратора:": "+7 (495) 101-23-07",
    "Рабочие часы:": "ПН-ВС с 9:00-20:00",
  },
  15: {
    title: "Салон дверей «Армада»",
    address:
      "г. Москва, Симферопольский бульвар, 11, ТЦ «Москворецкий рынок», 1 этаж, А 2060",
    "Телефон администратора:": "+7 (499) 391-01-55",
    "Рабочие часы:": "ПН-ВС с 9:00-20:00",
  },
  16: {
    title: "Салон дверей «Армада»",
    address:
      "г. Реутов, Северный проезд, 1, Строительный рынок «Владимирский тракт», линия 1, П-2, 2 этаж, павильон 16",
    "Телефон администратора:": "+7 (977) 334-38-34",
    "Рабочие часы:": "ПН-ВС с 9:00-20:00",
  },
  17: {
    title: "Салон дверей «Армада»",
    address:
      "г. Раменское, Донинское шоссе, 20, Строительный рынок «Радуга», эт. 2, пав. Б-5",
    "Телефон администратора:": "+7 (962) 999-32-72",
    "Рабочие часы:": "ПН-ВС с 9:00-20:00",
  },
  18: {
    title: "Салон дверей «Армада»",
    address:
      "г. Люберцы, Инициативная улица, 8, Строительный рынок «Эстакада», ряд 2, пав. В-21",
    "Телефон администратора:": "+7 (925) 855-84-81",
    "Рабочие часы:": "ПН-ВС с 9:00-20:00",
  },
  19: {
    title: "Салон дверей «Армада»",
    address:
      "г. Красногорск, М-9 Балтия, 21-й километр, с1, Строительный двор «Петровский», магазин Б-52",
    "Телефон администратора:": "+7 (926) 224-02-27",
    "Рабочие часы:": "ПН-ВС с 9:00-20:00",
  },
  20: {
    title: "Салон дверей «Армада»",
    address: "г. Москва, Осташковское шоссе, 1б, Строй двор «Яуза», ТСК 2-23",
    "Телефон администратора:": "+7 (919) 773-32-35",
    "Рабочие часы:": "ПН-ВС с 9:00-20:00",
  },
  21: {
    title: "Салон дверей «Армада»",
    address: "г. Москва, ул. Салтыковская, д.26, стр.2",
    "Телефон администратора:": "+7 (495) 125-42-05",
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

      @media screen and (max-width: 920px) {
        /* grid-template-columns: 1fr;
        grid-template-rows: 1fr 1fr; */
        display: flex;
        flex-direction: column-reverse;
      }
      .location-info_div__l {
        padding: 10px 0 26px 15px;
        border: 1px solid rgb(209, 213, 219);
        @media screen and (max-width: 920px) {
          padding: 10px;
        }
        .location-info__block {
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
      max-height: 651px;
      overflow: auto;
      width: 100%;
      .store__list {
        .store__item {
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
