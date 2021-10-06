<template>
  <form action="">
    <input type="search" v-model="searchInput" />
    <button type="submit" @click.prevent="$emit('search', searchInput)">
      Cerca
    </button>
  </form>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      searchInput: "",
    };
  },
};
</script>

<style lang="scss" scoped>
</style>