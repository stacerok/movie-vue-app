<template>
  <div class="home">
    <!-- <h1>{{ message }}</h1>
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
    <p> -->
      <!-- Genre:
      <input type="text" placeholder="Movie Genre" v-model="newMovieGenre" />
      <br /> -->
      <!-- <br />

      <button v-on:click="createMovie()">Add Movie</button>
    </p>

    <div>
      <div v-for="movie in movies" v-bind:key="movie.id">
        <h3>{{ movie.title }}</h3>
        {{ movie.plot }}
        <br />
        {{ movie.year }}
        <br /> -->
        <!-- {{ movie.genres_name }}
        <br /> -->
        <!-- <button v-on:click="showMovie(movie)">More Info.</button>
        <dialog id="movie-details">
          <form method="dialog">
            <h1>Movie Info</h1>
            <p>
              Title:
              <input type="text" v-model="currentMovie.title" />
            </p>
            <p>
              Plot:
              <input type="text" v-model="currentMovie.plot" />
            </p>
            <p>
              Year:
              <input type="text" v-model="currentMovie.year" />
            </p> -->
            <!-- <p>
              Genre:
              <input type="text" v-model="currentMovie.genre_name" />
            </p> -->
            <!-- <button v-on:click="updateMovie(currentMovie)">Update</button>
            <button v-on:click="destroyMovie(currentMovie)">Delete</button>
            <button>Close</button>
          </form>
        </dialog>
      </div>
    </div> -->
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
      currentMovie: {},
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
        .catch((error) => console.log(error.response));
    },
    showMovie: function (movie) {
      console.log(movie), (this.currentMovie = movie), document.querySelector("#movie-details").showModal();
    },
    updateMovie: function (movie) {
      var params = {
        title: movie.title,
        plot: movie.plot,
        year: movie.year,
        genre: movie.genre_name,
      };
      axios.patch("/api/movies/" + movie.id, params).then((response) => {
        console.log("Success", response.data);
      });
    },
    destroyMovie: function (movie) {
      axios.delete("/api/movies/" + movie.id).then((response) => {
        console.log("Movie deleted", response.data);
        var index = this.movies.indexOf(movie);
        this.movies.splice(index, 1);
      });
    },
  },
};
</script>
