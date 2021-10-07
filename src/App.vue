<template>
  <div id="app">
    <header>
      <Header @search="searchFilm" />
    </header>

    <main>
      <Films :arrayFilms="arrayFilms" :arraySeries="arraySeries" />
    </main>
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

<style lang="scss" >
@import './assets/style/common.scss';
@import url('https://fonts.googleapis.com/css2?family=Open+Sans:ital,wght@0,300;0,400;0,500;0,600;0,700;0,800;1,300;1,400;1,500;1,600;1,700;1,800&display=swap');

</style>
