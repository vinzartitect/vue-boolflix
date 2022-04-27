<template>
  <div class="card_movie">
    <img class="poster" :src="getPoster()" alt="" />
    <div class="info_card">
      <h4>Titolo: {{ movie.title }}</h4>
      <h4>Titolo originale: {{ movie.original_title }}</h4>
      <div>
        <h5>Lingua:</h5>
        <span
          class="flag"
          :class="
            movie.original_language == 'en'
              ? 'flag-en'
              : movie.original_language == 'it'
              ? 'flag-it'
              : 'flag-unknown'
          "
        >
          <!-- {{ movie.original_language }} -->
        </span>
      </div>

      <p class="star-vb">
        <!-- {{ movie.vote_average }} -->
        <i
          v-for="i in 5"
          :key="i"
          class="fa-star"
          :class="i <= stars() ? 'fa-solid' : 'fa-regular'"
        ></i>
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: "MoviesCard",
  props: {
    movie: Object,
  },
  data() {
    return {
      // variabile della locandina tipo sconosciuta
      posterUnknown: require("../assets/posterunknown.png"),
    };
  },
  methods: {
    getPoster() {
      if (this.movie.poster_path === null) {
        return this.posterUnknown;
      } else {
        return "https://image.tmdb.org/t/p/original" + this.movie.poster_path;
      }
    },

    stars() {
      const votoArrotondato = Math.ceil(this.movie.vote_average / 2);
      return votoArrotondato;
    },
  },
};
</script>

<style lang="scss" scoped>
.card_movie {
  width: 200px;
  min-height: 100%;
  max-height: 480px;
  background-color: black;
  color: white;
  margin: 10px;
  position: relative;

  .poster {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  &:hover .info_card {
    display: block;
  }

  .info_card {
    padding: 10px;
    background: black;
    position: absolute;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
    display: none;
  }

  .flag {
    background-size: contain;
    height: 24px;
    width: 24px;
    background-repeat: no-repeat;
    display: inline-block;
  }
  .flag-it {
    background-image: url("../assets/icons8-italia-48.png");
  }
  .flag-en {
    background-image: url("../assets/icons8-gran-bretagna-48.png");
  }
  .flag-unknown {
    background-image: url("../assets/unknown-flag.png");
  }
  .star-vb {
    color: yellow;
  }
}
</style>
