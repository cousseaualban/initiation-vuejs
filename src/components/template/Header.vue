<template>
  <script src="https://unpkg.com/vue@3"></script>
  <script src="https://unpkg.com/vue-router@4"></script>

  <div id="header">
    <p>
      <!-- use the router-link component for navigation. -->
      <!-- specify the link by passing the `to` prop. -->
      <!-- `<router-link>` will render an `<a>` tag with the correct `href` attribute -->
      <router-link to="/">Accueil</router-link>
      <router-link to="/LastMovies">Films sorties en 2022</router-link>
      <router-link to="/FrenchMovies">Films français</router-link>
      <router-link to="/AmericanMovies">Films américains</router-link>
      <router-link to="/TopRatedMovies">Top 50 films</router-link>
    </p>
    <!-- route outlet -->
    <!-- component matched by the route will render here -->
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: "HeaderNav",
};
</script>
