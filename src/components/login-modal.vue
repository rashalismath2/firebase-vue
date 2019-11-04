<template>
  <div>
    <div
      class="modal fade"
      id="loginmodal"
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
                id="exampleInputEmail1"
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
                id="exampleInputPassword1"
                placeholder="Password"
              />
            </div>
            <button v-on:click.prevent="login" type="submit" class="btn btn-primary">Login</button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email:'',
      password:''
    }
  },
  methods: {
    login(){ 
      if(this.email!='',this.password!=''){
        const btn=document.getElementById("btnLoginNav");
        btn.click();
        auth.signInWithEmailAndPassword(this.email,this.password)
        .then((user)=>{
            
        })
        .catch((e)=>{
          console.error("Sign in error ",e);
        })
      }
    }
  },
}
</script>