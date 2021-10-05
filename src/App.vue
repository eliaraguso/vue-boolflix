<template>
  <div id="app">
    <Header @search="searchFilms"/>
    <Films/>
  </div>
</template>

<script>
// import axios from 'axios';
import Header from './components/Header.vue';
import Films from './components/Films.vue';

export default {
  
  name: 'App',
  
  components: {
    Header,
    Films
  },

  // created() {
  //   axios
        
  // },

  methods: {
    searchFilms(text) {
      console.log(text)
    }
  },

};
</script>

<style lang="scss">

</style>
