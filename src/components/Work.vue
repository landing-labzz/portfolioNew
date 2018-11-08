<template lang="html">
  <div class="container" style="padding-top: 90px;">
    <row class="justify-content-center" >
      <div class="col-lg-3 container__works">
        <img class="icon__img mb-4" src="../assets/icon1.png" alt="">
        <h3 class="mb-4">Стратегия и планирование</h3>
        <p>
          Стратегия контента,
          Исследование, Анализ возможностей и
          стратегическое планирование
        </p>
      </div>
      <div class="col-lg-3 container__works">
        <img class="icon__img mb-4" src="../assets/icon2.png" alt="">
        <h3 class="mb-4">Дизайн и прототип</h3>
        <p>
          Дизайн интерфейса,
          Оформление и прототипирование,
          Визуальный дизайн, Адаптивный дизайн и UI-kits
        </p>

      </div>
      <div class="col-lg-3 container__works">
        <img class="icon__img mb-4" src="../assets/icon3.png" alt="">
        <h3 class="mb-4">Финальное тестирование</h3>
        <p>
          Финальное тестирование, Внесение првок,
          Оплата, запуск сайта на хостинге.
        </p>

      </div>
    </row>
  </div>
</template>

<script>
import { Row, } from 'mdbvue'
export default {
  name: 'work',
  components: {
    Row,
  }
}
</script>

<style lang="css">
.icon__img {
  max-width: 100%;
  margin: 0 auto;
  display: block;
  position: relative;
}
.container__works {
  display: flex;
  flex-flow: column;
  align-items: center;
}
.container__works h3 {
  color:  #222222;
  font-size: 20px;/* Приближение из-за подстановки шрифтов */
  font-weight: 500;
  line-height: 40px;/* Приближение из-за подстановки шрифтов */
  text-align: center;
}
.container__works {
  color:  #7c7c7c;
  font-size: 14px;/* Приближение из-за подстановки шрифтов */
  font-weight: 400;
  line-height: 30px;/* Приближение из-за подстановки шрифтов */
  text-align: center;
}
</style>
