<template>
  <div id="app">
    <HeaderComp @searchVideo="userSearch" />

    <MainComp :moviesRes="movieArray" :tvshowsRes="tvshowArray" />
  </div>
</template>

<script>
import HeaderComp from "./components/HeaderComp.vue";
import MainComp from "./components/MainComp.vue";

import axios from "axios";

export default {
  name: "App",
  components: {
    HeaderComp,
    MainComp,
  },
  data() {
    return {
      // valore vuoto che raccogliera la selezione dell utente
      searchVideo: "",
      // info riferite all url dell api
      apiKey: "8a0c7ffee9a756d284aa4154b924940e",
      lang: "it-IT",
      // info riferite ai film
      movieArray: [],
      // info riferite ai telefilm
      tvshowArray: [],
    };
  },
  methods: {
    userSearch(selezione) {
      this.searchVideo = selezione;
      console.log(this.searchVideo);

      axios
        .all([
          axios.get("https://api.themoviedb.org/3/search/movie", {
            params: {
              api_key: this.apiKey,
              language: this.lang,
              query: this.searchVideo,
            },
          }),

          axios.get("https://api.themoviedb.org/3/search/tv", {
            params: {
              api_key: this.apiKey,
              language: this.lang,
              query: this.searchVideo,
            },
          }),
        ])

        .then(
          axios.spread((respMovies, respShow) => {
            this.movieArray = respMovies.data.results;
            this.tvshowArray = respShow.data.results;
          })
        )

        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>

<style lang="scss">
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background-color: #141414;
}
</style>
