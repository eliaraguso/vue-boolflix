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
            <h3>Titolo: <span>{{ film.title || film.name }}</span></h3>
          </li>
          <li>
            <h3>
              Titolo originale: <span>{{ film.original_title || film.original_name }}</span>
            </h3>
          </li>
          <li id="country-box">
            <h3>
              Lingua:<country-flag class="country-flag" :country="film.original_language == 'en' ? 'us' : film.original_language"/>
            </h3>
          </li>
          <li>
            
            <div class="stars-vote">
              <h3>Voto:</h3>
              <font-awesome-icon :icon="starSolid" v-for="(voto, index) in vote" :key="index"/>
              <font-awesome-icon :icon="starEmpty" v-for="(voto, index) in 5 - vote" :key="'empty' + index"/>
            </div>
          </li>
          <li>
            <h3>Overview: <span>{{film.overview}}</span></h3>
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

span {
  font-size: 14px;
  font-weight: normal;
}

ul {
  list-style:none;
  li {
    padding: 5px 0;
  }
}

.poster-img {
  // border: 6px solid yellowgreen;
  top: 0;
  height: 100%;
  img {
    width: 100%;
    height: 100%;
  }
}


.film-card {
  // border: 6px solid blue;
  margin: 10px 10px;
  width: calc((100% / 5) - 20px);
  position: relative;
}

.film-card:hover {
  .info-container {
    visibility: visible;
    opacity: 90%;
  }
}
.info-container {
  // border: 6px solid orangered;
  height: 100%;
  width: 100%;
  position: absolute;
  top: 0;
  visibility: hidden;
  color: white;
  background-color: black;
  padding-top: 5%;
  padding-left: 5%;
  overflow-y: scroll;
}

.stars-vote {
  h3,
  font-awesome-icon {
  display: inline-block;
  }

  
}

h3 {
    padding-right: 10px;
    font-size: 18px;
  }

#country-box {
  position: relative;
  .country-flag {
    position: absolute;
    top: 0;

  }
}

::-webkit-scrollbar {
    width: 4px;
}
 
/* Track */
::-webkit-scrollbar-track {
    -webkit-box-shadow: inset 0 0 6px rgba(0,0,0,0.3); 
    -webkit-border-radius: 10px;
    border-radius: 10px;
}
 
/* Handle */
::-webkit-scrollbar-thumb {
    -webkit-border-radius: 10px;
    border-radius: 10px;
    background: rgba(255, 255, 255, 0.8); 
    -webkit-box-shadow: inset 0 0 6px rgba(0,0,0,0.5); 
}


</style>