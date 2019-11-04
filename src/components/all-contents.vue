<template>
  <div class="col-6 mt-3 mr-auto  ml-auto">
    <div v-if="guides.length>0" class="accordion" id="accordionExample">
      <div v-for="guide in guides" v-bind:key="guide.id" class="card">
        <div class="card-header" id="headingOne">
          <h2 class="mb-0">
            <button
              class="btn btn-link"
              type="button"
              data-toggle="collapse"
              data-target="#collapseOne"
              aria-expanded="true"
              aria-controls="collapseOne"
            >{{guide.data().title}}</button>
          </h2>
        </div>

        <div
          id="collapseOne"
          class="collapse "
          aria-labelledby="headingOne"
          data-parent="#accordionExample"
        >
          <div
            class="card-body"
          >{{guide.data().content}}</div>
        </div>
      </div>
    </div>
    <div v-else>
      <p>logged in to see posts</p>
    </div>
  </div>
</template>
<script>
/* eslint-disable */
export default {
  props:{
    guides:{
      type:Array,
      required:true
    }
  },
  data() {
    return {
 
    }
  }
}
</script>