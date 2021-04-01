<template>
  <div class="movies-new">
    <form>
      <div class="form-group">
        <label for="exampleInputTitle">Title</label>
        <input type="text" class="form-control" id="exampleInputTitle" placeholder="Title" v-model="movieTitle" />
      </div>
      <div class="form-group">
        <label for="exampleInputPlot">Plot</label>
        <input type="text" class="form-control" id="exampleInputPlot" placeholder="Plot" v-model="moviePlot" />
      </div>
      <div class="form-group">
        <label for="exampleInputYear">Year</label>
        <input type="integer" class="form-control" id="exampleInputYear" placeholder="Year" v-model="movieYear" />
      </div>
      <button type="submit" class="btn btn-primary" v-on:click="createMovie()">Submit</button>
    </form>
    <!-- <div>
      <h2>Add a movie.</h2>
      <p>
        Title:
        <input type="text" placeholder="Title" v-model="movieTitle" />
      </p>
      <p>
        Plot:
        <input type="text" placeholder="Plot" v-model="moviePlot" />
      </p>
      <p>
        Year:
        <input type="text" placeholder="Year" v-model="movieYear" />
        <br />
      </p>
      <p>
        <button v-on:click="createMovie()">Add Movie</button>
      </p>
    </div> -->
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      movieTitle: "",
      moviePlot: "",
      movieYear: "",
    };
  },
  created: function () {
    // this.indexPlaces();
  },
  methods: {
    createMovie: function () {
      console.log("Adding a Movie!");
      var params = {
        title: this.movieTitle,
        body: this.moviePlot,
        image: this.movieYear,
      };
      axios
        .post("/api/movies", params)
        .then(() => {
          this.$router.push("/movies");
        })
        .catch((error) => console.log(error.response));
    },
  },
};
</script>
