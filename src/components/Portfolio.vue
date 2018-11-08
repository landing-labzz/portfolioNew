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
          <div v-on:click="modalForm"><i class="far fa-comment fa-2x ml-2 mr-2"></i></div>
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
          <div v-on:click="modalForm"><i class="far fa-comment fa-2x ml-2 mr-2"></i></div>
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
          <div v-on:click="modalForm"><i class="far fa-comment fa-2x ml-2 mr-2"></i></div>
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
          <div v-on:click="modalForm"><i class="far fa-comment fa-2x ml-2 mr-2"></i></div>
          <p>{{project_4.comments}}</p>
          <i class="fas fa-link fa-2x ml-2 mr-2"></i>
        </div>
      </div>

    </div>
    <div v-if="modal" class="modal__container pt-5">
      <div class="close_container">
        <i class="far fa-times-circle fa-2x" v-on:click="modal = false"></i>
      </div>
      <div class="card col-lg-6 m-auto --inner__modal" v-bind:style="maxLength ? 'overflow-y: scroll;' : 'overflow-y: hidden'" id="list_comments">
        <div class="card-body">

          <form @submit.prevent="addComents" class="mb-3" action="index.html" method="post">
            <input type="text"  v-model="name" class="form-control mb-2" name="" value="" placeholder="Your Name">
            <textarea name="name" v-model="textComment" class="form-control" rows="2" placeholder="Text comment" cols="80"></textarea>
            <button class="btn btn-outline-purple mb-2 mt-2" type="submit">Отправить</button>

          </form>
          <div class="col-lg-8 m-auto text-center">
            <span class="text-center mb-2">comments list</span>
            <hr  class="col-lg-3 m-auto"/>
          </div>
          <ul class="list-group list_comments" >
            <li v-for="(item , index) of comments_list_1"class="mb-2"><img src="../assets/logo.png" class="mr-3 mb-2" alt="">{{item.name}}: {{item.txt}}</li>

          </ul>
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
      modal: false,
      name: null,
      textComment: null,
      maxLength: false,

      comments_list_1: [
        {
          name: "Anton",
          txt: "Your amazing Project"

        },
        {
          name: "Сергей",
          txt: "Крутой проект, я бы добавил немного анимации",
        },
      ],
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
  // computed () {
  //   coments_list_1 () {
  //     this.project_1.comments_list.map()
  //   },
  // },
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
    modalForm () {
      this.modal = !this.modal;
      console.log(this.modal)
    },
    addComents () {
      this.comments_list_1.push({
        name: this.name,
        txt: this.textComment,
      })

      if (this.comments_list_1.length > 4){
        this.maxLength = true
      }
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
.modal__container {
  width: 100%;
  position: fixed;
  height: 100vh;
  background: rgba(0, 0, 0, 0.5);
  z-index: 777;
  display: block;
  top:0;
  left: 0;
}
.--inner__modal {
  z-index: 999;
  height: 90vh;

}
.list_comments {
  list-style-type: none !important;
  display: flex;
  flex-flow: column-reverse;
}
.close_container {
  position: absolute;
  right: 40px;
  top: 40px;
  z-index: 999;
  width: 40px;
  height: 40px;
}
</style>
