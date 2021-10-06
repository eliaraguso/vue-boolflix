<template>
  <div id="app">
    <Header @search="searchFilm" />
    <Films :arrayFilms="arrayFilms" />
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
    };
  },

  methods: {
    searchFilm(text) {
      axios
        .get("https://api.themoviedb.org/3/search/movie", {
          params: {
            api_key: "f3ccf82f739dd6e779adfa5f91bae60b",
            query: text,
            language: "it-IT",
          },
        })
        .then((resp) => {
          this.arrayFilms = resp.data.results;
        });
    },
  },
};
</script>

<style lang="scss">
</style>
