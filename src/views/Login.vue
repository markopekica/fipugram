<template>
  <div class="about">
    <h1>This is a login page</h1>

    <div class="row">
      <div class="col-2"></div>
      <div class="col-8">
        <div style="color:red; margin:1em auto;">{{ err }}</div>
        <form>
          <div class="form-group">
            <label for="exampleInputEmail1">Email address</label>
            <input
              type="email"
              v-model="email"
              class="form-control"
              id="exampleInputEmail1"
              aria-describedby="emailHelp"
              placeholder="Enter email"
            />
            <small id="emailHelp" class="form-text text-muted">
              We'll never share your email with anyone else.
            </small>
          </div>
          <div class="form-group">
            <label for="exampleInputPassword1">Password</label>
            <input
              type="password"
              v-model="password"
              class="form-control"
              id="exampleInputPassword1"
              placeholder="Password"
            />
          </div>
          <button type="button" @click="login()" class="btn btn-primary">Submit</button>
        </form>
      </div>
      <div class="col"></div>
    </div>
  </div>
</template>

<script>
import { firebase } from "@/firebase";
export default {
  name: "login",
  data() {
    return {
      email: "",
      password: "",
      err: ""
    }
  },
  methods: {
    login() {
      console.log("login... " + this.email)
      firebase
        .auth()
        .signInWithEmailAndPassword(this.email,  this.password)
        .then( (result) => {
          console.log("uspjesna prijava", result)
          /* this.$router.replace({name:"home"}) */
        })
        .catch( (e) => {
          console.error("greska", e);
          this.err = e;
        })
    }
  }
}
</script>

<style lang="scss">
form{
  max-width: 400px;
  margin: auto;
}
</style>