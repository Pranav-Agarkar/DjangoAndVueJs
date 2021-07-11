<template lang="html">
  <div class="posts">
    <Navbar></Navbar>
    <div class="album py-5 bg-light">
      <div class="container">
        <div class="row">
          <div v-for="posts in APIData" :key="posts.id" class="col-md-4">
            <div class="card mb-4 box-shadow">
              <img src="https://via.placeholder.com/150x100" alt="Card image cap" class="card-img-top">
              <div class="card-body">
                <h4> <a href="" class="text-secondary"></a> {{posts.title}} </h4>
                <p class="card-text">{{posts.content}}</p>
                <div class="d-flex justify-content-between align-items-center">
                  <div class="btn-group">
                    <a href="#" class="btn btn-sm btn-outline-primary">View</a>
                    <a href="#" class="btn btn-sm btn-outline-secondary">Edit</a>
                  </div>
                  <small class="text-muted">9 mins</small>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Navbar from '../components/Navbar.vue'
import {getAPI} from '../axios-api'

export default {
  name: 'Posts',

  data(){
    return{
      APIData: [],
    }
  },

  components:{
    Navbar
  },

  created(){
    getAPI.get('/posts/',)
      .then(response => {
        console.log('Post API has recived data')
        this.APIData = response.data
      })
      .catch(err => {
        console.log(err);
      })
  }

}
</script>

<style lang="css" scoped>
*{
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
</style>
