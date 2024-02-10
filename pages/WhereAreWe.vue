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
          <img src="../public/svg/temp.png" alt="" />

          <div class="location-info__block">
            <div class="info-b">
              <h3 class="info-b__title">Стальные двери «Армада» в Москве</h3>
              <p class="info-b__subtitle">г. Йошкар-Ола, ул. Мира, д. 30</p>
            </div>
            <div class="contact-us-b">
              <ul class="contacts__list">
                <li class="contact__item" v-for="(value, key) in contactsWhere">
                  <p class="contact-i_l">{{ key }}</p>
                  <p class="contact-i_r">{{ value }}</p>
                </li>
              </ul>
            </div>
          </div>
        </div>

        <div class="location-choose_list__r">
          <ul class="store__list">
            <li class="store__item" v-for="_ in 6">
              <p class="store_t__l">Стальные двери «Армада» в Москве</p>
              <p class="store_st__r">г.Москва</p>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const contactsWhere = {
  "Телефон администратора:": "+7 (8362) 64-24-88",
  "Рабочие часы:": "По будням с 9:00 до 18:00",
  "E-mail:": "armadionzakaz@gmail.com",
};
console.log(contactsWhere);
</script>
<style>
.location__container {
  padding: 160px 0 0;
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
      }
      .location__title {
        color: #374151;

        font-family: Sansation;
        font-size: 64px;
        font-weight: 400;
        line-height: 105%;
      }

      .location__link {
        display: flex;
        text-decoration: none;
        align-items: center;
        border-radius: 5px;
        padding: 7px 10px;
        background: rgb(229, 231, 235);

        color: rgb(156, 163, 175);
        font-family: Sansation;
        font-size: 14px;
        font-weight: 700;
        line-height: 140%;
        .map__i {
          padding-left: 13px;
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
        /* @media screen and (max-width: 920px) {
          order: 1;
        } */
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
            }
          }
        }
      }
    }
    .location-choose_list__r {
      width: 100%;
      .store__list {
        .store__item {
          display: flex;
          width: 100%;
          padding: 26px 16px;
          border: 1px solid rgb(209, 213, 219);

          &:hover {
            .store_t__l {
              color: rgb(56, 189, 248);
              transition: color 0.2s;
            }
          }
          .store_t__l {
            padding-right: 10px;
          }
        }
      }
    }
  }
}
</style>
