<!-- détails d’un film (au moins titre, langue, slogan, description et bande-annonce-->

<!-- Films américains du moment -->

<template>
    <div class="container">
      <h1>Details Movies:</h1>
      <table class="table" v-if="detailsMovies">
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
            v-for="detailsMovie in detailsMovies.results"
            :key="detailsMovie.id"
          >
            <th scope="row">{{ detailsMovie.id }}</th>
            <td>{{ detailsMovie.original_language }}</td>
            <td>{{ detailsMovie.original_title }}</td>
            <td>{{ detailsMovie.overview }}</td>
            <td>{{ detailsMovie.popularity }}</td>
            <td>
              <img
                :src="
                  'https://image.tmdb.org/t/p/w200' + detailsMovie.poster_path
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
    name: "DetailsMovies",
    data() {
      return {
        detailsMovies: null,
      };
    },
    created() {
        const url = 'https://api.themoviedb.org/3/movie/movie_id?language=en-US';

  
      axios
        .get(url, {
          headers: {
            "Content-Type": "application/json",
            Authorization:
              "Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiJjYTZjMjQ5N2JjOTg0Zjk2MWFiNDJlMGE3NTdhY2NkMSIsInN1YiI6IjY1MDAzMGExMWJmMjY2MDExYzc4MTMyMiIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.oSLjNy7huqmj7YKQUa2EzLPEkOxzsZIJ6Fa0WVEnduQ", // Remplacez par votre clé d'API
          },
        })
        .then((res) => {
          this.detailsMovies = res.data;
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
  