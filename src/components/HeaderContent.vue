<template lang="html">
  <div class="container container__content">
    <div class="text-center content__header">
      <h5 class="font-weight-bold text-white h5__content">{{titleSm}}</h5>
      <h1 class="font-weight-bold text-white">{{titleFirst}}</h1>
      <h2 class="font-weight-bold text-white">{{titleSecond}}</h2>
      <h3 class="font-weight-bold text-white">{{titleThree}}</h3>
    </div>
  </div>
</template>

<script>
export default {
  name: 'headercontent',
  props: {
    titleSm: String,
    titleFirst: String,
    titleSecond: String,
    titleThree: String,
  }
}
</script>

<style lang="css">
 .h5h5__content {
   font-family: Montserrat;
    color:  #e2e2e2;
    font-size: 20px;/* Приближение из-за подстановки шрифтов */
    font-weight: 400;
    line-height: 55px;/* Приближение из-за подстановки шрифтов */
    text-align: center;
 }
.container__content {
  height: 100%;
}
.content__header {
  display: flex;
  flex-flow: column;
  height: 60%;
  justify-content: center;
}

</style>
