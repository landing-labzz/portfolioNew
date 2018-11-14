<template lang="html">
  <div class="col-lg-4 col-md-6 col-sm-6 col-12 mb-5">
  <div class="">
    <div class="portfolio_img mb-2">
      <img class="mw-100" src="../../assets/email-template.jpg" alt="">
        <div class="description__block">
          <h4 class="text-white font-weight-bold">{{project_3.name}}</h4>
          <span class="down_line mb-2"></span>
          <p class="text-white">{{project_3.description}}</p>
          <a
            href="https://vigorous-wilson-3e14b7.netlify.com/"
            class="btn btn-sm btn-outline-white font-wheight-bold"
            style="width: 60%; display:block; margin: 0 auto;">
            View
            </a>
        </div>
    </div>
    <div class="row justify-content-center">
      <div v-on:click="editCounter_3">
        <i
          v-bind:style="redCounter_3 ? 'color: red;' : ''"
          class="far fa-heart fa-2x ml-2 mr-2">
        </i>
      </div>
      <p v-bind:style="redCounter_3 ? 'color: red;' : ''">{{likeCounter_3}}</p>
      <div v-on:click="modalFormThree"><i class="far fa-comment fa-2x ml-2 mr-2"></i></div>
      <p>{{commentsCounter_3}}</p>
      <div v-on:click="linkThree"><i class="fas fa-link fa-2x ml-2 mr-2"></i></div>

    </div>
    <input
      v-if="link_3"
      class="form-control"
      type="text"
      name="link"
      value="https://vigorous-wilson-3e14b7.netlify.com/">
  </div>
  <!--end project -5 -->

  <!-- modal comments -->
  <div
    v-if="modal_3"
    class="modal__container pt-5"
  >
    <div class="close_container">
      <i
        class="far fa-times-circle fa-2x"
        v-on:click="modal_3 = false">
      </i>
    </div>
    <div
      class="card col-lg-6 m-auto --inner__modal scrollbar-secondary"
      v-bind:style="maxLength ? 'overflow-y: scroll;' : 'overflow-y: hidden'"
      id="list_comments"
    >
      <div class="card-body">
        <h3
          class="text-center"
        >
          Оставьте свой коментарий. Ваше мнение очень важно для нас!
        </h3>
        <form
          @submit.prevent="addComents_3"
          class="mb-3"
          action="index.html"
          method="post"
        >
          <input
            type="text"
            v-model="name"
            class="form-control mb-2"
            name="name"
            placeholder="Ваше имя"
          >
          <textarea
            name="name"
            v-model="textComment"
            class="form-control"
            rows="2"
            placeholder="Коментарийt"
            cols="80"
          >
          </textarea>
          <button
            class="btn btn-outline-purple mb-2 mt-2"
            type="submit"
          >
            Добавить
          </button>

        </form>
        <div class="col-lg-8 m-auto text-center">
          <span
            class="text-center mb-2">
              Коментарии
          <span
            class="ml-2"
            style="fon-size: 8px !important; color: #333;">
              {{commentsCounter_3}}
          </span>
        </span>
          <hr  class="col-lg-3 m-auto"/>
        </div>
        <ul class="list-group list_comments" >
          <li
            v-for="(item , index) of comments_list_3"
            class="mb-2"><img src="../../assets/logo.png"
            class="mr-3 mb-2" alt="">
            {{item.name}}: {{item.txt}}
          </li>

        </ul>
      </div>
    </div>
  </div>
  <!-- end modal comments -->
</div>
</template>

<script>
export default {
  name: 'ProjectThree',
  data () {
    return {
      likeCounter_3: 0,
      redCounter_3: false,
      commentsCounter_3: 0,
      modal_3: false,
      link_3: false,
      comments_list_3: [],
      textComment: null,
      name: null,
      maxLength: false,
      project_3:  {
          id: 3,
          name: 'Email Template',
          description: 'Готовый шаблон Email - презентации',
        },
    }
  },
    created () {
        var self =  this;

        firebase.database().ref('likeCounter_3/').once('value').then(function(snapshot) {
          self.likeCounter_3 = snapshot.val()
        });

        var db = firebase.firestore();
        // Disable deprecated features
        db.settings({
          timestampsInSnapshots: true
        });

        db.collection("comment_list_3").get().then((querySnapshot) => {
            querySnapshot.forEach((doc) => {
              self.comments_list_3.push(doc.data());
            });
          self.commentsCounter_3 =   self.comments_list_3.length
        });
        if (localStorage.getItem('liked_3') === 'true') {
          this.redCounter_3 = true
        } else {
          this.redCounter_3 = false

        }
    },
    methods: {

      linkThree() {
        this.link_3 = !this.link_3
      },

      editCounter_3 () {
        var newPostKey = firebase.database().ref().child('list_comments_3').push().key;
        firebase.database().ref('likeCounter_3/').set(
            this.likeCounter_3 + 1
          );
        localStorage.setItem('liked_3', 'true')
        this.redCounter_3  = !this.redCounter_3;
        this.redCounter_3 ? this.likeCounter_3++ : this.likeCounter_3-- ;
      },
      modalFormThree () {
        this.modal_3 = !this.modal_3;
      },
      addComents_3 () {
        // Initialize Cloud Firestore through Firebase
        var db = firebase.firestore();

        // Disable deprecated features
        db.settings({
          timestampsInSnapshots: true
        });
        var postData = {
          name: this.name,
          txt: this.textComment,
        };
        db.collection("comment_list_3").add(postData)
        .then(function(docRef) {
            console.log("Document written with ID: ", docRef.id);
        })
        .catch(function(error) {
            console.error("Error adding document: ", error);
        });
        this.comments_list_3.push(postData)
        this.commentsCounter_3 ++
        this.name = null
        this.textComment = null
        if (this.comments_list_3.length > 4){
          this.maxLength = true
        }
    },

  },
}
</script>

<style lang="css">
</style>
