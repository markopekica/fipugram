<template>
  <div class="about">
    <h1>This is a signup page</h1>

    <div class="row">
      <div class="col-2"></div>
      <div class="col-8">
        <div v-if="greska" style="color:red;">
          Watch out <br> {{ greska }}
        </div>
        <form>
          <div class="form-group">
            <label for="exampleInputEmail1">Email address</label>
            <input
              type="email"
              v-model="username"
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
          <div class="form-group">
            <label for="exampleInputPassword2">Repeat Password</label>
            <input
              type="password"
              v-model="passwordRepeat"
              class="form-control"
              id="exampleInputPassword2"
              placeholder="Password"
            />
          </div>
          <button type="button" @click="signup" class="btn btn-primary">
            Submit
          </button>
        </form>
      </div>
      <div class="col"></div>
    </div>
  </div>
</template>


<script>
import { firebase } from "@/firebase";
export default {
  name: "Signup",
  data() {
    return {
      username: "",
      password: "",
      passwordRepeat: "",
      greska: this.err
    };
  },
  props: {
  },
  methods: {
    signup() {
      /* this.username="phuc" */
      if(this.password == this.passwordRepeat /* && this.password != '' */ ){
        firebase
          .auth()
          .createUserWithEmailAndPassword(this.username, this.password)
          .then( () => {console.log("f yes")} )
          .catch( (error) => {
            console.error("Falia si: ", error)
            this.greska = error.message
          })
      } else {
        console.log('ni isto')
      }
    },
  },
};
</script>


<style lang="scss">
form{
  max-width: 400px;
  margin: auto;
}
</style>