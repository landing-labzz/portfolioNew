<template lang="html">
  <div class="container text-center container__title">
    <h1 class="font-weight-bold text-black text-center mb-4">{{titleLg}}</h1>
    <h3 class="font-weight-bold text-black text-center">{{titleMd}}</h3>
    <h5 class="font-weight-bold text-black text-center">{{titleSm}}</h5>
    <p class="col-lg-7 text-center m-auto ">{{description}}</p>
  </div>
</template>

<script>
export default {
  name: 'title',
  props: {
    titleLg: String,
    titleMd: String,
    titleSm: String,
    description: String,
  },
}
</script>

<style lang="css">
.container__title p{
  color:  #222222;
  font-size: 16px;/* Приближение из-за подстановки шрифтов */
  font-weight: 400;
  line-height: 35px;/* Приближение из-за подстановки шрифтов */
  text-align: center;
}
</style>
