<template>
  <div class="movies-index">
    <h1>Movies!</h1>

    Search by title: <input v-model="titleFilter" list="titles">
    <datalist id="titles">
      <option v-for="movie in movies">{{movie.title}}</option>
    </datalist>
    <div v-for="movie in filterBy(movies, titleFilter, 'title')">
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
import Vue2Filters from "vue2-filters";

export default {
  mixins: [Vue2Filters.mixin],

  data: function() {
    return {
      movies: [],
      titleFilter: "",
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