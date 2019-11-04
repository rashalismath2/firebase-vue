<template>
  <div id="app">
    <navbar v-bind:userStatus="userLoggedIn" v-on:userLoggedOut="clear($event)"></navbar>
    <allcontent v-bind:guides="guides"></allcontent>
  </div>
</template>

<script>
import navbar from "./components/navbar.vue"
import allcontent from "./components/all-contents.vue"
export default {
  name: 'App',
  components:{
    navbar: navbar,
    allcontent: allcontent
  },
  methods: {
    
  },
  data() {
    return {
      guides:[],
      userLoggedIn:false
    }
  },
  created() {
    auth.onAuthStateChanged((user)=>{
      if(user){
        this.userLoggedIn=true;
        console.error("user present");
            db.collection("guides").get()
              .then((doc)=>{
                this.guides=doc.docs
              })
            .catch((e)=>{
                console.error("Getting data error");
            })
      }else{
        this.userLoggedIn=false;
        this.guides=[]
        console.error("User logged out");
      }
    }),


    db.collection("guides")
      .onSnapshot((snapshot)=>{
        console.error("snap ",snapshot);
        let changes=snapshot.docChanges();
        changes.forEach(element => {
          if(element.type=="added"){
            this.guides.unshift(element.doc);
          }
        });
      })

  },
  methods: {
    clear(data){
      this.guides=[]
    }
  },
}
</script>

<style>
</style>
