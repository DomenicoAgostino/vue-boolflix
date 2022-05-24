<template>
<div class="card overflow-hidden">
 <div class="smv-card">
    <div class="flip-card-principal">
      <div class="flip-card-front">
        <img :src="`${urlImg}${image}`" alt="">

      </div>
      <div class="flip-card-back">
        <h4>{{ title }}</h4>
        <p>Titolo: {{ originalTitle }}</p>

        <div v-if="language == 'en'"><img class="b-lng" src="../assets/img/eng-lng.png" alt=""></div>
        <div v-else-if="language == 'it'"><img class="b-lng" src="../assets/img/it-lng.png" alt=""></div>
        <p v-else>Lingua: {{language}}</p>
        <p>&starf;{{ vote }}</p>
        <p class="overview">{{overview}}</p>


        <div>
          <span v-for="n in 5" :key="n">
          <span v-if="voto >= n">&starf;</span>
          <span v-else>&star;</span>
          </span>
        </div>
        <p class="overview">{{overview}}</p>
      </div>
    </div>
  </div> 
</div>
</template>

<script>
export default {
  name: 'CardComp',
  data(){
    return{
      urlImg: 'https://image.tmdb.org/t/p/w300',
      voto: Math.round(this.vote / 2)
    }
  },
  props:{
      title : String,
      originalTitle: String,
      language: String,
      vote: Number,
      image: String,
      overview: String,
    },
}
</script>

<style lang="scss" scoped>
@import '../assets/style/vars';
.card{
  min-width: 250px;
  max-height: 100%;
  margin: 7px;
  border: none;
  background-color: black;
}
smv-card{
  width: 100%;
  height: 100%;
  img{
    width: 100%;
    height: 100%;
  }
  h4{
    color: white;
  }
  p{
    color: gray;
    font-size: 12px;
    overflow-y:auto;
  }
}

    span{
    color: red;
  }

.flip-card-principal {
  position: relative;
  min-width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.4s;
  transform-style: preserve-3d;
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  background-color: black;
}
.smv-card:hover .flip-card-principal {
  transform: rotateY(180deg);
  background-color: black;
}
.flip-card-front, .flip-card-back {
  position: absolute;
  width: 100%;
  backface-visibility: hidden;
  background-color: black;
}
.flip-card-back {
  transform: rotateY(180deg);
  background-color: black;
  h4{
    color: white;
    text-transform: uppercase;
  }
  p{
    color: white;
    font-size: 20px;
    font-weight: 500;
  }

  .b-lng{
    height: 20px;
  }
}
</style> 