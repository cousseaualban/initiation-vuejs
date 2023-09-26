<template>
  <div id="app">
    <TopRatedMovies />

    <div v-if="$forceUpdate.path == '/'">
      <!-- Si la route est / (racine du site)-->
      <h1 class="pt-5 font-weight-light">
        Vos films préférés sont sur VueJS Movies !
      </h1>
      <MoviesList :movies="movies" :loading="loading" :errored="errored" />
    </div>

    <div v-else>
      <!-- Si la route est différente de / -->
      <router-view :key="$forceUpdate.fullPath"></router-view>
    </div>

    <FooterApp />
  </div>
</template>

<script>
// import AmericanMovies from "./components/AmericanMovies.vue";
  import TopRatedMovies from "./components/TopRatedMovies.vue";
// import DetailsMovies from "./components/MovieDetails.vue";
//  import LastMovies from "./components/LastMovies.vue";

export default {
  name: "app",
  components: {
    // AmericanMovies,
    TopRatedMovies,
    // DetailsMovies,
    // LastMovies,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
