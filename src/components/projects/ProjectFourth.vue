<template lang="html">
  <div class="col-lg-4 col-md-6 col-sm-6 col-12 mb-5">
  <div class="">
    <div class="portfolio_img mb-2">
      <img class="mw-100" src="../../assets/mars.jpg" alt="">
        <div class="description__block">
          <h4 class="text-white font-weight-bold">{{project_4.name}}</h4>
          <span class="down_line mb-2"></span>
          <p class="text-white">{{project_4.description}}</p>
          <a
            href="https://phantom-mars.netlify.com/"
            class="btn btn-sm btn-outline-white font-wheight-bold"
            style="width: 60%; display:block; margin: 0 auto;">
            View
            </a>
        </div>
    </div>
    <div class="row justify-content-center">
      <div v-on:click="editCounter_4">
        <i
          v-bind:style="redCounter_4 ? 'color: red;' : ''"
          class="far fa-heart fa-2x ml-2 mr-2">
        </i>
      </div>
      <p v-bind:style="redCounter_4 ? 'color: red;' : ''">{{likeCounter_4}}</p>
      <div v-on:click="modalFormFourth"><i class="far fa-comment fa-2x ml-2 mr-2"></i></div>
      <p>{{commentsCounter_4}}</p>
      <div v-on:click="linkFourth"><i class="fas fa-link fa-2x ml-2 mr-2"></i></div>

    </div>
    <input
      v-if="link_4"
      class="form-control"
      type="text"
      name="link"
      value="https://phantom-mars.netlify.com/">
  </div>
  <!--end project -5 -->

  <!-- modal comments -->
  <div
    v-if="modal_4"
    class="modal__container pt-5"
  >
    <div class="close_container">
      <i
        class="far fa-times-circle fa-2x"
        v-on:click="modal_4 = false">
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
          @submit.prevent="addComents_4"
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
              {{commentsCounter_4}}
          </span>
        </span>
          <hr  class="col-lg-3 m-auto"/>
        </div>
        <ul class="list-group list_comments" >
          <li
            v-for="(item , index) of comments_list_4"
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
  name: 'projectFourth',
  data () {
    return {
      likeCounter_4: 0,
      redCounter_4: false,
      commentsCounter_4: 0,
      modal_4: false,
      link_4: false,
      comments_list_4: [],
      textComment: null,
      name: null,
      maxLength: false,
      project_4:  {
          id: 4,
          name: 'Phantom - Mars',
          description: 'Макет Лендинга для продажи квадракоптеров',
        },
    }
  },
    created () {
        var self =  this;

        firebase.database().ref('likeCounter_4/').once('value').then(function(snapshot) {
          self.likeCounter_4 = snapshot.val()
        });

        var db = firebase.firestore();
        // Disable deprecated features
        db.settings({
          timestampsInSnapshots: true
        });

        db.collection("comment_list_4").get().then((querySnapshot) => {
            querySnapshot.forEach((doc) => {
              self.comments_list_4.push(doc.data());
            });
          self.commentsCounter_4 =   self.comments_list_4.length
        });
        if (localStorage.getItem('liked_4') === 'true') {
          this.redCounter_4 = true
        } else {
          this.redCounter_4 = false

        }
    },
    methods: {

      linkFourth() {
        this.link_4 = !this.link_4
      },

      editCounter_4 () {
        var newPostKey = firebase.database().ref().child('list_comments_4').push().key;
        firebase.database().ref('likeCounter_4/').set(
            this.likeCounter_4 + 1
          );
        localStorage.setItem('liked_4', 'true')
        this.redCounter_4  = !this.redCounter_4;
        this.redCounter_4 ? this.likeCounter_4++ : this.likeCounter_4-- ;
      },
      modalFormFourth () {
        this.modal_4 = !this.modal_4;
      },
      addComents_4 () {
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
        db.collection("comment_list_4").add(postData)
        .then(function(docRef) {
            console.log("Document written with ID: ", docRef.id);
        })
        .catch(function(error) {
            console.error("Error adding document: ", error);
        });
        this.comments_list_4.push(postData)
        this.commentsCounter_4 ++
        this.name = null
        this.textComment = null
        if (this.comments_list_4.length > 4){
          this.maxLength = true
        }
    },

  },
}
</script>

<style lang="css">
</style>
