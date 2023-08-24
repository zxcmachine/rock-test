<template>
  <div class="wrapper">
    <nav class="navbar navbar-dark bg-dark p-2">
      <input class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search" v-model="searchQuery">
      <button class="btn btn-outline-success my-2 my-sm-0" type="submit">Search</button>
    </nav>
    <div class="cards-container">
      <div class="card text-white bg-dark mb-3" style="width:48%" v-for="post in filteredPosts" :key="post.id">
        <div class="card-header">{{post.name}}</div>
        <div class="card-body">
          <h5 class="card-title">{{post.username}}</h5>
          <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import axios from 'axios'
export default {
  computed: {
    filteredPosts() {
      if (this.searchQuery == '') {
        return this.posts;
      } else {
        return this.posts.filter(post => post.name.toLowerCase().includes(this.searchQuery.toLowerCase()));
      }
    }
  },
  mounted() {
    this.loadPosts();
  },
  data() {
    return {
      posts: [],
      searchQuery: ''
    }
  },
  methods: {
    loadPosts(){
      axios.get('https://jsonplaceholder.typicode.com/users').then((res)=>{
        this.posts = res.data
      })
    }
  },
}
</script>

<style scoped>
.cards-container{
    display: flex;
    flex-wrap: wrap;
    gap: 15px;
    margin-top: 20px;
    justify-content: space-between;
}
.wrapper{
  max-width:1200px;
  margin: 0 auto;
  padding-top:100px;
  padding-bottom:100px;
}
</style>
