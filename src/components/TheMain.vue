<script>
import axios from "axios";
import TheCard from "./TheCard.vue";
import TheMain from "./TheMain.vue";
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
    movies: {
      type: Object,
      required:true,
    },

    },
    methods:{
    //--------- per avere la bandiera faccio la funzione getCountryflag-------------------
    getCountryFlag(language){
      const languageToCountry ={
        en:"us"
      };
      const countryCode = languageToCountry[language] ;
      return`https://flagsapi.com/BE/flat/64.png`;
      // return`https://flagsapi.com/${langFlat.toUperCase()}/flat/64.png`;
    },
    
    //---------------------------------------------------------------------------------
  },
  };

</script>

<template>
  <div class="row row-cols-4">
    <div class="col mt-3"  v-for="movie in movies" :key="movie.id">

      <div class="card text-bg-dark">

        <img :src="movie.poster_path" class="card-img " alt="...">

        <div class="card-img-overlay">
          <h5 class="card-title">{{ movie.title }}</h5>
          <!-- ---------------------------------------------------- -->
          <!-- aggiungo un div per mostrare la bandiera del paese -->
          <div>
            <img :src="getCountryFlag(movie.original-language)" alt="country-flag">
            {{ movie.original_language }}
          </div>
          <!-- ---------------------------------------------------- -->
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
.card{
  min-height: 400px;
  margin-bottom: 1rem;
  border-radius: 0;
}

</style>