<template>
  <div class="movies-index">
    <h1>Movies!</h1>

    <div v-for="movie in movies">
      <router-link :to="`/movies/${movie.id}`">
        <h2>Title: {{ movie.title }}</h2>
      </router-link>
      <p>Year: {{ movie.year }}</p>
      <p>Plot: {{ movie.plot }}</p>
      <p>Director: {{ movie.director }}</p>
    </div>

  </div>
</template>

<style>
</style>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      movies: [],
    };
  },
  created: function() {
    this.indexMovies();
  },
  methods: {
    indexMovies: function () {
      axios.get("/api/movies").then(response => {
        console.log(response.data);
        this.movies = response.data;
      });
    }
  }
};
</script>