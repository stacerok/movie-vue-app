<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <h2>Add a Movie.</h2>
    <p>
      Title:
      <input type="text" placeholder="Movie Title" v-model="newMovieTitle" />
      <br />
    </p>
    <p>
      Plot:
      <input type="text" placeholder="Movie Plot" v-model="newMoviePlot" />
      <br />
    </p>
    <p>
      Year:
      <input type="text" placeholder="Movie Year" v-model="newMovieYear" />
      <br />
    </p>
    <p>
      Genre:
      <input type="text" placeholder="Movie Genre" v-model="newMovieGenre" />
      <br />
      <br />

      <button v-on:click="createMovie()">Add Movie</button>
    </p>

    <div>
      <div v-for="movie in movies" v-bind:key="movie.id">
        <h3>{{ movie.title }}</h3>
        {{ movie.plot }}
        <br />
        {{ movie.year }}
        <br />
        {{ movie.genre_name }}
      </div>
    </div>
  </div>
</template>
<style></style>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "My Movie Database",
      movies: [],
      newMovieTitle: "",
      newMoviePlot: "",
      newMovieYear: "",
      newMovieGenre: "",
    };
  },
  created: function () {
    this.indexMovies();
  },
  methods: {
    indexMovies: function () {
      axios.get("/api/movies").then((response) => {
        this.movies = response.data;
        console.log("All Movies:", this.movies);
      });
    },
    createMovie: function () {
      console.log("Adding a Movie!");
      var params = {
        title: this.newMovieTitle,
        plot: this.newMoviePlot,
        year: this.newMovieYear,
        genre: this.newMovieGenre,
      };
      axios
        .post("/api/movies", params)
        .then((response) => {
          console.log("Successfully added movie!", response.data);
          this.movies.push(response.data);
        })
        .catch((error) => {
          console.log(error.response.data.errors);
          this.errors = error.response.data.errors;
        });
    },
  },
};
</script>
