<template>
  <div class="row">
    <div class="col-8">
      <instagram-card
        v-for="card in filteredCards"
        :key="card.url"
        :info="card"
      />
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
        <!-- {{ store.isThatTrue }} -->
      </div>
    </div>
  </div>
</template>
<script>
// @ is an alias to /src
import InstagramCard from "@/components/InstagramCard.vue";
import store from "@/store.js";

export default {
  name: "home",
  data() {
    return {
      store,
    };
  },
  imePrezime() {},
  computed: {
    filteredCards() {
      return this.store.cards.filter(
        (card) =>
          card.title.includes(store.searchTerm) ||
          card.author.includes(store.searchTerm)
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
</style>