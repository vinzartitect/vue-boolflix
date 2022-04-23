<template>
  <div class="main">
    <MoviesCard
      v-for="(movie, index) in moviesRes"
      :key="index"
      :movie="movie"
    />

    <TvshowsCard
      v-for="(tvshow, index) in tvshowsRes"
      :key="index"
      :tvshow="tvshow"
    />
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
  margin: 0 auto;
  display: flex;
  justify-content: start;
  flex-wrap: wrap;
}
</style>
