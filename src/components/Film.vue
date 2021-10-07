<template>
  <ul>
    
    
    <li>Titolo: {{film.title || film.name}}</li>

    <li>Titolo originale: {{film.original_title || film.original_name}}</li>

    <li>Lingua:<country-flag :country="(film.original_language == 'en') ? 'us' : film.original_language"/></li>
    <li>Voto: {{ film.vote_average }}</li>
    <li>Voto: {{starsQuantity(vote)}}</li>

    <li v-if="linkPoster != null">A<img :src="'https://image.tmdb.org/t/p/w300' + linkPoster" alt=""></li>
    <li v-else>B<img src="https://www.fiaddaemiliaromagna.org/wp-content/uploads/2020/04/lavori-in-corso.jpeg" alt=""></li>


  </ul>
</template>

<script>
export default {
  
  name: "Film",


  props: {
    film: Object,
  },

  data() {
    return {
      vote: Math.ceil(this.film.vote_average / 2),
      linkPoster: this.film.poster_path,
    }
  },

  methods: {
    starsQuantity(vote) {
      vote = this.vote
      return vote
    }
  },

};
</script>

<style>
</style>