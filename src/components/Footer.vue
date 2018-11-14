<template lang="html">
  <!-- Section: Contact v.1 -->
<section class="my-5" id="contact">

  <!-- Section heading -->
  <h2 class="h1-responsive font-weight-bold text-center my-5">Контакты</h2>
  <!-- Section description -->
  <p class="text-center w-responsive mx-auto pb-5">
    Остались вопросы? Есть предложения? Напишите, я очень люблю общаться и отвечу на все вопросы.</p>

  <!-- Grid row -->
  <div class="row">

    <!-- Grid column -->
    <div class="col-lg-5 col-md-8 col-sm-8 col-10 mx-auto mb-lg-0 mb-4">

      <!-- Form with header -->
      <div class="card">
        <div class="card-body">
          <!-- Header -->
          <div class="card-header purple-gradient accent-1">
            <h3 class="mt-2"><i class="fa fa-envelope"></i> Напишите мне:</h3>
          </div>
          <!-- Body -->
          <div class="md-form">
            <i class="fa fa-user prefix grey-text"></i>
            <input type="text" id="form-name" class="form-control">
            <label for="form-name">Ваше имя</label>
          </div>
          <div class="md-form">
            <i class="fa fa-envelope prefix grey-text"></i>
            <input type="text" id="form-email" class="form-control">
            <label for="form-email">Ваш Email</label>
          </div>
          <div class="md-form">
            <i class="fa fa-tag prefix grey-text"></i>
            <input type="text" id="form-Subject" class="form-control">
            <label for="form-Subject">Тема письма</label>
          </div>
          <div class="md-form">
            <i class="fa fa-pencil prefix grey-text"></i>
            <textarea type="text" id="form-text" class="form-control md-textarea" rows="3"></textarea>
            <label for="form-text">Сообщение</label>
          </div>
          <div class="text-center">
            <button class="btn btn-outline-purple">Отправить</button>
          </div>
        </div>
      </div>
      <!-- Form with header -->

    </div>
    <!-- Grid column -->

    <!-- Grid column -->
    <div class="col-lg-7 col-md-10 col-sm-10 col-10 mx-auto">

      <!-- Google map-->
      <div id="map-container" class="rounded z-depth-1-half map-container">
        <iframe style="width:100%;" src="https://yandex.ru/map-widget/v1/?um=constructor%3Ab1326008d989475314b719c69cd55d20c8cf831bd50ff59204c71066e3ff4ce8&amp;source=constructor"  height="400" frameborder="0"></iframe>
      </div>
      <br>
      <!-- Buttons-->
      <div class="row text-center">
        <div class="col-md-3">
          <a class="">
            <i style="color: purple;" class="fa fa-map-marker fa-2x"></i>
          </a>
          <p>Орел, 302025</p>
          <p class="mb-md-0">Россия</p>
        </div>
        <div class="col-md-3">
          <a href="tel:89961666762" class="">
            <i style="color: purple;" class="fa fa-phone fa-2x"></i>
          </a>
          <p>+ 7 (996) 166 67-62</p>
          <p class="mb-md-0">Понедельник - Пятница, 8:00-22:00</p>
        </div>
        <div class="col-md-4">
          <a class="">
            <i style="color: purple;" class="fa fa-envelope fa-2x"></i>
          </a>
          <p>wrestbild57@gmail.com</p>
          <p class="mb-0">lobanow.wrestbild57@yandex.ru</p>
        </div>
      </div>

    </div>
    <!-- Grid column -->

  </div>
  <!-- Grid row -->

</section>
<!-- Section: Contact v.1 -->
</template>

<script>
export default {
}
</script>

<style lang="css">
.purple-gradient {
    background: -webkit-linear-gradient(50deg,#ff6ec4,#7873f5)!important;
    background: -o-linear-gradient(50deg,#ff6ec4,#7873f5)!important;
    background: linear-gradient(40deg,#ff6ec4,#7873f5)!important;
}
</style>
