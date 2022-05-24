<template>
<div>
    <HeaderComp @myMovie="myMovie" />

    <div v-if="errorLoading" class="bug-container d-flex justify-content-center pt-5">
    <h3 class="text-standard">Che film vuoi vedere?</h3>
    </div>
    <div v-else-if="listMovie.length == 0" class="bug-container d-flex justify-content-center pt-5">
    <h3 class="text-standard">il titolo non è presente nella lista. <span>&#128546;</span></h3>
    </div>

    <div v-else>
    <MainComp :listMovie="listMovie" :listTV="listTV"/>
    </div>
    
  </div>
</template>

<script>
import HeaderComp from './components/HeaderComp.vue';
import MainComp from './components/MainComp.vue';
import axios from 'axios';
export default {
  name: 'App',
  components: {
    HeaderComp,
    MainComp,
},
data(){
    return{
      apiUrl: 'https://api.themoviedb.org/3/search/movie',
      apiUrlTV: 'https://api.themoviedb.org/3/search/tv',
      searchMovie:'',
      oggetto:{
        api_key: '638bdcdb877d0cd78cb521e79825ba13',
        language: 'it-IT',
        query: '',
      },
      listMovie:[],
      listTV:[],
      errorLoading:true,
    }
  },
  methods: {
    getApi(){
      this.oggetto.query = this.searchMovie,
      console.log(this.oggetto);
      axios.get(this.apiUrl, {
      params: this.oggetto
    })
   .then(response => {
          this.listMovie = response.data.results;
          console.log(this.listMovie);
          this.errorLoading = false;
          
        })
   .catch(error => {
          console.log(error);
          this.errorLoading = true;
          
        })
   },
   getApiTV(){
      this.oggetto.query = this.searchMovie,
      console.log(this.oggetto);
      axios.get(this.apiUrlTV, {
      params: this.oggetto
    })
   .then(response => {
          this.listTV = response.data.results;
          console.log(this.listTV);
          this.errorLoading = false;
          
        })
   .catch(error => {
          console.log(error);
          this.errorLoading = true;
          
        })
   },
    myMovie(selectValue){
      this.searchMovie = selectValue;
      console.log(this.searchMovie);
      this.getApi();
      this.getApiTV();
    },
  }
}
</script>

<style lang="scss">
@import './assets/style/general';
#app{
  height: 100vh;
  background-color: black;
}
.bug-container{
  height: calc(100vh - 100px);
  background-color: black;
  color: white;
}
.text-standard{
  text-transform: uppercase;
}
</style>