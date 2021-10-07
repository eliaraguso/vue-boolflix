<template>
  <div id="app">
    <Header @search="searchFilm" />
    <Films :arrayFilms="arrayFilms" :arraySeries="arraySeries" />
  </div>
</template>

<script>
import axios from "axios";
import Header from "./components/Header.vue";
import Films from "./components/Films.vue";

export default {
  name: "App",

  components: {
    Header,
    Films,
  },
  data() {
    return {
      arrayFilms: [],
      arraySeries: [],
    };
  },

  methods: {
    searchFilm(text) {
      const params = {
        api_key: "f3ccf82f739dd6e779adfa5f91bae60b",
        query: text,
        language: "it-IT",
      };
      axios
        .get("https://api.themoviedb.org/3/search/movie", {
          params: params,
        })
        .then((resp) => {
          this.arrayFilms = resp.data.results;
        });
      axios
        .get("https://api.themoviedb.org/3/search/tv", {
          params: params,
        })
        .then((resp) => {
          this.arraySeries = resp.data.results;
        });
    },
  },
};
</script>

<style lang="scss">
</style>
