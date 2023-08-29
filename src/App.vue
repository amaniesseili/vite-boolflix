<script>
import axios from "axios";
import TheHeader from './components/TheHeader.vue';
import TheMain from './components/TheMain.vue';


export default {
  components:{
    TheHeader,
    TheMain
  },

  data() {
    return{
      // movies:[]//forse da cancellare 
      //////////////////////////////////
      api_key: "fb4b225de7e28f7a5413be7fe7f8fd78",
      query:"",

    };
  },
  methods:{                                                         //creao una funzione per scaricare i dati
    fetchMovies (searchQuery) {

      axios.get("https://api.themoviedb.org/3/search/movie",{
        params:{
          api_key: this.api_key,
          query: this.searchQuery,
        },
      })
      .then((reso)=>{})
      .then(err=>{});

    }

  },
  mounted(){
    this.fetchMovies();
  }


}
</script>

<template>

  <TheHeader @search="fetchMovies"></TheHeader>

  <main>
    <div class="container">

      <TheMain></TheMain>

    </div>

  </main>

</template>

<style >

</style>
