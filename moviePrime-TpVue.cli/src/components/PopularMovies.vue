<template>
    <div>
      <h2>Películas Populares</h2>
      <div class="movie-list">
        <img v-for="movie in movies" :key="movie.id" :src="movie.imagen" :alt="movie.title" @click="showDetail(movie)" />
      </div>
    </div>
  </template>
  
  <script>


  export default {
    props: {
      movies: Array,
    },
    methods: {
    showDetail(movie) {
      this.$emit('show-detail', movie);
    },
   
  },
  };
  </script>
  
  <style scoped>
  .movie-list {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
  }
  
  .movie-list img {
    border-radius: 50%;
    cursor: pointer;
    margin: 10px;
    transition: transform 0.2s;
    max-width: 150px; 
    max-height: 150px; 
  }
  
  .movie-list img:hover {
    transform: scale(1.1);
    border-radius: 10%;
  }
  
  
  </style>