<script>
import axios from "axios";
import TheHeader from './components/TheHeader.vue';
import TheMain from './components/TheMain.vue';

//per allargare la ricerca anche alle serie TV, creo una variabile per determinare se sto cercando film o serieTV. E poi faccio la funzione per scaricare i dati



export default {
  components:{
    TheHeader,
    TheMain
  },

  data() {
    return{
      api_key: "fb4b225de7e28f7a5413be7fe7f8fd78",
      query:"",
      movies:[], 
      mediaType:"tv",
      showIntro :true   

    };
  },
  methods:{      
    //------------------creao una funzione per scaricare i dati movie
    fetchMovies (searchQuery) {

      axios.get("https://api.themoviedb.org/3/search/movie",{
        params:{
          api_key: this.api_key,
          query: searchQuery,
        },
      })
      .then((response)=>{
        this.movies = response.data.results;
        this.showIntro =this.movies.length === 0;
        console.log(this.movies)
      })
      .then(error=>{
        console.log("errore durante la chiamata API:", error);
      });

    },
    //--------------funzione per le serie tv-------------------
    fetchMediaType (searchQuery){
      axios.get("https://api.themoviedb.org/3/search/tv",{
        params:{
          api_key: this.api_key,
          query: searchQuery,
        },
      })
        .then((response)=>{
        this.mediaType = response.data.results;
        console.log(this.movies)
      })
      .then(error=>{
        console.log("errore durante il recupero dei media:", error);
    })
  }
  },

  //-------------------------------------------------------------
  mounted(){
    this.fetchMovies();
  },
};
</script>

<template>

  <TheHeader @search="fetchMovies"></TheHeader>

  <main>
    <!----------------- presentation intro-------------- -->
    <div class="intro" v-if="showIntro" >
      <div class="row">
        <div class="col-3 ms-5 me-5 description">
          <h3>Boolflix</h3>
          <p>Scopri mondi incantanti e avventure e avventure senza fine con BoolFlix: dove ogni schermo è una finestra verso l'infinito.Dalle epiche avventure alle scoperte segrete, preparati a immergerti nel magico mondo Del cinema come mai prima d'ora!</p>
        </div>
        <div class="col-3 slogan">
          <h1 class="title-slogan"><b>OLTRE LO <br> SCHERMO </b></h1>

        </div>
      </div>
    </div>
    <!-- ------------------------------------------------ -->        
    <div class="container mt-2">

      <TheMain :movies="movies"></TheMain>

    </div>

  </main>



</template>

<style >

.intro{
  width: 100%;
  height: calc(100wh - 100px);
  font-family: Arial, Helvetica, sans-serif;
  background-image: url(../public/boolflix-bg-2.jpg);
  background-size:cover;
  background-repeat: no-repeat;
  background-position: center;
} 

.slogan{
  margin-top: 600px;

}
  
.title-slogan{
  font-size: 60px;
}
.description{
  margin-top: 150px;
  
}


</style>
