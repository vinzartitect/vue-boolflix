<template>
  <div class="main">
    <h2>Films</h2>
    <div class="main_cards">
      <MoviesCard
        v-for="(movie, index) in moviesRes"
        :key="index"
        :movie="movie"
      />
    </div>

    <h2>Series</h2>
    <div class="main_cards">
      <TvshowsCard
        v-for="(tvshow, index) in tvshowsRes"
        :key="index"
        :tvshow="tvshow"
      />
    </div>
  </div>
</template>

<script>
import MoviesCard from "./MoviesCard.vue";
import TvshowsCard from "./TvshowsCard.vue";

export default {
  name: "MainComp",
  components: {
    MoviesCard,
    TvshowsCard,
  },
  props: {
    moviesRes: Array,
    tvshowsRes: Array,
  },
};
</script>

<style lang="scss" scoped>
.main {
  width: 90%;
  min-height: calc(100vh - 100px);
  margin: 0 auto;

  h2 {
    margin: 20px 0 10px 0;
    color: white;
  }

  .main_cards {
    display: flex;
    justify-content: start;
    flex-wrap: wrap;
  }
}
</style>
