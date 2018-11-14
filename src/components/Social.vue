<template lang="html">
    <div class="view  jarallax" data-jarallax='{"speed": 0.2}' style="" id="others">
      <!-- Mask & flexbox options-->
      <div class="mask rgba-purple-slight d-flex justify-content-center align-items-center">
        <!-- Content -->
        <div class="container">
          <!--Grid row-->
          <div class="row wow fadeIn">
            <!--Grid column-->
            <div class="col-md-12 text-center">
              <h1 class="display-4 font-weight-bold mb-0 pt-md-5 pt-5 wow fadeInUp">Другие проекты</h1>
              <h5 class="pt-md-5 pt-sm-2 pt-5 pb-md-5 pb-sm-3 pb-5 wow fadeInUp" data-wow-delay="0.2s">
                Попробуйте другие проекты и подписывайтесь на меня в социальных сетях
              </h5>
            </div>
            <!--Grid column-->
          </div>
          <!--Grid row-->
          <div  class="row justify-content-center pt-5 projects_new">
            <div class="col-lg-5 col-md-8 col-sm-10 col-12 mr-4 pl-3 mb-2" style="padding:0;margin:0;">
              <img class="img__projects_blog card-img" src="../assets/blog.jpg" alt="">
            </div>
            <div class="col-lg-5 col-md-8 col-sm-10 col-12">
              <h3>Gorilla Web-Blog</h3>
              <p>Блог неутомимой гориллы, которая пытается объять необъятное. Космос, Разработка, Любовь и немного постов из твиттера</p>
              <a href="#" class="btn btn-outline-purple btn-rounded btn-md"><i class="fa fa-book left"></i>Читать блог</a>
            </div>
          </div>
          <div  class="row justify-content-center flex-wrap pt-2">
            <div class="col-lg-1 col-md-1 col-sm-2 col-3"><a href="https://www.facebook.com/profile.php?id=100016666712579"><i class="icon__social__block fab fa-facebook fa-3x"></i></a></div>
            <div class="col-lg-1 col-md-1 col-sm-2 col-3"><a href="https://vk.com/bayrer/"><i class="icon__social__block fab fa-vk fa-3x"></i></a></div>
            <div class="col-lg-1 col-md-1 col-sm-2 col-3"><a href="https://github.com/webdevsghost/"><i class="icon__social__block fab fa-github fa-3x"></i></a></div>
            <div class="col-lg-1 col-md-1 col-sm-2 col-3"><a href="https://www.linkedin.com/in/anton-lobanov-331a20174/"><i class="icon__social__block fab fa-linkedin fa-3x"></i></a></div>
            <div class="col-lg-1 col-md-1 col-sm-2 col-3"><a href="https://plus.google.com/u/0/112269380727500600137"><i class="icon__social__block fab fa-google-plus-g fa-3x "></i></a></div>
          </div>
        </div>

        <!-- Content -->
      </div>
      <!-- Mask & flexbox options-->
    </div>
    <!-- Full Page Intro -->
</template>

<script>
export default {
  name: 'social',
  data () {
    return {
      isProjects: false,
      isSocial: true,
    }
  },
  methods: {
    viewProjects () {
      this.isProjects = !this.isProjects;
      this.isSocial =  !this.isSocial
    },
  },

}
</script>

<style lang="css">
.icon__social__block {
  color: #000;
}
  .icon__social__block:hover {
    color: #fff ;
  }
  .jarallax {
    background-image: url('../assets/gradient2.png');
    background-repeat: no-repeat;
    background-size: cover;
    background-position: center center;
    width: 100%;
    padding:0;
    min-height: 110vh;
  }
  .img__projects_blog  {
    padding: 0;
    margin: 0;
  }
  @media screen  and (max-width: 576px ){
    .display-4 {
      font-size: 40px;
    }
    .jarallax {
      min-height: 115vh;
    }
  }
</style>
