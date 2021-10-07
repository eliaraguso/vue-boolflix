<template>
  <main>
    <section class="films">
      <h2>Films</h2>
      <!-- Ciclo per i film -->
      <Film v-for="film in arrayFilms" :key="film.id" :film="film" />
    </section>

    <section class="series">
      <h2>Serie TV</h2>
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
}
</style>