<template>
  <div>
    <div
      class="modal fade"
      id="createguide"
      tabindex="-1"
      role="dialog"
      aria-labelledby="exampleModalLabel"
      aria-hidden="true"
    >
      <div class="modal-dialog" role="document">
        <div class="modal-content">
          <form>
            <div class="form-group">
              <label for="exampleInputEmail1">Guide title</label>
              <input
              v-model.lazy="title"
                class="form-control"
                id="exampleInputEmail1"
                aria-describedby="emailHelp"
                placeholder="Guide title"
              />
            </div>
            <div class="form-group">
              <label for="exampleInputPassword1">Content</label>
              <textarea
              v-model.lazy="content"
                class="form-control"
                id="exampleInputPassword1"
                placeholder="Content"
              />
            </div>
            <button v-on:click.prevent="create" type="submit" class="btn btn-primary">Submit</button>
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
      title:'',
      content:''
    }
  },
  methods: {
    create(){
      if(this.title!='' && this.content!=''){
        const btn=document.getElementById("createNav");
        btn.click();
        db.collection("guides").add({
          title:this.title,
          content:this.content
        })
        .then(()=>{
          console.error("Guide created");
        })
        .catch(()=>{
          console.error("Guide cannot be created");
        })
      }
    }
  },
}
</script>