<template>
  <div>
    <Film v-for="(film, index) in arrayFilms" :key="index" :film="film" />
  </div>
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
  },
};
</script>

<style lang="scss" scoped>
</style>