<template>
  <div class="location__container">
    <div class="location__wrapper">
      <div class="location-title_div">
        <h2 class="location__title">Наши магазины</h2>
        <a :href="selectedStore.yalink" target="_blank" class="location__link">
          Смотреть на карте
          <span class="map__i">
            <svg
              style="height: 1.2rem"
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 384 512"
            >
              <path
                fill="#9ca3af"
                d="M215.7 499.2C267 435 384 279.4 384 192C384 86 298 0 192 0S0 86 0 192c0 87.4 117 243 168.3 307.2c12.3 15.3 35.1 15.3 47.4 0zM192 128a64 64 0 1 1 0 128 64 64 0 1 1 0-128z"
              />
            </svg>
          </span>
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
                      key !== 'title' &&
                      key !== 'address' &&
                      key !== 'link' &&
                      key !== 'yalink'
                    "
                  >
                    {{ key }}:
                  </p>
                  <p
                    class="contact-i_r"
                    v-if="
                      key !== 'title' &&
                      key !== 'address' &&
                      key !== 'link' &&
                      key !== 'yalink'
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
              style="cursor: pointer"
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
    yalink:
      "https://yandex.ru/maps/41/yoshkar-ola/house/ulitsa_mira_30/YE4YfwNkT0YFQFtsfXpydXRqZg==/?ll=47.944632%2C56.634892&z=16.64",
  },
  2: {
    title: "Двери Форт",
    address: "г. Самара, Заводское шоссе 17, 2-й этаж, офис 5",
    "Телефон администратора:": "+7 (846) 207-23-20",
    "Рабочие часы:": "ПН-ВС с 9:00-18:00",
    link: "https://yandex.ru/map-widget/v1/?um=constructor%3A260c0e063a014cb682ae3856c0f426f7857a3302438861e76e8529abffd0ec29&amp;source=constructor",
    yalink:
      "https://yandex.ru/maps/org/fort/1221606065/?ll=50.268151%2C53.202270&z=16.64",
  },
  3: {
    title: "Домовой",
    address: "Рязанская область, г. Ряжск, пл. Советская 7А",
    "Телефон администратора:": "+7 (915) 613-30-00",
    "Рабочие часы:": "ПН-ПТ с 9:00-18:00, СБ-ВС с 9:00-15:00",
    link: "https://yandex.ru/map-widget/v1/?um=constructor%3A895867b74cd091f963ee83ea19a11d2d5389ada1eb83feca4b64c0a868f8b3a0&amp;source=constructor",
    yalink:
      "https://yandex.ru/maps/10775/ryazgsk/house/sovetskaya_ploshchad_7a/YEkYdgFhTEUFQFtpfXtxeXtgZA==/?ll=40.061502%2C53.708730&z=16.64",
  },
  4: {
    title: "Домовой",
    address: "Рязанская область, г. Рыбное, Малое шоссе, д.4, ТЦ «МАКС»",
    "Телефон администратора:": "+7 (903) 839-99-00",
    "Рабочие часы:": "ПН-ПТ с 9:00-19:00, СБ-ВС с 9:00-16:00",
    link: "https://yandex.ru/map-widget/v1/?um=constructor%3Aadd8044acd039f0957ed45e88f7352595af953808a5f3e5096798fc2ad679579&amp;source=constructor",
    yalink:
      "https://yandex.ru/maps/org/domovoy/221284262860/?from=mapframe&ll=39.483311%2C54.732351&source=mapframe&um=constructor%3A895867b74cd091f963ee83ea19a11d2d5389ada1eb83feca4b64c0a868f8b3a0&utm_source=mapframe&z=16.64",
  },
  5: {
    title: "Магазин Двери",
    address:
      "Республика Татарстан, пгт Рыбная-Слобода, ул. Заки-Шаймарданова, 1А",
    "Телефон администратора:": "+7 (927) 677-02-55",
    "Рабочие часы:": "ПН-ПТ с 8:00-17:00, СБ-ВС с 8:00-14:00",
    link: "https://yandex.ru/map-widget/v1/?um=constructor%3Ab1b3089c92777ad86b03b02428b06ad6f15e2e6b1ffe388439e6981c5122991a&amp;source=constructor",
    yalink:
      "https://yandex.ru/maps/11119/republic-of-tatarstan/house/ulitsa_zaki_shaymardanova_1/YUkYcARkSEcCQFtvfXpycn1mYQ==/?ll=50.634125%2C55.633155&z=16.64",
  },
  6: {
    title: "Мир дверей",
    address:
      "Самарская обл., г. Тольятти, ул. Коммунальная, д.32. ТЦ «Арбуз», 1 этаж",
    "Телефон администратора:": "+7 (848) 257-03-10",
    "Рабочие часы:": "ПН-ПТ с 9:00-19:00, СБ с 9:00-18:00, ВС с 10:00-17:00",
    link: "https://yandex.ru/map-widget/v1/?um=constructor%3Addaa07970f2d42197fa66ab9b6cf9fafc05b02f7ae60654b3b2decb3a1fc3ee3&amp;source=constructor",
    yalink:
      "https://yandex.ru/maps/org/mir_dverey/1721208087/?from=mapframe&indoorLevel=1&ll=49.307879%2C53.561043&source=mapframe&um=constructor%3A895867b74cd091f963ee83ea19a11d2d5389ada1eb83feca4b64c0a868f8b3a0&utm_source=mapframe&z=16.64",
  },
  7: {
    title: "Окошко",
    address: "Рязанская область, г. Касимов, ул. Советская, д. 99",
    "Телефон администратора:": "+7 (952) 122-00-17",
    "Рабочие часы:": "ПН-ПТ с 9:00-18:00, СБ-ВС с 9:00-15:00",
    link: "https://yandex.ru/map-widget/v1/?um=constructor%3A4dec9729b5ba366adec3f288fd94cf2cd45fbd9186166312fff767e92db5ca07&amp;source=constructor",
    yalink:
      "https://yandex.ru/maps/org/okoshko/169575986061/?ll=41.405813%2C54.945376&z=16.64",
  },
  8: {
    title: "Салон дверей «АВАНДОР»",
    address: 'г. Казань, пр. Х. Ямашева, д. 93, ТК "САВИНОВО", 2 этаж',
    "Телефон администратора:": "+7 (917) 233-98-88",
    "Рабочие часы:": "ПН-ВС с 10:00-21:00",
    link: "https://yandex.ru/map-widget/v1/?um=constructor%3A756f9a9ef46b78560492a0190329fb2da13d4aa5e6aaa735eac140ab83f49a48&amp;source=constructor",
    yalink:
      "https://yandex.ru/maps/org/avandoor/78401944501/?from=mapframe&indoorLevel=2&ll=49.148833%2C55.826043&source=mapframe&um=constructor%3A895867b74cd091f963ee83ea19a11d2d5389ada1eb83feca4b64c0a868f8b3a0&utm_source=mapframe&z=16.64",
  },
  9: {
    title: "Салон дверей «Армада»",
    address: "г. Балашиха, ул. Советская 35, офис 402",
    "Телефон администратора:": "+7 (495) 135-13-74",
    link: "https://yandex.ru/map-widget/v1/?um=constructor%3A14d1cc417e4427eeab6eefcfd12cfdb59a667183f5e78d21959057ad28600d16&amp;source=constructor",
    yalink:
      "https://yandex.ru/maps/10716/balashiha/house/sovetskaya_ulitsa_35/Z04YfwJiTkcCQFtvfXRweH1jZA==/inside/?ll=37.952725%2C55.819100&tab=inside&z=16.64",
  },
  10: {
    title: "Салон дверей «Армада»",
    address:
      "г. Москва, Северо-Восточный административно-территориальный округ, ул. Шереметьевская, д.85, стр.1, этаж 5, пом.1, комн. № 2а",
    "Телефон администратора:": "+7 (495) 928-07-38",
    link: "https://yandex.ru/map-widget/v1/?um=constructor%3A4e59224313f83eb7887ed966a72dee43e8fc8f37b69775cbb9d485e12963a3be&amp;source=constructor",
    yalink:
      "https://yandex.ru/maps/213/moscow/house/sheremetyevskaya_ulitsa_85s1/Z04YcAZnSkwEQFtvfXRwcXplbA==/inside/?ll=37.617387%2C55.810655&tab=inside&z=18.69",
  },
  11: {
    title: "Салон дверей «Армада»",
    address:
      "г. Москва, Волгоградский проспект, 32 к. 25, ТЦ «Метр Квадратный», 1 этаж, павильон 172",
    "Телефон администратора:": "+7 (495) 005-55-95",
    "Рабочие часы:": "ПН-ВС с 9:00-20:00",
    link: "https://yandex.ru/map-widget/v1/?um=constructor%3Aca0e19e2cf0d2023d5028ca51ae50946910391ae2ff361fa028a1bd302a0d7b4&amp;source=constructor",
    yalink:
      "https://yandex.ru/maps/213/moscow/house/volgogradskiy_prospekt_32k25/Z04YcA5nTUYEQFtvfXtzcXtqbA==/?from=mapframe&indoorLevel=1&ll=37.697433%2C55.720798&source=mapframe&um=constructor%3A895867b74cd091f963ee83ea19a11d2d5389ada1eb83feca4b64c0a868f8b3a0&utm_source=mapframe&z=16.64",
  },
  12: {
    title: "Салон дверей «Армада»",
    address:
      "г. Реутов, Улица имени Академика В.Н. Челомея, 12, ТЦ «Аладин», 1 этаж",
    "Телефон администратора:": "+7 (495) 101-23-07",
    "Рабочие часы:": "ПН-ВС с 9:00-20:00",
    link: "https://yandex.ru/map-widget/v1/?um=constructor%3A6a942e05c7d2a1391edd2e42596d9c8b8357188ba1438cd5ededb05d4f69becc&amp;source=constructor",
    yalink:
      "https://yandex.ru/maps/213/moscow/?from=mapframe&ll=37.878958%2C55.748921&mode=poi&poi%5Bpoint%5D=37.878589%2C55.748970&poi%5Buri%5D=ymapsbm1%3A%2F%2Forg%3Foid%3D1085908612&source=mapframe&um=constructor%3A895867b74cd091f963ee83ea19a11d2d5389ada1eb83feca4b64c0a868f8b3a0&utm_source=mapframe&z=19.39",
  },
  13: {
    title: "Салон дверей «Армада»",
    address:
      "г. Москва, Симферопольский бульвар, 11, ТЦ «Москворецкий рынок», 1 этаж, А 2060",
    "Телефон администратора:": "+7 (499) 391-01-55",
    "Рабочие часы:": "ПН-ВС с 9:00-20:00",
    link: "https://yandex.ru/map-widget/v1/?um=constructor%3A4cbc2a5c665f7efcf202cd8b0bdc42598bc04598e61fcb1edd75748637718e77&amp;source=constructor",
    yalink:
      "https://yandex.ru/maps/org/moskvoretskiy_rynok/139296251009/?from=mapframe&ll=37.607206%2C55.657195&source=mapframe&um=constructor%3A895867b74cd091f963ee83ea19a11d2d5389ada1eb83feca4b64c0a868f8b3a0&utm_source=mapframe&z=16.64",
  },
  14: {
    title: "Салон дверей «Армада»",
    address:
      "г. Реутов, Северный проезд, 1, Строительный рынок «Владимирский тракт», линия 1, П-2, 2 этаж, павильон 16",
    "Телефон администратора:": "+7 (977) 334-38-34",
    "Рабочие часы:": "ПН-ВС с 9:00-20:00",
    link: "https://yandex.ru/map-widget/v1/?um=constructor%3A72dc26b7ed8681e90b1719fcc2b9beb5d9c0db3aab53378cdd5a2cb7d50a01d1&amp;source=constructor",
    yalink:
      "https://yandex.ru/maps/21621/reutov/?from=mapframe&indoorLevel=2&ll=37.855716%2C55.778715&mode=poi&poi%5Bpoint%5D=37.853654%2C55.778688&poi%5Buri%5D=ymapsbm1%3A%2F%2Forg%3Foid%3D86440883477&source=mapframe&um=constructor%3A895867b74cd091f963ee83ea19a11d2d5389ada1eb83feca4b64c0a868f8b3a0&utm_source=mapframe&z=16",
  },
  15: {
    title: "Салон дверей «Армада»",
    address:
      "г. Раменское, Донинское шоссе, 20, Строительный рынок «Радуга», эт. 2, пав. Б-5",
    "Телефон администратора:": "+7 (962) 999-32-72",
    "Рабочие часы:": "ПН-ВС с 9:00-20:00",
    link: "https://yandex.ru/map-widget/v1/?um=constructor%3Abf5979e1cc38a2849e00fa7f79c4e84a414974f8626f14e1df547abddd627fa9&amp;source=constructor",
    yalink:
      "https://yandex.ru/maps/10750/ramenskoe/house/doninskoye_shosse_20_b1/Z0EYdAJiQUYDQFtvfXl5eXVjbA==/?from=mapframe&indoorLevel=2&ll=38.253819%2C55.588603&source=mapframe&um=constructor%3A895867b74cd091f963ee83ea19a11d2d5389ada1eb83feca4b64c0a868f8b3a0&utm_source=mapframe&z=17.64",
  },
  16: {
    title: "Салон дверей «Армада»",
    address:
      "г. Люберцы, Инициативная улица, 8, Строительный рынок «Эстакада», ряд 2, пав. В-21",
    "Телефон администратора:": "+7 (925) 855-84-81",
    "Рабочие часы:": "ПН-ВС с 9:00-20:00",
    link: "https://yandex.ru/map-widget/v1/?um=constructor%3Ace96221bcd38d19d689a1ba3b3625d7da639b82ea02fbf88404e219415f104a2&amp;source=constructor",
    yalink:
      "https://yandex.ru/maps/10738/lubercy/house/initsiativnaya_ulitsa_8/Z04Yfg5lTUwEQFtvfXp5cnRqbQ==/inside/?from=mapframe&ll=37.896135%2C55.683869&source=mapframe&tab=inside&um=constructor%3A895867b74cd091f963ee83ea19a11d2d5389ada1eb83feca4b64c0a868f8b3a0&utm_source=mapframe&z=19.67",
  },
  17: {
    title: "Салон дверей «Армада»",
    address:
      "г. Красногорск, М-9 Балтия, 21-й километр, с1, Строительный двор «Петровский», магазин Б-52",
    "Телефон администратора:": "+7 (926) 224-02-27",
    "Рабочие часы:": "ПН-ВС с 9:00-20:00",
    link: "https://yandex.ru/map-widget/v1/?um=constructor%3Af96dbbb19886fb27cadcb80f95abc67f5c53f50f559fb705fb0b0153dd377e87&amp;source=constructor",
    yalink:
      "https://yandex.ru/maps/org/petrovskiy_stroitelny_dvor/34937466438/?from=mapframe&ll=37.233538%2C55.785315&source=mapframe&um=constructor%3A895867b74cd091f963ee83ea19a11d2d5389ada1eb83feca4b64c0a868f8b3a0&utm_source=mapframe&z=16.07",
  },
  18: {
    title: "Салон дверей «Армада»",
    address: "г. Москва, Осташковское шоссе, 1б, Строй двор «Яуза», ТСК 2-23",
    "Телефон администратора:": "+7 (919) 773-32-35",
    "Рабочие часы:": "ПН-ВС с 9:00-20:00",
    link: "https://yandex.ru/map-widget/v1/?um=constructor%3A2a2e99c3d83d45d0dc9c8ef2eb872fff1b947bd5fbdc4d815d58dfb687491907&amp;source=constructor",
    yalink:
      "https://yandex.ru/maps/10740/mytischi/house/ostashkovskoye_shosse_4s2/Z04YcABoQE0GQFtvfXVxcXpmbA==/?from=mapframe&indoorLevel=1&ll=37.678981%2C55.900658&source=mapframe&um=constructor%3A2a2e99c3d83d45d0dc9c8ef2eb872fff1b947bd5fbdc4d815d58dfb687491907&utm_source=mapframe&z=16.64",
  },
  19: {
    title: "Салон дверей «Армада»",
    address: "г. Москва, ул. Салтыковская, д.26, стр.2",
    "Телефон администратора:": "+7 (495) 125-42-05",
    link: "https://yandex.ru/map-widget/v1/?um=constructor%3A2b8aefa26e4c8a8ea01c240f4dadcbb6b126f0fc5e6937e11a475993d18f2e4a&amp;source=constructor",
    yalink:
      "https://yandex.ru/maps/213/moscow/house/saltykovskaya_ulitsa_26s2/Z04Yfg9nSU0CQFtvfXt1d3xrZQ==/?ll=37.886491%2C55.746480&z=18",
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
        transition: background 0.3s ease;
        .map__i {
          padding-left: 4px;
          svg {
            padding-top: 2px;
          }
        }
        @media screen and (max-width: 920px) {
          margin-top: 10px;
        }
      }
    }
    .location__link:hover {
      background: #0ea5e9;
      color: #fff;
      .map__i svg path {
        fill: #fff;
      }
    }
    .location-info {

      display: grid;
      grid-template-columns: 1fr 1fr;
      max-height: 670px;
      @media screen and (max-width: 920px) {
        /* grid-template-columns: 1fr;
        grid-template-rows: 1fr 1fr; */
        max-height: 100%;
        display: flex;
        flex-direction: column-reverse;
      }
      .location-info_div__l {
        max-height: 670px;
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
      min-height: 670px;
      max-height: 670px;
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
