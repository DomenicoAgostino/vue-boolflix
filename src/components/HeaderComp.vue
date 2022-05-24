<template>
<header class="start-search d-flex justify-content-between align-items-center">
  <div>
    <img src="../assets/img/logo-booflix.png" alt="">
    <button class="btn-movie-tv m-3" @click="movieSelect()">Movie</button>
    <button class="btn-movie-tv m-2" @click="tvSelect()">TV</button>
    </div>
    <div>
      <input type="text" v-model="searchMovie" @keyup.enter="serachMovieMethods()">
      <button class="btn btn-danger m-2" @click="serachMovieMethods()">Cerca</button>
  </div>


</header>
</template>

<script>
export default {
  name: 'HeaderComp',
  data() {
    return {
      searchMovie:'',
      onlyTV: false,
      onlyMovie: false,
    }
  },
  methods: {
    serachMovieMethods(){
      this.$emit( 'myMovie', this.searchMovie );
      this.searchMovie= '';
    },
    movieSelect(){
      this.onlyMovie = true;
      console.log('movie' + this.onlyMovie);
      if(this.onlyTV == true){
        this.onlyTV = false;
        console.log('tv' + this.onlyTV);
      }
    },
    tvSelect(){
      this.onlyTV = true;
      console.log('tv' + this.onlyTV);
      if(this.onlyMovie == true){
        this.onlyMovie = false;
        console.log('movie' + this.onlyMovie);
      }
    },
  },
}
</script>


<style lang="scss" scoped>
.start-search{
  height: 100px;
  
  background: black;
  }
  h1{
    text-transform: uppercase;
    color: red;
  }
</style>
