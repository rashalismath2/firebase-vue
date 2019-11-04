<template>
  <div>
    <div
      class="modal fade"
      id="signupmodal"
      tabindex="-1"
      role="dialog"
      aria-labelledby="exampleModalLabel"
      aria-hidden="true"
    >
      <div class="modal-dialog" role="document">
        <div class="modal-content">
          <form>
            <div class="form-group">
              <label for="exampleInputEmail1">Email address</label>
              <input
                v-model.lazy="email"
                type="email"
                class="form-control"
                id="email"
                aria-describedby="emailHelp"
                placeholder="Enter email"
              />
              <small
                id="emailHelp"
                class="form-text text-muted"
              >We'll never share your email with anyone else.</small>
            </div>
            <div class="form-group">
              <label for="exampleInputPassword1">Password</label>
              <input
                v-model.lazy="password"
                type="password"
                class="form-control"
                id="password"
                placeholder="Password"
              />
            </div>
            <button v-on:click.prevent="signup" type="submit" class="btn btn-primary">Sign up</button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
/* eslint-disable */
export default {
  data() {
    return {
      email:'',
      password:''

    }
  },
  methods: {
    signup(){
      if(this.email!="" && this.email!=""){
        const btn=document.getElementById("signupnav");
        btn.click();
        auth.createUserWithEmailAndPassword(this.email,this.password)
        .then((cred)=>{
      
        })
        .catch((e)=>{
          console.log("User signup error");
          console.log(e);
        })

      }
    }
  },
}
</script>