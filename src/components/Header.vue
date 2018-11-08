<template lang="html">
  <div class="header__container">
    <Navbar />
    <HeaderContent
      titleSm="landing pages and web-development"
      titleFirst="Привет, Меня зовут Антон!"
      titleThree="Я разрабатываю Landing Page и SPA-приложения" />
  </div>
</template>

<script>
import Navbar from './Navbar'
import HeaderContent from './HeaderContent'
export default {
  name: 'header',
  components: {
    Navbar,
    HeaderContent,

  }
}
</script>

<style lang="css">
.header__container {
  background-image: url('../assets/bg.png');
  background-size: 100%;
  background-repeat: no-repeat;
  width: 100%;
  height: 668px;
}
</style>
