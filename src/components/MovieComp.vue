<template>

<div class="container d-flex overflow-auto p-1">
<CardComp v-for="movie in listMovie" :key="movie.id" :title="movie.title" :originalTitle="movie.original_title" :language="movie.original_language" :vote="movie.vote_average" :image='movie.poster_path' :overview="movie.overview"/>

  </div>
</template>

<script>
import CardComp from './CardComp.vue';
export default {
    name: "MovieComp",
    components: { CardComp },
    props:{
      listMovie : Array,
    },
    
}
</script>

<style lang="scss" scoped>
.container{
  height: 400px;
}
::-webkit-scrollbar{
  height: 10px;
}
::-webkit-scrollbar-track {
  background: #f1f1f1;
  border-radius: 20px;
}
::-webkit-scrollbar-thumb {
  background: red;
  border-radius: 20px;
}
</style>