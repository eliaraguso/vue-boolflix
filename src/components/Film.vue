<template>
  <ul>
      <li>{{film.title}}</li>
      <li>{{film.original_title}}</li>
      <li>{{film.original_language}}</li>
      <li>{{film.vote_average}}</li>

  </ul>
</template>

<script>
export default {
    name: 'Film',
    props: {
        film: Object
    }

};
</script>

<style>

</style>