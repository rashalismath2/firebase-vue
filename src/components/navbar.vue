<template>
  <div>
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
      <a class="navbar-brand" href="#">
        <img src="../assets/logo.png" width="30" height="30" class="d-inline-block align-top" alt />
      </a>
      <button
        class="navbar-toggler"
        type="button"
        data-toggle="collapse"
        data-target="#navbarNav"
        aria-controls="navbarNav"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav">
          <li v-if="userStatus" class="nav-item active">
            <a class="nav-link" data-toggle="modal" data-target="#accountmodal" href="#">Account</a>
          </li>
          <li v-if="userStatus" class="nav-item">
            <a v-on:click="logout" class="nav-link" href="#">Logout</a>
          </li>
          <li v-if="userStatus" class="nav-item">
            <a id="createNav" class="nav-link" data-target="#createguide" data-toggle="modal" href="#">Create Guide</a>
          </li>
          <li v-if="!userStatus" class="nav-item">
            <a
              id="btnLoginNav"
              class="nav-link"
              data-toggle="modal"
              data-target="#loginmodal"
              href="#"
            >Login</a>
          </li>
          <li v-if="!userStatus" class="nav-item">
            <a
              class="nav-link"
              id="signupnav"
              href="#"
              data-toggle="modal"
              data-target="#signupmodal"
            >Sign up</a>
          </li>
        </ul>
      </div>
    </nav>
    <signupmodal></signupmodal>
    <loginmodal></loginmodal>
    <accountmodal></accountmodal>
    <createguide></createguide>
  </div>
</template>

<script>
/* eslint-disable */
import signupmodal from "./signup-modal.vue";
import loginmodal from "./login-modal.vue";
import createguide from "./createContent-modal.vue";
import accountmodal from "./account-modal.vue";
export default {
  props: {
    userStatus: {
      type: Boolean,
      required: true
    }
  },
  components: {
    signupmodal: signupmodal,
    accountmodal: accountmodal,
    createguide: createguide,
    loginmodal: loginmodal
  },
  methods: {
    logout() {
      auth
        .signOut()
        .then(() => {
          console.error("User logged out");
          this.$emit("userLoggedOut", true);
        })
        .catch(() => {
          console.error("User logged out error");
        });
    }
  }
};
</script>