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
    
    };
  },
  props:{
    movies: {
      type: Object,
      required:true,
    },

    },
    methods:{
    //--------- 1- per avere la bandiera faccio la funzione getCountryflag-------------------
    getCountryFlag(language){
      const languageToCountry ={
        en:"us"
      };
      const countryCode = languageToCountry[language] ;
      return`https://flagsapi.com/BE/flat/64.png`;
      // return`https://flagsapi.com/${langFlat.toUperCase()}/flat/64.png`;
    },
    
    //---------------------------------------------------------------------------------
    //-------- 3-per convertire il voto in stelle -> funzione per calcolare il num delle stelle -> template
    getStarRaiting(voteAverage){
      const rating = Math.ceil(voteAverage / 2);  // per trasformare a scala 1-5
      return rating; 
    }
    //----------------------------------------------------------------------------------------
  },
   //------- 6- per aggiungere la cpertina del film faccio una funzione getFullImagePath---
    /*getFullImagePath(posterPath){
      
      return `https://image.tmdb.org/t/p/w342/s2al5ubCNoMud9hLA80KL1qQdxB.jpg`;
    },*/
    //---------------------------------------------------------------------------------
  };

</script>

<template>



  <div class="row row-cols-4">
    <div class="col mt-3"  v-for="movie in movies" :key="movie.id">

      <div class="card text-bg-dark">

        

        <div class="card-img-overlay">
          
          <!-- <img :src="getFullImagePath (movie.poster_path)" class="card-img " alt="movie poster">   -->

          <img :src="movie.poster_path" class="card-img " alt="..."> 

          <h5 class="card-title">{{ movie.title }}</h5>
          <!-- ---------------------------------------------------- -->
          <!----  2-  aggiungo un div per mostrare la bandiera del paese -------- -->
          <div>
            <img class="flag" :src="getCountryFlag(movie.original-language)" alt="country-flag">
            {{ movie.original_language }}
          </div>
          <!-- ---------------------------------------------------- -->
          <!--  4- uso la funzione getStarRating permostrare le stelle  Rating  -------------------------------->
          <span class="card-rating star-icon" v-for="star in getStarRaiting(movie.vote_average)" :key="star"><i class="fa-solid fa-star"> * </i></span>

          <!-- ------------------------------------------------- -->
          <!-- <h5 class="card-rating" v-for="star in getStarRaiting(movie.vote_average)" :key="star">{{ movie.vote_average }}</h5> -->

          <p class="card-overview"><small>{{ movie.overview}}</small></p>
        </div>

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
.flag{
  height: 30px;
}

.fa-star{
  font-size: 2rem;
  color: yellow;
}
.card-title{
  font-weight: bold;
  margin-bottom: 0.5rem;
}

</style>