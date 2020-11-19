<template>
  <div id="app">
    <nav id="nav" class="navbar navbar-expand-lg navbar-light">
      <a class="logo-span navbar-brand" href="#">
        <img src="@/assets/insta.png" height="30" alt="" />
      </a>
      <button
        class="navbar-toggler"
        type="button"
        data-toggle="collapse"
        data-target="#navbarToggler"
        aria-controls="navbarToggler"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>

      <div class="collapse navbar-collapse" id="navbarToggler">
        <ul class="navbar-nav mr-auto mt-2 mt-lg-0">
          <li class="nav-item">
            <router-link class="nav-link" to="/home">Home</router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link" to="/login">Login</router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link" to="/signup">Signup</router-link>
          </li>
        </ul>
        <form class="form-inline my-2 my-lg-0">
          <input
            class="form-control mr-sm-2"
            type="search"
            placeholder="Search"
            aria-label="Search"
          />
        </form>
      </div>
    </nav>

    <router-view />

    <div id="footer" class="text-center mt-5">
      Ovo je footer. (c) 2019 mi svi skupa.
    </div>
  </div>
</template>


<script>
import store from "@/store.js";

export default {
  data() {
    return store;
  },

  methods: {
    logout() {
      store.authenticated = false;
    },
  },
};
</script>


<style lang="scss">
.logo-span {
  display: flex;
  align-items: center;
  margin: 0 1em;
}
.container {
  max-width: 100vw;
  padding: 0;
}
.row {
  max-width: 100vw;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  min-width: 100vw;
  max-width: 100vw;
}
#nav {
  padding: 30px; 

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
