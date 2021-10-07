<template>
  <main>
    <h2>Films</h2>
    <section class="films">
      <!-- Ciclo per i film -->
      <Film v-for="film in arrayFilms" :key="film.id" :film="film" />
    </section>

    
    <h2>Serie TV</h2>
    <section class="series">
      <!-- Ciclo per le serie TV -->
      <Film v-for="film in arraySeries" :key="film.id" :film="film" />
    </section>
  </main>
</template>

<script>
import Film from "./Film.vue";

export default {
  name: "Films",
  components: {
    Film,
  },
  props: {
    arrayFilms: Array,
    arraySeries: Array,
  },
};
</script>

<style lang="scss" scoped>

.films,
.series {
  display: flex;
  flex-wrap: wrap;
}

main {
  // border: 6px solid peru;
  width: 80%;
  max-width: 1920px;
  margin: auto;
  padding-top: 80px;
  color: white;
}
</style>