<template>
  <div class="card_movie">
    <img src="" alt="" />
    <div class="info_card">
      <h3>{{ movie.title }}</h3>
      <h3>{{ movie.original_title }}</h3>
      <h5>{{ movie.original_language }}</h5>
      <h5>{{ movie.vote_average }}</h5>
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
  background-color: black;
  color: white;
  margin: 10px;
}
</style>
