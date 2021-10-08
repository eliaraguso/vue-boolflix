<template>
<header :class="{classA: scrollPosition < 100, classB: scrollPosition > 100}">
  <div class="boolflix-logo">
    <img src="https://fontmeme.com/permalink/211007/4937b74c6317b36c509baa13669b4b20.png" alt="">
  </div>
  <form class="search" action="">
    <input id="searchBar" type="search" v-model="searchInput" />
    <button id="searchButton" type="submit" @click.prevent="$emit('search', searchInput)">
      Cerca
    </button>
  </form>
  </header>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      searchInput: "",
      scrollPosition: null,
    }},
     methods: {
    updateScroll() {
      this.scrollPosition = window.scrollY
    },
    },
    mounted() {
    window.addEventListener('scroll', this.updateScroll)
    },
    
    destroy() {
    window.removeEventListener('scroll', this.updateScroll)
    },
}

</script>

<style lang="scss" scoped>
  header {
    display: flex;
    justify-content: space-between;
    background-image: linear-gradient(to bottom, #141414, #171717, #1b1b1b, #1e1e1e, #212121, #262626, #2b2b2b, #303030, #383838, #414141, #4a4a4a, #535353);
    position: fixed;
    width: 100%;
    height: 70px;
    align-items: center;
    z-index: 10;
  }

  .search {
    padding-right: 40px;
    #searchBar {
      background-color: #141414;
      border: 1px solid white;
      height: 30px;
      margin-right: 40px;
      border-radius: 5px;
      color: white;
    }
    #searchButton {
      color: white;
      background-color: black;
      border: 1px solid white;
      padding: 7px 20px;
      border-radius: 5px;
    }
  }

  .boolflix-logo {
    padding-left: 40px;
    img {
      height: 35px;
    }
  }
  .classA {
    visibility: visible;
  }
  .classB {
    visibility: hidden;
  }
</style>