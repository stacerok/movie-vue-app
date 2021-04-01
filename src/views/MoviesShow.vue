<template>
  <div class="movies-show">
    <div class="container">
      <!-- <div v-for="post in posts" v-bind:key="post.id"> -->
      <h3>{{ movie.title }}</h3>
      {{ movie.plot }}
      <br />
      <router-link v-bind:to="`/movies/${movie.id}/edit`">More info...</router-link>
    </div>
    <br />
    <button v-on:click="destroyMovie(movie)">Delete Movie</button>
    <!-- </div> -->
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      movie: {},
    };
  },
  created: function () {
    this.showMovies();
  },
  methods: {
    showMovies: function () {
      axios.get("/api/movies/" + this.$route.params.id).then((response) => {
        this.movie = response.data;
        console.log("All Movies:", this.movie);
      });
    },
    destroyMovie: function (movie) {
      axios.delete("/api/movies/" + movie.id).then(() => {
        console.log("Movie deleted.");
        this.$router.push("/movies");
      });
    },
  },
};
</script>
