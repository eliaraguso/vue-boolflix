<template>
  <div id="app">
    <Header @search="searchFilms" />
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
      search: '',
      arrayFilms: [],
    };
  },

  methods: {
    searchFilms(text) {
      this.search = text;
      console.log(text);
      axios.get('https://api.themoviedb.org/3/search/movie', {
        params: {
          api_key: 'f3ccf82f739dd6e779adfa5f91bae60b',
          query: this.search
        }
      })
       .then( (resp) => {
        this.arrayFilms = resp.data.results;
    });
    }
  },
};
</script>

<style lang="scss">
</style>
