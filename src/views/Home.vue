<template>
  <div class="row">
    <div class="col-0"></div>
    <div class="col-8">
      <div class="post-new-div">
        <form
          id="new-post-form"
          @submit.prevent="postNewImage"
          class="form-inline mb-5"
        >
          <div class="form-group">
            <label for="imageUrl">Image URL</label>
            <input
              v-model="newImageUrl"
              type="text"
              class="form-control ml-2"
              placeholder="Enter the image URL"
              id="imageUrl"
            />
          </div>
          <div class="form-group">
            <label for="imageDescription">Description</label>
            <input
              v-model="newImageDescription"
              type="text"
              class="form-control ml-2"
              placeholder="Enter the image description"
              id="imageDescription"
            />
          </div>
          <button type="submit" class="btn btn-primary ml-2">Post image</button>
        </form>
        <div class="success-message" v-if="successMsg">
          {{ successMsg }}
        </div>
      </div>

      <instagram-card
        v-for="card in filteredCards"
        :key="card.id"
        :info="card"
      />
      <!--
      zašto, ali zašto pomišljam na grozote;
      i onda odjednom promjenim
      info=cards
      u
      info=card
      i stvar proradi...
      -->
    </div>
    <div class="col-4">
      Sidebar
      <br /><br />
      <div class="imeprez">
        <label for="name">Name:</label>
        <input
          v-model="store.ime"
          type="text"
          id="name"
          name="name"
          required
          size="10"
          value="1"
        />
        <br />
        <label for="lastName">Last name:</label>
        <input
          v-model="store.prezime"
          type="text"
          id="last-name"
          name="lastName"
          required
          size="10"
        />
      </div>
      <div style="margin-top: 1em">
        {{ store.ime + " " + store.prezime }}
      </div>
    </div>
  </div>
</template>
<script>
// @ is an alias to /src
import InstagramCard from "@/components/InstagramCard.vue";
import store from "@/store.js";
import { db } from "@/firebase";

export default {
  name: "home",
  data() {
    return {
      store,
      cards: [],
      newImageDescription: null,
      newImageUrl: null,
      successMsg: "",
    };
  },
  mounted() {
    this.getPosts();
  },
  methods: {
    getPosts() {
      console.log("dohvat iz baze");
      db.collection("posts")
        .orderBy('posted_at', 'desc')
        .limit(10)
        .get()
        .then((query) => {
          this.cards = []
          query.forEach((doc) => {
            const data = doc.data();

            this.cards.push({
              id: doc.id,
              time: data.posted_at,
              description: data.desc,
              url: data.url
            });
          });
        });
    },
    postNewImage() {
      const imageUrl = this.newImageUrl;
      const imageDescription = this.newImageDescription;

      //collection = u koju tablicu spremam
      if (imageUrl && imageDescription) {
        db.collection("posts")
          .add({
            url: imageUrl,
            desc: imageDescription,
            email: store.currentUser,
            posted_at: Date.now(),
          })
          .then((doc) => {
            console.log("spremljeno", doc);
            this.newImageDescription = "";
            this.newImageUrl = "";
            this.successMsg = "Your post is saved";

            this.getPosts() //update when new post added

            setTimeout(() => {
              this.successMsg = "";
            }, 3000);
          })
          .catch((e) => {
            console.log(e);
          });
      } else {
        this.successMsg = "Please fill in the fields";
        setTimeout(() => {
          this.successMsg = "";
        }, 3000);
      }
    },
  },
  computed: {
    filteredCards() {
      return this.cards.filter(
        (card) =>
          card.description.includes(store.searchTerm) /* ||
          card.author.includes(store.searchTerm) */
      );
    },
  },
  components: {
    InstagramCard,
  },
};
</script>


<style lang="scss" scoped>
.imeprez {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 1em auto;
}
#new-post-form {
  margin: 1em auto 0 auto;
  display: flex;
  flex-direction: column;
  /* border: 1px solid red; */
}
.form-group {
  margin: 0.5em auto;
}
.success-message {
  margin: -2em auto 2em auto;
  /* color: green; */
}
</style>