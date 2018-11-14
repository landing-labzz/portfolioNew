<template lang="html">
  <div class="">
    <nav class="navbar navbar-scroll">
      <a class="navbar-brand" href="#">
        <div class="row pl-3 align-items-center">
          <img class="logo__img" src="../assets/logo.png" alt="">
          <h3 class="font-weight-bold text-white ml-3 brand-text" style="text-transform: uppercase;">landing LAbzz</h3>
        </div>
        </a>
        <button v-on:click="openModal" type="button" class="btn__quest" name="button">Задать вопрос</button>

          <div class="hamburger__block" v-on:click="slideMenuOpen">
            <span v-bind:class="slideMenu ? 'hidden_item': ''" class="hamburger__item mb-2 mt-2"></span>
            <span v-bind:class="slideMenu ? 'active__item_first' : '' " class="hamburger__item mb-2"></span>
            <span v-bind:class="slideMenu ? 'active__item_second' : '' " class="hamburger__item mb-2"></span>
          </div>

    </nav>
    <div
      v-bind:style="hamburgerMenu ? 'visibility: visible; width :0;' :  'visibility: hidden;width:100%;'"
      class="hamburger__menu__container"
    >
    <ul style="list-style-type: none;" class="pt-3 pl-4  pr-4 pb-3 hamburger_ul">
      <li class="mb-2"><a class="link-hamburger font-weight-bold lead text-white" href="#">Главная</a></li>
      <li class="mb-2"><a class="link-hamburger font-weight-bold lead text-white" href="#portfolio">Портфолио</a></li>
      <li class="mb-2"><a class="link-hamburger font-weight-bold lead text-white" href="#about">Обо мне</a></li>
      <li class="mb-2"><a class="link-hamburger font-weight-bold lead text-white" href="#skills">Навыки</a></li>
      <li class="mb-2"><a class="link-hamburger font-weight-bold lead text-white" href="#work">Процесс</a></li>
      <li class="mb-2"><a class="link-hamburger font-weight-bold lead text-white" href="#contact">Контакты</a></li>
      <li class="mb-2"><a class="link-hamburger font-weight-bold lead text-white" href="#features">Преимущества</a></li>
      <li class="mb-2"><a class="link-hamburger font-weight-bold lead text-white" href="#others">Другие проекты</a></li>
      <li class="mb-2">
        <button v-on:click="openModal" type="button" class="btn__quest" name="button">Задать вопрос</button>
      </li>
    </ul>
    </div>
    <modal v-if="modal" @close="modal = false">
      <modal-header>
        <img class="mr-3" src="../assets/logo.png" alt="">
        <modal-title>Задать вопрос</modal-title>
      </modal-header>
      <modal-body>
        <!-- Material form subscription -->
        <form class="form-group justify-content-center">
          <p class="h5 text-center mb-4">Если у вас есть вопросы или предложения, напишите мне!</p>
          <div class="grey-text m-auto col-lg-10" style="display: block; margin 0 auto;">
            <input class="form-control mb-2" placeholder="Ваше Имя " type="text"/>
            <input class="form-control mb-2" placeholder="Ваш Email" type="email"/>
            <textarea name="name" class="form-control mb-3" placeholder="Сообщение" rows="4" cols="40"></textarea>
          </div>
          <div class="text-center">
            <button class="btn btn-outline-purple btn-md">Send <i class="text-purple ml-1 fa fa-paper-plane-o"></i></button>
          </div>
        </form>
        <!-- Material form subscription -->
      </modal-body>
    </modal>
  </div>
</template>

<script>
import { Modal, ModalHeader, ModalTitle, ModalBody, ModalFooter, Btn,} from 'mdbvue';
export default {
  name: 'navbar',
  components: {
    Modal,
    ModalHeader,
    ModalTitle,
    ModalBody,
    ModalFooter,
    Btn,
  },
  data () {
    return {
      modal: false,
      hamburgerMenu:  false,
      slideMenu: false,
    }
  },
  methods: {
    slideMenuOpen () {
      this.slideMenu = !this.slideMenu
      this.hamburgerMenu = !this.hamburgerMenu
    },
    openModal () {
      this.modal = !this.motal
    }
  }
}
</script>

<style lang="css">
.hamburger__menu__container {
  width: 300px;
  min-height: 250px;
  position: absolute;
  transition: all .6s ease;
  background: rgba(96, 9, 255, .6);
  border-radius: 10px;

}
.hamburger_ul {
  display: flex;
  flex-flow: column;
  align-items: flex-end;
}
.hamburger__block {
  display: flex;
  flex-flow: column;
  width: 50px;
  position: relative;
  height: 50px;
  top: 0;
  z-index: 999;
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
