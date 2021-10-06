<template>
  <main>
    <!-- Ciclo per i film -->
    <h2>Films</h2>
    <Film v-for="film in arrayFilms" :key="film.id" :film="film" />

    <!-- Ciclo per le serie TV -->
    <h2>Serie TV</h2>
    <Film v-for="film in arraySeries" :key="film.id" :film="film" />

  </main>
</template>

<script>
import Film from "./Film.vue";

export default {
  name: "Films",
  components: {
    Film
  },
  props: {
    arrayFilms: Array,
    arraySeries: Array
  },
};
</script>

<style lang="scss" scoped>
</style>