<template>
  <div class="login">

    <h1>Login</h1>
    <br>
    <!-- hehe -->
    <!-- https://getbootstrap.com/docs/4.0/layout/grid/ -->
    <!-- https://getbootstrap.com/docs/4.0/components/forms/ -->
    <div class="container">
      <div class="row">
        <div class="col-sm" style="color:snow;">
          One
        </div>
        <div class="col-sm" style="min-width:fit-content;">
          <form style="margin:2em;">
            <div class="form-group">
              <label for="exampleInputEmail1">Email address</label>
              <input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" placeholder="Enter email" required>
              <!-- <small id="emailHelp" class="form-text text-muted">We'll never share your email with anyone else, but someone else might.</small> -->
            </div>
            <div class="form-group">
              <label for="exampleInputPassword1">Password</label>
              <input type="password" class="form-control" id="exampleInputPassword1" placeholder="Password" required>
            </div>
            <button type="submit" class="btn btn-primary">Submit</button>
          </form>
        </div>
        <div class="col-sm" style="color:snow;">
          of three
        </div>
      </div>



      <br><br><br><br>
      <div class="row" style="margin-bottom:2em; opacity:.6;">
        <div class="col-sm">
      <hr>
          <h4>Don't have an account yet? Make one right now, <a href="/Signup.vue">here</a>.</h4>
        </div>
      </div>
    </div>

    

    <!-- <div style="min-height: 50vh;"></div>
    <hr style="width:80%;">

    <div class="container">
      <h1>Primjer kako to moze izgledat</h1>
      <div class="row">
        <div class="col-sm"></div>
        <div class="col-sm">
          <form>
            <div class="form-group">
              <label for="exampleInputEmail1">Email address</label>
              <input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" placeholder="Enteremail" />
              <small id="emailHelp" class="form-text text-muted" >We'll never share your email with anyone else.</small>
            </div>
            <div class="form-group">
              <label for="exampleInputPassword1">Password</label>
              <input type="password" class="form-control" id="exampleInputPassword1" placeholder="Password" />
            </div>
            <button type="submit" class="btn btn-primary">Submit</button>
          </form>
        </div>
        <div class="col-sm"></div>
      </div>
    </div> -->

  </div>

</template>
