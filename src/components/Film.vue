<template>
  <div class="film-card">
    <!-- <div class="background-container" :style="`background-image:url(${film.poster_path ? `https://image.tmdb.org/t/p/w300${film.poster_path}` : `https://www.fiaddaemiliaromagna.org/wp-content/uploads/2020/04/lavori-in-corso.jpeg)`}`"></div> -->
      <div class="poster-img">
        <img v-if="film.poster_path != null" :src="'https://image.tmdb.org/t/p/w342' + film.poster_path" alt="">
        <img v-else src="https://www.fiaddaemiliaromagna.org/wp-content/uploads/2020/04/lavori-in-corso.jpeg" alt="">
      </div>
      <div class="info-container">
        <ul>
          <li>
            <h2>Titolo: {{ film.title || film.name }}</h2>
          </li>
          <li>
            <h2>
              Titolo originale: {{ film.original_title || film.original_name }}
            </h2>
          </li>
          <li>
            <h2>
              Lingua:<country-flag :country="film.original_language == 'en' ? 'us' : film.original_language"/>
            </h2>
          </li>
          <li>
            <div class="stars-vote">
              <font-awesome-icon :icon="starSolid" v-for="(voto, index) in vote" :key="index"/>
              <font-awesome-icon :icon="starEmpty" v-for="(voto, index) in 5 - vote" :key="'empty' + index"/>
            </div>
          </li>
        </ul>
      </div>
  </div>
</template>

<script>
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
import { faStar as fasStar } from "@fortawesome/free-solid-svg-icons";
import { faStar as farStar } from "@fortawesome/free-regular-svg-icons";
export default {
  name: "Film",

  props: {
    film: Object,
  },

  components: {
    FontAwesomeIcon,
  },

  data() {
    return {
      vote: Math.ceil(this.film.vote_average / 2),
      linkPoster: this.film.poster_path,
      starSolid: fasStar,
      starEmpty: farStar,
    };
  },

  methods: {
    starsQuantity(vote) {
      vote = this.vote;
      return vote;
    },
  },
};
</script>

<style lang="scss" scoped>

ul {
  list-style:none;
}

.poster-img {
  border: 6px solid yellowgreen;
  top: 0;
  height: 100%;
  img {
    width: 100%;
    height: 100%;
  }
}


.film-card {
  border: 6px solid blue;
  width: calc((100% / 5));
  position: relative;
}

.film-card:hover {
  .info-container {
    visibility: visible;
  }
}
.info-container {
  border: 6px solid orangered;
  height: 100%;
  width: 100%;
  position: absolute;
  top: 0;
  visibility: hidden;
  color: white;
  background-color: black;
}



</style>