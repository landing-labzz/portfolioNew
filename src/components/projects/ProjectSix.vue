<template lang="html">
  <div class="col-lg-4 col-md-6 col-sm-6 col-12 mb-5">
  <div class="">
    <div class="portfolio_img mb-2">
      <img class="mw-100" src="../../assets/tatooink.jpg" alt="">
        <div class="description__block">
          <h4 class="text-white font-weight-bold">{{project_6.name}}</h4>
          <span class="down_line mb-2"></span>
          <p class="text-white">{{project_6.description}}</p>
          <a
            href="https://tatooink.netlify.com"
            class="btn btn-sm btn-outline-white font-wheight-bold"
            style="width: 60%; display:block; margin: 0 auto;">
            View
            </a>
        </div>
    </div>
    <div class="row justify-content-center">
      <div v-on:click="editCounter_6">
        <i
          v-bind:style="redCounter_6 ? 'color: red;' : ''"
          class="far fa-heart fa-2x ml-2 mr-2">
        </i>
      </div>
      <p v-bind:style="redCounter_6 ? 'color: red;' : ''">{{likeCounter_6}}</p>
      <div v-on:click="modalFormSix"><i class="far fa-comment fa-2x ml-2 mr-2"></i></div>
      <p>{{commentsCounter_6}}</p>
      <div v-on:click="linkSix"><i class="fas fa-link fa-2x ml-2 mr-2"></i></div>

    </div>
    <input
      v-if="link_6"
      class="form-control"
      type="text"
      name="link"
      value="https://tatooink.netlify.com">
  </div>
  <!--end project -6 -->

  <!-- modal comments -->
  <div
    v-if="modal_6"
    class="modal__container pt-6"
  >
    <div class="close_container">
      <i
        class="far fa-times-circle fa-2x"
        v-on:click="modal_6 = false">
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
          @submit.prevent="addComents_6"
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
              {{commentsCounter_6}}
          </span>
        </span>
          <hr  class="col-lg-3 m-auto"/>
        </div>
        <ul class="list-group list_comments" >
          <li
            v-for="(item , index) of comments_list_6"
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
  name: 'projectFive',
  data () {
    return {
      likeCounter_6: 0,
      redCounter_6: false,
      commentsCounter_6: 0,
      modal_6: false,
      link_6: false,
      comments_list_6: [],
      textComment: null,
      name: null,
      maxLength: false,
      project_6:  {
          id: 6,
          name: 'Tatoo INK',
          description: 'Bootstrap шаблон сайта для тату студии',
        },
    }
  },
    created () {
        var self =  this;

        firebase.database().ref('likeCounter_6/').once('value').then(function(snapshot) {
          self.likeCounter_6 = snapshot.val()
        });

        var db = firebase.firestore();
        // Disable deprecated features
        db.settings({
          timestampsInSnapshots: true
        });

        db.collection("comment_list_6").get().then((querySnapshot) => {
            querySnapshot.forEach((doc) => {
              self.comments_list_6.push(doc.data());
            });
          self.commentsCounter_6 =   self.comments_list_6.length
        });
        if (localStorage.getItem('liked_6') === 'true') {
          this.redCounter_6 = true
        } else {
          this.redCounter_6 = false
        }
    },
    methods: {

      linkSix() {
        this.link_6 = !this.link_6
      },

      editCounter_6 () {
        var newPostKey = firebase.database().ref().child('list_comments_6').push().key;
        firebase.database().ref('likeCounter_6/').set(
            this.likeCounter_6 + 1
          );
        localStorage.setItem('liked_6', 'true')
        this.redCounter_6  = !this.redCounter_6;
        this.redCounter_6 ? this.likeCounter_6++ : this.likeCounter_6-- ;
      },
      modalFormSix () {
        this.modal_6 = !this.modal_6;
      },
      addComents_6 () {
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
        db.collection("comment_list_6").add(postData)
        .then(function(docRef) {
            console.log("Document written with ID: ", docRef.id);
        })
        .catch(function(error) {
            console.error("Error adding document: ", error);
        });
        this.comments_list_6.push(postData)
        this.commentsCounter_6 ++
        this.name = null
        this.textComment = null
        if (this.comments_list_6.length > 4){
          this.maxLength = true
        }
    },

  },
}
</script>

<style lang="css">
</style>
