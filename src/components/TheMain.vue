<script>
import axios from "axios";
import TheCard from "./TheCard.vue";
// import { store } from "./scss/store.js";


export default {
  components:{
    TheCard
  },
  data() {
    return{
      // movies:[],
    };
  },
  props:{
    movie: {
      type: Object,
      required:true,
    },

    },
  };
  methods:{
  /* fetchMovies() {
      const url= "https://api.themoviedb.org/3/search/movie?api_key=fb4b225de7e28f7a5413be7fe7f8fd78&query=futuro";

      axios.get(url).then((response)=>{
        this.movies = response.data.results;
        console.log(this.movies)
      });
    },
  },
  mounted() {
    this.fetchMovies();
  },*/



};


</script>

<template>
  <div class="row">
    <div class="col">

      <div class="card text-bg-dark" v-for="movie in movies" :key="movie.id">

        <img :src="movie.poster_path" class="card-img" alt="...">

        <div class="card-img-overlay">
          <h5 class="card-title">{{ movie.title }}</h5>
          <h5 class="card-original-title">{{ movie.original_title }}</h5>
          <!-- Rating v-for=??"-->
          <h5 class="card-rating">{{ movie.vote_average }}</h5>

          <p class="card-overview"><small>{{ movie.overview}}</small></p>
        </div>

        <!-- prova
        <ul>
          <li v-for="movie in movies" :key="movie.id">{{ movie.title }}</li>
        </ul> -->


        <!-- <img src="..." class="card-img" alt="...">
        <div class="card-img-overlay">
          <h5 class="card-title">Card title</h5>
          <p class="card-text">This is a wider card with supporting text below as a natural lead-in to additional content. This content is a little bit longer.</p>
          <p class="card-text"><small>Last updated 3 mins ago</small></p>
        </div> -->

      </div>
    </div>
  </div>



</template>


<style lang="scss" scoped>

</style>