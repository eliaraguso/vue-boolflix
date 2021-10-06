<template>
  <ul>
    <li v-if="film.title">Titolo: {{ film.title }}</li>
    <li v-else>Titolo: {{film.name}}</li>

    <li v-if="film.original_title">Titolo originale: {{ film.original_title }}</li>
    <li v-else>Titolo originale: {{film.original_name}}</li>


    <li>Lingua:<country-flag :country="(film.original_language == 'en') ? 'us' : film.original_language"/></li>
    <li>Voto: {{ film.vote_average }}</li>
    <li><img :src="'https://image.tmdb.org/t/p/w300' + film.poster_path" alt=""></li>

  </ul>
</template>

<script>
export default {
  name: "Film",

  props: {
    film: Object,
  },
};
</script>

<style>
</style>