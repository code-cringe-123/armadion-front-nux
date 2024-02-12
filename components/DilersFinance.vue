<template>
  <div class="finance-card">
    <div class="finance-card__content">
      <h3>{{ item.price }}</h3>
      <p>{{ item.description }}</p>
      <span>{{ item.city }}</span>
    </div>
  </div>
</template>
<script>
export default {
  name: "DilersFinance",
  props: {
    item: Object,
  },
};
</script>
<style>
.finance-card {
  width: calc(50% - 10px);
  box-shadow: 1px 1px 5px rgba(0, 0, 0, 0.1);
  background: radial-gradient(
    427.63% 102.96% at 50% 50%,
    rgb(255, 255, 255) 0%,
    rgb(235, 236, 240) 100%
  );
  height: 200px;
  display: inline-block;
  border-radius: 8px;
}
.finance-card:hover {
  background: linear-gradient(135deg, #fff 0%, #ebecf0 100%);
}

.finance-card__content {
  padding: 20px 24px;
}
.finance-card__content h3 {
  font-size: 2.25rem;
  line-height: 105%;
  font-weight: 400;
  color: #1f2937;
  margin-bottom: 20px;
}
.finance-card__content p {
  font-size: 1.5rem;
  line-height: 120%;
  font-weight: 400;
  color: #111827;
  margin-bottom: 52px;
}
.finance-card__content span {
  font-size: 16px;
  line-height: 120%;
  font-weight: 400;
  color: #4b5563;
}

@media (max-width: 1300px) {
  .finance-card__content {
    padding: 20px;
  }
  .finance-card__content p {
    margin-bottom: 25px;
  }
}
@media (max-width: 990px) {
  .finance-card {
    width: 100%;
    margin: 0 auto;
  }
}
@media (max-width: 568px) {
  .finance-card {
    height: 170px;
  }
  .finance-card__content {
    padding: 15px;
  }
  .finance-card__content h3 {
    font-size: 1.8rem;
  }
  .finance-card__content p {
    font-size: 1.1rem;
    margin-bottom: 20px;
  }
}
</style>
