<template lang="html">
  <div class="container__portfolio pl-2 pr-2" >
    <div class="row">
      <div class="col-lg-3 col-md-6 col-sm-6 col-12 mb-5">
        <div class="portfolio_img mb-2">
          <img class="mw-100" src="../assets/job_1.png" alt="">
            <div class="description__block">
              <h4 class="text-white font-weight-bold">{{project_1.name}}</h4>
              <span class="down_line mb-2"></span>
              <p class="text-white">{{project_1.description}}</p>
              <a
                href=""
                class="btn btn-sm btn-outline-white font-wheight-bold"
                style="width: 60%; display:block; margin: 0 auto;">
                View
                </a>
            </div>
        </div>
        <div class="row justify-content-center">
          <div v-on:click="editCounter_1"><i v-bind:style="redCounter_1 ? 'color: red;' : ''" class="far fa-heart fa-2x ml-2 mr-2"></i></div>
          <p v-bind:style="redCounter_1 ? 'color: red;' : ''">{{likeCounter_1}}</p>
          <i class="far fa-comment fa-2x ml-2 mr-2"></i>
          <p>{{project_1.comments}}</p>
          <i class="fas fa-link fa-2x ml-2 mr-2"></i>
        </div>
      </div>

      <div class="col-lg-3 col-md-6 col-sm-6 col-12 mb-5">
        <div class="portfolio_img mb-2">
          <img class="mw-100" src="../assets/job_1.png" alt="">
            <div class="description__block">
              <h4 class="text-white font-weight-bold">{{project_2.name}}</h4>
              <span class="down_line mb-2"></span>
              <p class="text-white">{{project_2.description}}</p>
              <a
                href=""
                class="btn btn-sm btn-outline-white font-wheight-bold"
                style="width: 60%; display:block; margin: 0 auto;">
                View
                </a>
            </div>
        </div>
        <div class="row justify-content-center">
          <div v-on:click="editCounter_2"><i v-bind:style="redCounter_2 ? 'color: red;' : ''" class="far fa-heart fa-2x ml-2 mr-2"></i></div>
          <p v-bind:style="redCounter_2 ? 'color: red;' : ''">{{likeCounter_2}}</p>
          <i class="far fa-comment fa-2x ml-2 mr-2"></i>
          <p>{{project_2.comments}}</p>
          <i class="fas fa-link fa-2x ml-2 mr-2"></i>
        </div>
      </div>

      <div class="col-lg-3 col-md-6 col-sm-6 col-12 mb-5">
        <div class="portfolio_img mb-2">
          <img class="mw-100" src="../assets/job_1.png" alt="">
            <div class="description__block">
              <h4 class="text-white font-weight-bold">{{project_3.name}}</h4>
              <span class="down_line mb-2"></span>
              <p class="text-white">{{project_3.description}}</p>
              <a
                href=""
                class="btn btn-sm btn-outline-white font-wheight-bold"
                style="width: 60%; display:block; margin: 0 auto;">
                View
                </a>
            </div>
        </div>
        <div class="row justify-content-center">
          <div v-on:click="editCounter_3"><i v-bind:style="redCounter_3 ? 'color: red;' : ''" class="far fa-heart fa-2x ml-2 mr-2"></i></div>
          <p v-bind:style="redCounter_3 ? 'color: red;' : ''">{{likeCounter_3}}</p>
          <i class="far fa-comment fa-2x ml-2 mr-2"></i>
          <p>{{project_3.comments}}</p>
          <i class="fas fa-link fa-2x ml-2 mr-2"></i>
        </div>
      </div>

      <div class="col-lg-3 col-md-6 col-sm-6 col-12 mb-5">
        <div class="portfolio_img mb-2">
          <img class="mw-100" src="../assets/job_1.png" alt="">
            <div class="description__block">
              <h4 class="text-white font-weight-bold">{{project_4.name}}</h4>
              <span class="down_line mb-2"></span>
              <p class="text-white">{{project_4.description}}</p>
              <a
                href=""
                class="btn btn-sm btn-outline-white font-wheight-bold"
                style="width: 60%; display:block; margin: 0 auto;">
                View
                </a>
            </div>
        </div>
        <div class="row justify-content-center">
          <div v-on:click="editCounter_4"><i v-bind:style="redCounter_4 ? 'color: red;' : ''" class="far fa-heart fa-2x ml-2 mr-2"></i></div>
          <p v-bind:style="redCounter_4 ? 'color: red;' : ''">{{likeCounter_4}}</p>
          <i class="far fa-comment fa-2x ml-2 mr-2"></i>
          <p>{{project_4.comments}}</p>
          <i class="fas fa-link fa-2x ml-2 mr-2"></i>
        </div>
      </div>

    </div>

  </div>
</template>

<script>
export default {
  name: 'portfolio',
  data () {
    return {
      likeCounter_1: 323,
      redCounter_1: false,
      likeCounter_2: 432,
      redCounter_2: false,
      likeCounter_3: 3123,
      redCounter_3: false,
      likeCounter_4: 94,
      redCounter_4: false,
        project_1:  {
            id: 2,
            likes: 132,
            name: 'Project - 1',
            description: 'Some Project',
            comments: '34',
            color: null,
          },
          project_2:  {
              id: 2,
              likes: 92,
              name: 'Project - 2',
              description: 'Some Project',
              comments: '34',
              color: null,
            },
      project_3:  {
          id: 3,
          likes: 93,
          name: 'Project - 3',
          description: 'Some Project',
          comments: '11'

        },
      project_4:  {
          id: 4,
          likes:321,
          name: 'Project - 4',
          description: 'Some Project',
          comments: '45'

        },
    }
  },
  methods: {
    editCounter_1 () {
      this.redCounter_1  = !this.redCounter_1;
      this.redCounter_1 ? this.likeCounter_1++ : this.likeCounter_1--;
    },
    editCounter_2 () {
      this.redCounter_2  = !this.redCounter_2;
      this.redCounter_2 ? this.likeCounter_2++ : this.likeCounter_2--;
    },
    editCounter_3 () {
      this.redCounter_3  = !this.redCounter_3;
      this.redCounter_3 ? this.likeCounter_3++ : this.likeCounter_3--;
    },
    editCounter_4 () {
      this.redCounter_4  = !this.redCounter_4;
      this.redCounter_4 ? this.likeCounter_4++ : this.likeCounter_4--;
    },
  },
}
</script>

<style lang="css">
.container__portfolio {
  padding-top: 90px;
  padding-bottom: 90px;
}
.mw-100 {
  max-width: 100%;
}
.portfolio_img{
  position: relative;
  transition: all .4s ease;
  margin: 0;
  padding: 0;
}
.portfolio_img::before{
  content: '';
  background-color:  rgba(0, 0, 0, 0.8);
  position: absolute;
  width: 100%;
  height: 0;
  opacity: 0;
  transition: all .7s ease-in-out;
}
.portfolio_img:hover::before {
  opacity: 1;
  height: 100%;
}
.description__block {
  position: absolute;
  width: 100%;
  height: 0;
  z-index: 555;
  display: block;
  top: 0;
  opacity: 0;
  transition: all 1.2s ease-in-out;
  text-align: center;
  display: flex;
  flex-flow: column;
  justify-content: center;
}
.portfolio_img:hover .description__block{
  height: 100%;
  opacity: 1;
}
.down_line {
  width: 45px;
  background: #fff;
  display: block;
  margin: 0 auto;
  height: 1px;
}
</style>
