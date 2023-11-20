<template>
  <div>
    <h2 class="mt-3">Películas Favoritas</h2>
    <div class="row">
      <div class="col-md-4" v-for="item in movies" :key="item.id">
        <div class="card">
          <img :src="item.imagen" class="card-img-top" alt="Poster de la película">
          <div class="card-body">
            <h5 class="card-title">{{ item.title }}</h5>
            <p class="card-text">{{ item.description }}</p>
            <p class="card-text"><strong>Género:</strong> {{ getGenresList(item.genre) }}</p>
            <button class="btn btn-primary mt-2" @click="verDetalle(item)">Ver Detalle</button>
            <button class="btn btn-danger mt-2" @click="removerFavorito(item)">Quitar de Favoritos</button>
          </div>
        </div>
      </div>
    </div>
    <div v-if="movies.length === 0" class="mt-3">
      <p>No tienes películas favoritas.</p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    movies: {
      type: Array,
      required: true,
    },
  },
  methods: {
    verDetalle(item) {
      this.$emit('detail', item);
    },
    removerFavorito(item) {
      this.$emit('remove-favorite', item);
    },
    getGenresList(genreIds) {
      const genreMap = {
        28: 'Acción',
        27: 'Terror',
        18: 'Drama',
        16: 'Animacion',
        12: 'Aventura',
        35: 'Comedia',
        14: 'Fantasia',
        878: 'Ciencia Ficcion',
        53: 'Suspenso',
        99: 'Documental',
        36: 'Historia'
      };

      const genreNames = genreIds.map((id) => genreMap[id] || 'Desconocido');
      return genreNames.join(', ');
    },
  },
};
</script>
  
  <style scoped>
h2 {
  display: none;
}



.container{
    display: flex;
    width: 80%;
    justify-content: space-between;
    flex-direction: row;
    flex-wrap: wrap;
  }
.card {
    background-color: rgb(47, 46, 46);
    margin-bottom: 20px;
    display: flex;
    margin-right: 2px;
    height: auto;
    width: 80%;
    text-align: center;
    align-items: center;
}

h5{
    color: white;
}

img{
    width: 100%;
}

.card-title {
  font-size: 1.2rem;
}

.card-text {
  color: #ccc;
}

.btn-primary {
  background-color: #e50914;
  border-color: #e50914;
}

.btn-danger {
  background-color: #ff3e3e;
  border-color: #ff3e3e;
}
</style>