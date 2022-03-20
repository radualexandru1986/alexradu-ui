<template>
  <div class="container">
    <div class="row">
      <div class="col-12 col-lg-6">
        <h1 class="display-2 text-center text-xl-start"> Tweets </h1>
      </div>
      <div class="col-12 col-lg-6">
        <div class="form-group h-100 d-flex justify-content-center align-items-center">
          <input type="text"
                 v-model="searchTerm"
                 class="form-control border-2 border-dark form-control-lg text-center text-xl-start"
                 placeholder="Search in tweets">
        </div>
      </div>
    </div>

    <hr>
    <p class="text-muted text-center text-xl-start w-100"> @FarrowsDesign - Last 20 tweets </p>
    <p class="text-muted text-center text-xl-start w-100" v-if="searchTerm">Matching results : {{this.tweets.length}}</p>
    <div class="row mt-5 p-1">
      <CardComponent v-for="(tweet, index) in tweets" v-bind:key=index v-bind:details = tweet> </CardComponent>
    </div>
  </div>

</template>

<script>
import CardComponent from './components/Card';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    CardComponent
  },
  data(){
    return {
      serverResponse:[],
      searchTerm:'',

    }
  },
  methods:{

  },
  computed :{
    tweets(){
      return this.serverResponse.filter(tweet=>{
          return tweet.text.toLowerCase().match(this.searchTerm.toLowerCase())
        })
    }
  },
  mounted() {
    axios.get('https://backend.alexradu.co.uk/api/tweets').then(response=>{
      console.log(response.data)
      this.serverResponse = response.data
    })
  }
}
</script>

<style>
@import '~bootstrap/dist/css/bootstrap.css';
</style>
