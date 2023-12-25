<template>
  <div class="HeaderCatalog-container">
    <div class="HeaderCatalog-wrapper">
      <ul class="HeaderCatalog-list">
        <li
          class="HeaderCatalog-list__list-item"
          v-for="(category, index) in categories"
          :key="index"
          @mouseover="showBlock(index)"
        >
          <NuxtLink :to="category.link">
            {{ category.label }}
          </NuxtLink>
          <img
            class="HeaderCatalog-arrow"
            src="../public/svg/headerCatalogArrow.svg"
            alt="headerCatalogArrow"
          />
        </li>
      </ul>
      <div v-if="showBlockIndex !== null" class="description-block">
        <div class="description-block-title">
          {{ categories[showBlockIndex].label }}
        </div>
        <div class="description-block-links">
          <ul class="description-block-list">
            <li
              class="description-block-list__list-item"
              v-for="(link, linkIndex) in categories[showBlockIndex].links"
              :key="linkIndex"
            >
              <NuxtLink :to="link.link">{{ link.label }}</NuxtLink>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const showBlockIndex = ref(null);

const categories = [
  {
    link: "#",
    label: "Входные двери",
    links: [
      {
        label: "Двери с терморазрывом (4)",
        link: "#",
      },
      {
        label: "Премиум (10)",
        link: "#",
      },
      {
        label: "Стандарт (12)",
        link: "#",
      },
      {
        label: "Элитные (8)",
        link: "#",
      },
      {
        label: "Уличные двери (4)",
        link: "#",
      },
    ],
  },
  {
    link: "#",
    label: "Внешняя отделка",
    links: [
      {
        label: "Двери с терморазрывом (1000)",
        link: "#",
      },
      {
        label: "Премиум (10)",
        link: "#",
      },
      {
        label: "Стандарт (55)",
        link: "#",
      },
      {
        label: "Элитные (8)",
        link: "#",
      },
      {
        label: "Уличные двери (4)",
        link: "#",
      },
    ],
  },
  {
    link: "#",
    label: "Отделка панелью",
    links: [
      {
        label: "Двери с терморазрывом (4)",
        link: "#",
      },
      {
        label: "Стандарт (12)",
        link: "#",
      },
      {
        label: "Элитные (8)",
        link: "#",
      },
      {
        label: "Уличные двери (4)",
        link: "#",
      },
    ],
  },
  {
    link: "#",
    label: "Фурнитура",
    links: [
      {
        label: "Элитные (8)",
        link: "#",
      },
      {
        label: "Уличные двери (4)",
        link: "#",
      },
    ],
  },
];

const showBlock = (index) => {
  showBlockIndex.value = index;
};
</script>

<style>
.HeaderCatalog-container {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}

.HeaderCatalog-wrapper {
  min-width: 1210px;
  height: 229px;
  display: flex;
  align-items: center;
  justify-content: flex-start;
}

.HeaderCatalog-list {
  width: 209px;
  height: 229px;
  padding: 20px, 10px, 0px, 0px;
  border: 0px, 1px, 0px, 0px;
  gap: 8px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  border-right: 1px solid #e5e7eb;
}

.HeaderCatalog-list__list-item {
  width: 199px;
  height: 36px;
  border-radius: 4px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding-right: 10px;
  padding-left: 10px;
  padding-top: 6px;
  padding-bottom: 6px;
  cursor: pointer;
  font-family: Sansation;
  font-size: 16px;
  font-weight: 700;
  line-height: 22px;
  letter-spacing: 0em;
  text-align: left;
}

.HeaderCatalog-list__list-item:hover {
  background-color: #f3f4f6;
}

.HeaderCatalog-list__list-item a {
  text-decoration: none;
  color: #374151;
}

.description-block {
  width: 474px;
  height: 183px;
  padding-top: 10px;
  padding-left: 44px;
}

.description-block-title {
  font-family: Sansation;
  font-size: 24px;
  font-weight: 400;
  line-height: 29px;
  letter-spacing: 0em;
  text-align: left;
  margin-bottom: 20px;
}

.description-block-list {
  width: 474px;
  height: 114px;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 30px 50px;
}

.description-block-list__list-item a {
  text-decoration: none;
  font-family: Sansation;
  font-size: 16px;
  font-weight: 700;
  line-height: 18px;
  letter-spacing: 0em;
  text-align: left;
  color: #6b7280;
  transition: 0.3s;
}

.description-block-list__list-item a:hover {
  color: #0ea5e9;
  transition: 0.3s;
}

.description-block-list__list-item a:active {
  color: #6b7280;
  transition: 0.3s;
}
</style>
