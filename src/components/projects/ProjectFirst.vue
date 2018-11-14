<template lang="html">
  <div class="col-lg-4 col-md-6 col-sm-6 col-12 mb-5">
  <div class="">
    <div class="portfolio_img mb-2">
      <img class="mw-100" src="../../assets/prezent_ecostart.png" alt="">
        <div class="description__block">
          <h4 class="text-white font-weight-bold">{{project_1.name}}</h4>
          <span class="down_line mb-2"></span>
          <p class="text-white">{{project_1.description}}</p>
          <a
            href="https://eco-start.com"
            class="btn btn-sm btn-outline-white font-wheight-bold"
            style="width: 60%; display:block; margin: 0 auto;">
            View
            </a>
        </div>
    </div>
    <div class="row justify-content-center">
      <div v-on:click="editCounter_1">
        <i
          v-bind:style="redCounter_1 ? 'color: red;' : ''"
          class="far fa-heart fa-2x ml-2 mr-2">
        </i>
      </div>
      <p v-bind:style="redCounter_1 ? 'color: red;' : ''">{{likeCounter_1}}</p>
      <div v-on:click="modalFormFirst"><i class="far fa-comment fa-2x ml-2 mr-2"></i></div>
      <p>{{commentsCounter_1}}</p>
      <div v-on:click="linkFirst"><i class="fas fa-link fa-2x ml-2 mr-2"></i></div>

    </div>
    <input
      v-if="link_1"
      class="form-control"
      type="text"
      name="link"
      value="https://eco-start.com">
  </div>
  <!--end project -5 -->

  <!-- modal comments -->
  <div
    v-if="modal_1"
    class="modal__container pt-5"
  >

    <div
      class="card col-lg-6 m-auto --inner__modal scrollbar-secondary"
      v-bind:style="maxLength ? 'overflow-y: scroll;' : 'overflow-y: hidden'"
      id="list_comments"
    >
    <div class="close_container">
      <i
        class="far fa-times-circle fa-2x"
        v-on:click="modal_1 = false">
      </i>
    </div>
      <div class="card-body">
        <h3
          class="text-center"
        >
          Оставьте свой коментарий. Ваше мнение очень важно для нас!
        </h3>
        <form
          @submit.prevent="addComents_1"
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
              {{commentsCounter_1}}
          </span>
        </span>
          <hr  class="col-lg-3 m-auto"/>
        </div>
        <ul class="list-group list_comments" >
          <li
            v-for="(item , index) of comments_list_1"
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
  name: 'projectFirst',
  data () {
    return {
      likeCounter_1: 0,
      redCounter_1: false,
      commentsCounter_1: 0,
      modal_1: false,
      link_1: false,
      comments_list_1: [],
      textComment: null,
      name: null,
      maxLength: false,
      project_1:  {
          id: 1,
          name: 'EcoStart',
          description: 'Сайт криптовалюты TEC',
        },
    }
  },
    created () {
        var self =  this;

        firebase.database().ref('likeCounter_1/').once('value').then(function(snapshot) {
          self.likeCounter_1 = snapshot.val()
        });

        var db = firebase.firestore();
        // Disable deprecated features
        db.settings({
          timestampsInSnapshots: true
        });

        db.collection("comment_list_1").get().then((querySnapshot) => {
            querySnapshot.forEach((doc) => {
              self.comments_list_1.push(doc.data());
            });
          self.commentsCounter_1 =   self.comments_list_1.length
        });
        if (localStorage.getItem('liked_1') === 'true') {
          this.redCounter_1 = true
        } else {
          this.redCounter_1 = false

        }
    },
    methods: {

      linkFirst() {
        this.link_1 = !this.link_1
      },

      editCounter_1 () {
        var newPostKey = firebase.database().ref().child('list_comments_1').push().key;
        firebase.database().ref('likeCounter_1/').set(
            this.likeCounter_1 + 1
          );
        localStorage.setItem('liked_1', 'true')
        this.redCounter_1  = !this.redCounter_1;
        this.redCounter_1 ? this.likeCounter_1++ : this.likeCounter_1-- ;
      },
      modalFormFirst () {
        this.modal_1 = !this.modal_1;
      },
      addComents_1 () {
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
        db.collection("comment_list_1").add(postData)
        .then(function(docRef) {
            console.log("Document written with ID: ", docRef.id);
        })
        .catch(function(error) {
            console.error("Error adding document: ", error);
        });
        this.comments_list_1.push(postData)
        this.commentsCounter_1 ++
        this.name = null
        this.textComment = null
        if (this.comments_list_1.length > 4){
          this.maxLength = true
        }
    },

  },
}
</script>

<style lang="css">
</style>
