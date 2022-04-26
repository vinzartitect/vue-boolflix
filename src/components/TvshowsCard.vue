<template>
  <div class="card_tvshow">
    <img class="poster" :src="getPoster()" alt="" />
    <div class="info_card">
      <h4>Titolo: {{ tvshow.name }}</h4>
      <h4>Titolo originale: {{ tvshow.original_name }}</h4>
      <div>
        <h5>Lingua:</h5>
        <span
          class="flag"
          :class="
            tvshow.original_language == 'en'
              ? 'flag-en'
              : tvshow.original_language == 'it'
              ? 'flag-it'
              : 'flag-unknown'
          "
        >
          <!-- {{ tvshow.original_language }} -->
        </span>
      </div>

      <h5>Voto: {{ tvshow.vote_average }}</h5>
    </div>
  </div>
</template>

<script>
export default {
  name: "TvshowsCard",
  props: {
    tvshow: Object,
  },
  data() {
    return {
      // variabile della locandina tipo sconosciuta
      posterUnknown: require("../assets/posterunknown.png"),
    };
  },
  methods: {
    getPoster() {
      if (this.tvshow.poster_path === null) {
        return this.posterUnknown;
      } else {
        return "https://image.tmdb.org/t/p/original" + this.tvshow.poster_path;
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.card_tvshow {
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
}
</style>
