<template lang="html">
  <div class="">
    <nav class="navbar navbar-scroll">
      <a class="navbar-brand" href="#">
        <div class="row pl-3 align-items-center">
          <img class="logo__img" src="../assets/logo.png" alt="">
          <h3 class="font-weight-bold text-white ml-3 brand-text" style="text-transform: uppercase;">landingLAb</h3>
        </div>
        </a>
        <button type="button" class="btn__quest" name="button">Задать вопрос</button>

          <div class="hamburger__block" v-on:click="slideMenuOpen">
            <span v-bind:class="slideMenu ? 'hidden_item': ''" class="hamburger__item mb-2 mt-2"></span>
            <span v-bind:class="slideMenu ? 'active__item_first' : '' " class="hamburger__item mb-2"></span>
            <span v-bind:class="slideMenu ? 'active__item_second' : '' " class="hamburger__item mb-2"></span>
          </div>

    </nav>

  </div>
</template>

<script>
export default {
  name: 'navbar',
  data () {
    return {
      modal: false,
      slideMenu: false,
    }
  },
  methods: {
    slideMenuOpen () {
      this.slideMenu = !this.slideMenu
    },
  }
}
</script>

<style lang="css">

.hamburger__block {
  display: flex;
  flex-flow: column;
  width: 50px;
  position: relative;
  height: 50px;
  top: 0;
  z-index: 555;
}
.hamburger__block .hamburger__item {
  width: 35px;
  height: 2px;
  background: #fff;
  transition: all .4s ease-in-out;
}
.active__item_first {
  transform: rotate(45deg);
  position: absolute;
  top: 20px;
  left: 0;
}
.active__item_second {
  transform: rotate(-45deg);
  position: absolute;
  top: 20px;
  left: 0;
}
.hidden_item {
  opacity: 0;
}
.btn__quest {
  background: transparent;
  border-width: 2px;
  border-color:  #71b4ff;
  border-style: solid;
  width: 156px;
  height: 42px;
  color: #fff;
  text-transform: uppercase;
  margin-left: 280px;
  border-radius: 5px;
}
@media screen and (max-width: 824px){

  .btn__quest {
    margin-left: 240px;
  }
}
@media screen and (max-width: 768px){
  .brand-text {
    display: none;
  }
  .btn__quest {
    display: none;
  }
}
</style>
