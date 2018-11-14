<template lang="html">
  <div class="col-lg-4 col-md-6 col-sm-6 col-12 mb-5">
  <div class="">
    <div class="portfolio_img mb-2">
      <img class="mw-100" src="../../assets/portfolio.jpg" alt="">
        <div class="description__block">
          <h4 class="text-white font-weight-bold">{{project_5.name}}</h4>
          <span class="down_line mb-2"></span>
          <p class="text-white">{{project_5.description}}</p>
          <a
            href="https://web-devs.netlify.com"
            class="btn btn-sm btn-outline-white font-wheight-bold"
            style="width: 60%; display:block; margin: 0 auto;">
            View
            </a>
        </div>
    </div>
    <div class="row justify-content-center">
      <div v-on:click="editCounter_5">
        <i
          v-bind:style="redCounter_5 ? 'color: red;' : ''"
          class="far fa-heart fa-2x ml-2 mr-2">
        </i>
      </div>
      <p v-bind:style="redCounter_5 ? 'color: red;' : ''">{{likeCounter_5}}</p>
      <div v-on:click="modalFormFive"><i class="far fa-comment fa-2x ml-2 mr-2"></i></div>
      <p>{{commentsCounter_5}}</p>
      <div v-on:click="linkFive"><i class="fas fa-link fa-2x ml-2 mr-2"></i></div>

    </div>
    <input
      v-if="link_5"
      class="form-control"
      type="text"
      name="link"
      value="https://web-devs.netlify.com">
  </div>
  <!--end project -5 -->

  <!-- modal comments -->
  <div
    v-if="modal_5"
    class="modal__container pt-5"
  >
    <div class="close_container">
      <i
        class="far fa-times-circle fa-2x"
        v-on:click="modal_5 = false">
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
          @submit.prevent="addComents_5"
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
              {{commentsCounter_5}}
          </span>
        </span>
          <hr  class="col-lg-3 m-auto"/>
        </div>
        <ul class="list-group list_comments" >
          <li
            v-for="(item , index) of comments_list_5"
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
      likeCounter_5: 0,
      redCounter_5: false,
      commentsCounter_5: 0,
      modal_5: false,
      link_5: false,
      comments_list_5: [],
      textComment: null,
      name: null,
      maxLength: false,
      project_5:  {
          id: 5,
          name: 'Web-devs',
          description: 'Сайт - портфолио, для фрилансера',
        },
    }
  },
    created () {
        var self =  this;

        firebase.database().ref('likeCounter_5/').once('value').then(function(snapshot) {
          self.likeCounter_5 = snapshot.val()
        });

        var db = firebase.firestore();
        // Disable deprecated features
        db.settings({
          timestampsInSnapshots: true
        });

        db.collection("comment_list_5").get().then((querySnapshot) => {
            querySnapshot.forEach((doc) => {
              self.comments_list_5.push(doc.data());
            });
          self.commentsCounter_5 =   self.comments_list_5.length
        });
        if (localStorage.getItem('liked_5') === 'true') {
          this.redCounter_5 = true
        } else {
          this.redCounter_5 = false
        }
    },
    methods: {

      linkFive() {
        this.link_5 = !this.link_5
      },

      editCounter_5 () {
        var newPostKey = firebase.database().ref().child('list_comments_5').push().key;
        firebase.database().ref('likeCounter_5/').set(
            this.likeCounter_5 + 1
          );
        localStorage.setItem('liked_5', 'true')
        this.redCounter_5  = !this.redCounter_5;
        this.redCounter_5 ? this.likeCounter_5++ : this.likeCounter_5-- ;
      },
      modalFormFive () {
        this.modal_5 = !this.modal_5;
      },
      addComents_5 () {
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
        db.collection("comment_list_5").add(postData)
        .then(function(docRef) {
            console.log("Document written with ID: ", docRef.id);
        })
        .catch(function(error) {
            console.error("Error adding document: ", error);
        });
        this.comments_list_5.push(postData)
        this.commentsCounter_5 ++
        this.name = null
        this.textComment = null
        if (this.comments_list_5.length > 4){
          this.maxLength = true
        }
    },

  },
}
</script>

<style lang="css">
</style>
