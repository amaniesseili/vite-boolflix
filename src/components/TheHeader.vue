<script>
export default{
  data(){
    return{
      searchQuery: "", 
    };
  },
  methods:{
    onEnter(){
      this.$emit("search",this.searchQuery);

    }
    
  }

};

</script>

<template>
  <header >


    <h1 class="flex-grow-1">BOOLFLIX</h1>
    <div class="input-group mb-3">
      
      <input type="text" class="form-control" 
          v-model="searchQuery"  @keyup.enter="onEnter"             
          placeholder="Search for movie.." aria-label="Search">

      <button class="btn btn-outline-secondary" 
          type="button my-btn" @click="onEnter">Search</button>
    </div>
    
  </header>
</template>


<style lang="scss" scoped>
header{
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 2rem;
  gap: 40rem;
  background-color:black;
  text-align: center;
}

h1{
  color: white;
}



</style>