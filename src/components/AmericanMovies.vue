<!-- Films américains du moment -->

<template>
  <div class="container">
    <h1>American Movies:</h1>
    <table class="table">
        <thead>
            <tr>
                <th scope="col">ID</th>
                <th scope="col">Original Language</th>
                <th scope="col">Original Title</th>
                <th scope="col">Overview</th>
                <th scope="col">Popularity</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="americanMovie in americanMovies" v-bind:id="americanMovie.id">
                <th scope="row">{{ americanMovie.id }}</th>
                <td>{{ americanMovie.original_language }}</td>
                <td>{{ americanMovie.original_title }}</td>
                <td>{{ americanMovie.overview }}</td>
                <td>{{ americanMovie.popularity }}</td>

            </tr>
        </tbody>
    </table>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'AmericanMovies',
  data() {
    return {
        americanMovies: null,
    };
  },
  created: function(){
    axios
        .get(url, {
            headers: {
                'Content-Type': 'application/json',
                'Authorization': 'Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiJjYTZjMjQ5N2JjOTg0Zjk2MWFiNDJlMGE3NTdhY2NkMSIsInN1YiI6IjY1MDAzMGExMWJmMjY2MDExYzc4MTMyMiIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.oSLjNy7huqmj7YKQUa2EzLPEkOxzsZIJ6Fa0WVEnduQ'
            }
        })
        .then(res => {
            this.americanMovies = res.data;
        })
  }
};

// headers: {
//             'Content-Type': 'application/json',
//             'Authorization': 'Bearer '+TOKEN
//         }

const url = 'https://api.themoviedb.org/3/discover/movie?include_adult=false&include_video=false&language=en-US&page=1&sort_by=popularity.desc';

</script>

<style>
    h1{
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