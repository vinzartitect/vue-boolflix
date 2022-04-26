<template>
  <div class="card_tvshow">
    <img src="" alt="" />
    <div class="info_card">
      <h3>Titolo: {{ tvshow.name }}</h3>
      <h3>Titolo originale: {{ tvshow.original_name }}</h3>
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
