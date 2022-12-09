<template>
<div class="container">
  <div class="card" v-if="comments">
      <h2>Комментарии</h2>
      <ul class="list">
        <li class="list-item" :key="comment" v-for="comment in comments">
          <div >
            <p><strong> {{ comment.email }}</strong></p>
            <small>{{ comment.body }}</small>
          </div>
        </li>
      </ul>
    </div>
    <div v-else>
      <button class="btn primary" @click="loadComments">
        Загрузить комментарии
      </button>
    </div>
      
      <app-loader v-if="loading"></app-loader>
</div>
</template>

<script>
import axios from "axios"
import AppLoader from "./AppLoader"

export default {
    data () {
      return {
      comments: "",
      loading: false,
      }
    },

    methods: {
      loadComments() {

      this.loading=true

     axios.get('https://jsonplaceholder.typicode.com/comments?_limit=42').then((response) => {
        this.comments = Object.keys(response.data).map((key) => {
          return {
            email: response.data[key].email,
            body: response.data[key].body,
          }
        })  
        this.loading=false})
      
     
    },

    },
    components: {AppLoader}

}
</script>

<style>

</style>