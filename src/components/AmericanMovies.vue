<!-- Films américains du moment -->

<template>
  <div class="container">
    <h1>American Movies:</h1>
    <table class="table" v-if="americanMovies">
      <thead>
        <tr>
          <th scope="col">ID</th>
          <th scope="col">Original Language</th>
          <th scope="col">Original Title</th>
          <th scope="col">Overview</th>
          <th scope="col">Popularity</th>
          <th scope="col">Poster Path</th>
        </tr>
      </thead>
      <tbody>
        <tr
          v-for="americanMovie in americanMovies.results"
          :key="americanMovie.id"
        >
          <th scope="row">{{ americanMovie.id }}</th>
          <td>{{ americanMovie.original_language }}</td>
          <td>{{ americanMovie.original_title }}</td>
          <td>{{ americanMovie.overview }}</td>
          <td>{{ americanMovie.popularity }}</td>
          <td>
            <img
              :src="
                'https://image.tmdb.org/t/p/w200' + americanMovie.poster_path
              "
              alt="Movie Poster"
            />
          </td>
        </tr>
      </tbody>
    </table>
    <p v-else>Loading...</p>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "AmericanMovies",
  data() {
    return {
      americanMovies: null,
    };
  },
  created() {
    const url =
      "https://api.themoviedb.org/3/movie/popular?language=en-US&page=1";

    axios
      .get(url, {
        headers: {
          "Content-Type": "application/json",
          Authorization:
            "Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiJjYTZjMjQ5N2JjOTg0Zjk2MWFiNDJlMGE3NTdhY2NkMSIsInN1YiI6IjY1MDAzMGExMWJmMjY2MDExYzc4MTMyMiIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.oSLjNy7huqmj7YKQUa2EzLPEkOxzsZIJ6Fa0WVEnduQ", // Remplacez par votre clé d'API
        },
      })
      .then((res) => {
        this.americanMovies = res.data;
      })
      .catch((error) => {
        console.error("Error fetching data:", error);
      });
  },
};
</script>

<style>
h1 {
  color: green;
  font-size: 4em;
}
</style>

<!-- 

    Stocker dans une variable la clé de l'API
    Trouver un moyen avec GET de récupérer les datas sur le site the Movie
    Ensuite, faire then.response consoleLog avec les données récupérées
    Stockés le tout dans data()
    Déplacer la requête dans store.js et affecter ce dernier à data
-->
