<template>
  <div class="delivery-block">
    <h2 class="delivery-block__title">Доставка</h2>
    <table class="delivery-block__table">
      <thead>
        <tr class="delivery-block__header">
          <th>Транспортная компания</th>
          <th>Срок поставки</th>
          <th>Отправление из Йошкар-Олы</th>
          <th>Стоимость перевозки одной двери</th>
        </tr>
      </thead>
      <tbody>
        <tr
          class="delivery-block__item"
          v-for="(item, index) in deliveryCompanies"
          :key="index"
        >
          <td>{{ item.company }}</td>
          <td>{{ item.deadline }} дней</td>
          <td>{{ item.departure }}</td>
          <td>{{ item.price }} р.</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      deliveryCompanies: [
        {
          company: "Деловые линии",
          deadline: "7-10",
          departure: "По мере формирования",
          price: "1500-2000",
        },
        {
          company: "Байкал-сервис",
          deadline: "5-7",
          departure: "По мере формирования",
          price: "1200-1700",
        },
      ],
    };
  },
};
</script>

<style scoped>
.delivery-block {
  margin-bottom: 32px;
}

.delivery-block__title {
  margin-bottom: 16px;
  font-weight: 500;
  font-size: 24px;
  line-height: 32px;
}

.delivery-block__table {
  border-collapse: collapse;
  width: 100%;
}

.delivery-block__header {
  height: 19px;
}

.delivery-block__table th {
  height: 19px;
  font-size: 1rem;
  line-height: 120%;
  color: #111827;
  font-weight: 600;
  text-align: left;
}
.delivery-block__item {
  height: 65px;
}
.delivery-block__table td {
  font-size: 1rem;
  line-height: 120%;
  color: #4b5563;
  font-weight: 400;
}

@media (max-width: 768px) {
  .delivery-block__table th,
  .delivery-block__table td {
    font-size: 0.8rem;
  }
}
@media (max-width: 568px) {
  .delivery-block__table th,
  .delivery-block__table td {
    font-size: 0.6rem;
  }
}
</style>
