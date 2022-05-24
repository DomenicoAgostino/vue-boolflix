<template>
  <div class="container d-flex overflow-auto p">
<CardComp v-for="( movie, index ) in listTV" :key="index" :title="movie.name" :originalTitle="movie.name" :language="movie.original_language" :vote="movie.vote_average" :image='movie.poster_path' :overview="movie.overview"/>  </div>
</template>

<script>
import CardComp from "./CardComp.vue";
export default {
    name: "SeriesComp",
    components: { CardComp },
    props: {
      listTv: Array,
    }
}
</script>

<style lang="scss" scoped>
</style> 