<script>
import axios from "axios";
import TheCard from "./TheCard.vue";


export default {
  components:{
    TheCard
  },
  data() {
    return{
      movies:[]
    }
  };
};


</script>

<template>
  <div class="row">
    <div class="col">

      <div class="card text-bg-dark" v-for="movie in movies" :key="movie.id">

        <TheCard :movie="singleMovie in movies" :key="movie.id"> </TheCard>

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