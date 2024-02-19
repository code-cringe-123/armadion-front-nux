<template>
  <div class="deliv__container">
    <div class="deliv__wrapper">
      <!-- <img src="../public/svg/zz.svg" alt="" class="deliv__img"> -->
      <div class="deliv-text__block">
        <h2 class="deliv__title" style="padding-top: 50px">Наша гарантия</h2>

        <section class="first__section">
          <h3 class="section-f__title">1. Условия гарантии</h3>
          <p class="section-f__subtitle" style="margin-bottom: 12px">
            Надежная работа дверей зависит от правильной установки, эксплуатации
            и своевременного технического обслуживания. Монтаж должен
            осуществляться специально обученными бригадами официального
            представителя компании.
            <br />
            <br />
            Гарантийная таблица на продукцию:
          </p>
          <table class="table-products_g" style="margin-bottom: 12px">
            <thead>
              <tr>
                <th>Продукция</th>
                <th>Гарантийный срок, месяц</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td>
                  Двери из металла, изготовленные и установленные нашей
                  компанией
                </td>
                <td>12</td>
              </tr>
              <tr>
                <td>
                  Замки стандартной комплектации и российского производства
                </td>
                <td>12</td>
              </tr>
              <tr>
                <td>Замки итальянского производства</td>
                <td>24</td>
              </tr>
              <tr>
                <td>Дверная фурнитура</td>
                <td>6</td>
              </tr>
              <tr>
                <td>Отделку (зависит от вида покрытия)</td>
                <td>6 - 12</td>
              </tr>
            </tbody>
          </table>

          <p class="section-f__subtitle" style="margin-bottom: 12px">
            Во время действия гарантии, починка металлической двери выполняется
            бесплатно при предъявлении гарантийного талона. Обязательства по
            гарантийному ремонту не относятся к изделиям, установленным
            сторонними лицами.
          </p>
        </section>

        <section class="first__section">
          <h3 class="section-f__title">
            2. Гарантийное обслуживание не осуществляется в следующих случаях
          </h3>
          <ul class="section-f__list-gar">
            <li class="section-f__item-gar section-f__subtitle">
              3.1. Потеря договора заказ-наряда.
            </li>
            <li class="section-f__item-gar section-f__subtitle">
              3.2. В случае выявления дефектов, полученных при транспортировке и
              монтажных работах двери сторонним подрядчиком.
            </li>
            <li class="section-f__item-gar section-f__subtitle">
              3.3. При обнаружении дефекта двери, полученного при форс-мажорных
              обстоятельствах, а также умышленных или неосторожных действий
              заказчика или третьего лица.
            </li>
            <li class="section-f__item-gar section-f__subtitle">
              3.4. Присутствие повреждений, образованных посредством попадания
              внутрь изделия посторонних предметов, химических веществ,
              строительного мусора и т.д.
            </li>
            <li class="section-f__item-gar section-f__subtitle">
              3.5. В случае нарушений заказчиком правил эксплуатации данной
              инструкции, повлекших появление дефекта двери.
            </li>
            <li class="section-f__item-gar section-f__subtitle">
              3.6. В случае неединичного нарушения заказчиком рекомендаций
              специалистов фирмы-исполнителя, направленных на устранение причин,
              которые способствуют нарушению правильного функционирования
              дверного механизма.
            </li>
            <li class="section-f__item-gar section-f__subtitle">
              3.7. В случае наличия неисправностей, по изменению конструкции,
              установке механизмов, не предусматриваемых и не одобряемых
              изготовителем.
            </li>
          </ul>
        </section>
      </div>
    </div>
  </div>
</template>
<script src="/static/build/app.js"></script>

   <script>
       if ('serviceWorker' in navigator) {
           window.addEventListener('load', function() {
               navigator.serviceWorker.register('/service-worker.js').then(function(registration) {
                   // Registration was successful
               console.log('ServiceWorker registration successful with scope: ', registration.scope);
             }, function(err) {
               // registration failed :(
               console.log('ServiceWorker registration failed: ', err);
             }).catch(function(err) {
               console.log(err)
             });
           });
         } else {
           console.log('service worker is not supported');
         }
   </script>

<style>
.table-products_g {
  width: 100%;
  border-collapse: collapse;
  margin-top: 15px;
}

.table-products_g th,
.table-products_g td {
  border: 1px solid rgba(0, 0, 0, 0.2);
  padding: 10px;
}

.section-f__item-gar {
  margin-bottom: 10px;
}
</style>
