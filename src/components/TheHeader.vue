<script>
export default{
  name:"TheHeader"


};

</script>

<template>
  <header >

    <h1 class="flex-grow-1">BOOLFLIX</h1>
    <div class="input-group mb-3">
      <input type="text" class="form-control" placeholder="Search for movie.." aria-label="Search">
      <button class="btn btn-outline-secondary" type="button" id="button-addon2">Search</button>
    </div>
    
  </header>





</template>


<style lang="scss" scoped>
header{
  display: flex;
  align-items: center;
  padding: 4rem;
  gap: 3rem;

}


</style>