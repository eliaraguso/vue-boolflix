<template>
  <main>
    <Film v-for="(film, index) in arrayFilms" :key="index" :film="film" />
    <Film v-for="(film, index) in arraySeries" :key="index" :film="film" />

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