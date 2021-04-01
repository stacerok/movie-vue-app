<template>
  <!-- <div class="movies-index"> -->
  <!-- <div v-for="movie in movies" v-bind:key="movie.id">
      <router-link v-bind:to="`movies/${movie.id}`">
        <h3>{{ movie.title }}</h3>
      </router-link>
      {{ movie.year }}
      <br />
      <br />
    </div> -->
  <div class="container">
    <div class="row">
      <div class="col-sm-6">
        <div class="card" v-for="movie in movies" v-bind:key="movie.id">
          <div class="card-body">
            <h5 class="card-title">{{ movie.title }}</h5>
            <p class="card-text">{{ movie.year }}</p>
            <router-link class="btn btn-primary" v-bind:to="`movies/${movie.id}`">More Info...</router-link>
          </div>
        </div>
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
      movies: [],
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
  },
};
</script>
