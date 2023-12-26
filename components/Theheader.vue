<template>
  <header class="header-wrapper">
    <div class="header">
      <div class="left-side">
        <!-- мобилка -->
        <button @click="toggleSlide" class="menu-icon-btn">
          <img class="menu-icon" src="../public/svg/menu-icon.svg" alt="menu" />
        </button>
        <div :class="['slide-out-block', { show: isSlideOutVisible }]">
          <div class="nav-mobile">
            <div class="nav-mobile-header">
              <button @click="closeSlide" class="close-btn">закрыть</button>
              <div class="mobile-name-and-icon-menu">
                <div class="menu-name">меню</div>
                <div class="menu-icon-wrapper" @click="toggleCatalogLinksBlock">
                  <img
                    class="menu-icon-active"
                    src="../public/svg/menu-icon-active.svg"
                    alt="menu-active"
                  />
                </div>
                <div
                  :class="[
                    'catalog-links-block',
                    { show: isCatalogLinksBlockVisible },
                  ]"
                >
                  <div class="catalog-toggle">
                    <div class="toggle-label">Каталог</div>
                    <img
                      class="HeaderCatalog-close"
                      src="../public/svg/close.svg"
                      alt="menu-active"
                      @click="hideCatalogLinksBlock"
                    />
                  </div>
                  <ul class="HeaderCatalog-mobile-list">
                    <li>
                      <NuxtLink
                        @click="hideCatalogLinksBlock"
                        class="menu-mobile-catalog__link"
                        :to="category.link"
                        v-for="(category, i) of categories"
                        :key="i"
                        >{{ category.label }}
                        <img
                          class="HeaderCatalog-mobile-arrow"
                          src="../public/svg/headerCatalogArrow.svg"
                          alt="headerCatalogArrow"
                      /></NuxtLink>
                    </li>
                  </ul>
                </div>
              </div>
            </div>
            <NuxtLink
              @click="closeSlide"
              class="menu-mobile__link"
              :to="element.path"
              v-for="(element, i) of menu"
              :key="i"
              >{{ element.name }}</NuxtLink
            >
          </div>
        </div>
        <!-- ------ -->
        <div class="Company-name">
          <NuxtLink to="/">Армада.</NuxtLink>
        </div>
        <div class="header-catalog-wrapper">
          <div class="header-catalog-logo-wrapper">
            <img
              class="header-catalog-logo"
              src="../public/svg/Catalog-icon.svg"
              alt="catalog"
            />
          </div>
          <div
            class="header-catalog-name"
            @click="toggleSlideCatalogBlock"
            ref="block"
          >
            Каталог
          </div>
        </div>
        <div
          :class="[
            'slide-out-block-catalog-block',
            { show: isSlideOutVisibleCatalogBlock },
          ]"
          @click.stop="toggleSlideCatalogBlock"
        >
          <div ref="blockContent" class="catalog-block-content">
            <HeaderCatalog />
          </div>
        </div>
      </div>
      <div class="right-side">
        <div class="nav">
          <NuxtLink
            class="menu__link"
            :to="element.path"
            v-for="(element, i) of menu"
            :key="i"
            >{{ element.name }}</NuxtLink
          >
        </div>
        <UI-btn type="header">Связь с нами</UI-btn>
      </div>
    </div>
  </header>
</template>

<script setup>
import { ref } from "vue";
import { onClickOutside } from "@vueuse/core";
const categories = [
  {
    link: "#",
    label: "Входные двери",
  },
  {
    link: "#",
    label: "Внешняя отделка",
  },
  {
    link: "#",
    label: "Отделка панелью",
  },
  {
    link: "#",
    label: "Фурнитура",
  },
];
const menu = [
  {
    name: "Для дилеров",
    path: "/Contact",
  },
  {
    name: "Для застройщиков",
    path: "/Catalog",
  },
  {
    name: "Правила эксплуатации",
    path: "/operating_rules",
  },
  {
    name: "Двери оптом",
    path: "/doors_wholesale",
  },
];

const isSlideOutVisible = ref(false);
const isSlideOutVisibleCatalogBlock = ref(false);

const toggleSlide = () => {
  isSlideOutVisible.value = true;
};

const closeSlide = () => {
  isSlideOutVisible.value = false;
};

const toggleSlideCatalogBlock = () => {
  isSlideOutVisibleCatalogBlock.value = !isSlideOutVisibleCatalogBlock.value;
};

const block = ref(null);
const blockContent = ref(null);

onClickOutside([block, blockContent], (event) => {
  if (isSlideOutVisibleCatalogBlock.value) {
    isSlideOutVisibleCatalogBlock.value = false;
  }
});
//
const isCatalogLinksBlockVisible = ref(false);

const toggleCatalogLinksBlock = () => {
  isCatalogLinksBlockVisible.value = !isCatalogLinksBlockVisible.value;
};

const hideCatalogLinksBlock = () => {
  isCatalogLinksBlockVisible.value = false;
};
</script>

<style lang="scss">
.menu-mobile-catalog__link {
  height: 44px;
  width: 100vw;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 18px 0 10px;
  border-bottom: 1px solid #e5e7eb;

  text-decoration: none;
  font-family: Sansation;
  font-size: 16px;
  font-weight: 400;
  line-height: 22px;
  letter-spacing: 0em;
  text-align: left;
  color: #374151;
}

