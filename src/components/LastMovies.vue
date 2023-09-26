<!-- Films de l'année en cours uniquement -->

<!-- Films américains du moment -->

<template>
    <div class="container">
      <h1>Last Movies:</h1>
      <table class="table" v-if="lastMovies">
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
            v-for="lastMovie in lastMovies.results"
            :key="lastMovie.id"
          >
            <th scope="row">{{ lastMovie.id }}</th>
            <td>{{ lastMovie.original_language }}</td>
            <td>{{ lastMovie.original_title }}</td>
            <td>{{ lastMovie.overview }}</td>
            <td>{{ lastMovie.popularity }}</td>
            <td>
              <img
                :src="
                  'https://image.tmdb.org/t/p/w200' + lastMovie.poster_path
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
    name: "LastMovies",
    data() {
      return {
        lastMovies: null,
      };
    },
    created() {
        const url = 'https://api.themoviedb.org/3/movie/latest';

  
      axios
        .get(url, {
          headers: {
            "Content-Type": "application/json",
            Authorization:
              "Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiJjYTZjMjQ5N2JjOTg0Zjk2MWFiNDJlMGE3NTdhY2NkMSIsInN1YiI6IjY1MDAzMGExMWJmMjY2MDExYzc4MTMyMiIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.oSLjNy7huqmj7YKQUa2EzLPEkOxzsZIJ6Fa0WVEnduQ", // Remplacez par votre clé d'API
          },
        })
        .then((res) => {
          this.lastMovies = res.data;
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
  