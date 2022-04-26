<template>
  <div class="card_movie">
    <img src="" alt="" />
    <div class="info_card">
      <h3>Titolo: {{ movie.title }}</h3>
      <h3>Titolo originale: {{ movie.original_title }}</h3>
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

      <h5>Voto: {{ movie.vote_average }}</h5>
    </div>
  </div>
</template>

<script>
export default {
  name: "MoviesCard",
  props: {
    movie: Object,
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
}
</style>