.HeaderCatalog-mobile-list {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.toggle-label {
  font-family: Sansation;
  font-size: 16px;
  font-weight: 700;
  line-height: 18px;
  letter-spacing: 0em;
  text-align: left;
  color: #374151;
}

.catalog-toggle {
  padding: 0 19px 0 10px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 53px;
  border-bottom: 1px solid #e5e7eb;
}

.catalog-links-block {
  position: fixed;
  background: #ffffff;
  top: 0;
  right: -100%;
  bottom: 0;
  width: 100vw;
  transition: 0.7s;
  z-index: 10000;
}

.catalog-links-block.show {
  right: 0%;
  width: 100vw;
  transition: 0.7s;
}

.header-wrapper {
  width: 100vw;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: #ffffff;
  border-bottom: 1px solid #e5e7eb;
  position: fixed;
  z-index: 10000;

  @media screen and (max-width: 425px) {
    width: 100vw;
  }
}

.header {
  position: relative;
  z-index: 10000;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
  max-width: 1180px;
  height: 90px;
  width: 100%;

  @media screen and (max-width: 1024px) {
    padding: 0 10px;
  }

  @media screen and (max-width: 768px) {
    display: flex;
    align-items: center;
    justify-content: space-between;
    height: 50px;
    padding: 0 10px 0 4px;
  }
}

.left-side {
  display: flex;
  align-items: center;
  justify-content: center;
}

.menu-icon-btn {
  @media screen and (max-width: 9999px) {
    display: none;
  }

  @media screen and (max-width: 768px) {
    display: block;
  }

  width: auto;
  height: auto;
  border: none;
  background-color: transparent;
  cursor: pointer;
}

.menu-icon {
  width: 24px;
  height: 24px;
  margin-right: 24px;
}

.slide-out-block {
  @media screen and (max-width: 9999px) {
    display: none;
  }

  @media screen and (max-width: 768px) {
    display: block;
  }

  position: fixed;
  background: #f9fafb;
  top: 0;
  left: -101%;
  bottom: 0;
  right: 0;
  width: 100vw;
  transition: 0.7s;
  z-index: 100000;
}

.slide-out-block.show {
  left: 0;
  transition: 0.7s;
}

.slide-out-block-catalog-block {
  display: none;
  position: fixed;
  background: #ffffff;
  top: -100%;
  left: 0;
  bottom: 0;
  right: 0;
  width: 100vw;
  height: 229px;
  z-index: -1;
}

.slide-out-block-catalog-block.show {
  display: block;
  top: 91px;
}

.mobile-name-and-icon-menu {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
}

.menu-name {
  font-size: 16px;
  font-weight: 700;
  color: #6b7280;
  margin-right: 14px;
}

.close-btn {
  cursor: pointer;
  width: auto;
  height: auto;
  font-size: 16px;
  font-weight: 700;
  text-align: center;
  color: #6b7280;
  border: none;
  padding: 0;
  background-color: transparent;
  transition: 0.3s;
}

.close-btn:hover {
  color: #0369a1;
  transition: 0.3s;
}

.menu-icon-wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
  width: auto;
  height: auto;
}

.menu-icon-active {
  width: 24px;
  height: 24px;
}

.nav-mobile {
  max-width: 100vw;
}

.nav-mobile-header {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
  height: 50px;
  border-bottom: 1px solid #e5e7eb;
  margin-bottom: 30px;
  padding: 0 20px;
}

.menu-mobile__link {
  text-decoration: none;
  display: flex;
  flex-direction: column;
  margin-bottom: 30px;
  font-size: 24px;
  font-weight: 400;
  color: #374151;
  padding: 0 20px;
  transition: 0.3s;
  line-height: 22.4px;
}

.menu-mobile__link:hover {
  color: #0369a1;
  transition: 0.3s;
}

.menu-mobile__link:active {
  color: #0c4a6e;
  transition: 0.3s;
}

.Company-name a {
  text-decoration: none;
  margin-right: 30px;
  font-size: 24px;
  font-weight: 700;
  color: #1f2937;
  line-height: 28.8px;

  @media screen and (max-width: 1024px) {
    font-size: 20px;
    margin-right: 15px;
  }
}

.header-catalog-wrapper {
  padding-top: 5px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;

  @media screen and (max-width: 1024px) {
    margin-right: 10px;
  }

  @media screen and (max-width: 768px) {
    display: none;
  }
}

.header-catalog-logo-wrapper {
  min-height: 22px;
  min-width: 23px;
}

.header-catalog-logo {
  width: 22px;
  height: 23px;
  margin-right: 4px;
}

.header-catalog-name {
  font-size: 16px;
  font-weight: 700;
  color: #374151;
  line-height: 22.4px;
}

.right-side {
  display: flex;
  align-items: center;
  justify-content: center;
}

.nav {
  display: flex;
  align-items: center;
  justify-content: center;

  @media screen and (max-width: 768px) {
    display: none;
  }
}

.menu__link {
  text-decoration: none;
  font-size: 16px;
  font-weight: 700;
  color: #374151;
  margin-right: 25px;
  transition: 0.3s;
  line-height: 22.4px;

  @media screen and (max-width: 1024px) {
    margin-right: 15px;
    font-size: 14px;
  }
}

.menu__link:hover {
  color: #0ea5e9;
  transition: 0.3s;
}

.menu__link:active {
  color: #374151;
  transition: 0.3s;
}
</style>
