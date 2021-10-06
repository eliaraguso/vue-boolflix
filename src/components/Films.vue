<template>
  <main>
    <Film v-for="film in arrayFilms" :key="film.id" :film="film" />
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