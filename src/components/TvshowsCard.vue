<template>
  <div class="card_tvshow">
    <img src="" alt="" />
    <div class="info_card">
      <h3>{{ tvshow.name }}</h3>
      <h3>{{ tvshow.original_name }}</h3>
      <h5>{{ tvshow.original_language }}</h5>
      <h5>{{ tvshow.vote_average }}</h5>
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
  background-color: black;
  color: white;
  margin: 10px;
}
</style>
