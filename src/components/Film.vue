<template>
  <ul>
    <li>Titolo: {{ film.title }}{{film.name}}</li>
    <li>Titolo originale: {{ film.original_title }}{{film.original_name}}</li>
    <li>Lingua:<country-flag :country="(film.original_language == 'en') ? 'us' : film.original_language"/></li>
    <li>Voto: {{ film.vote_average }}</li>

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