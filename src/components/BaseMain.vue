<template>
  <main class="py-5">
    <div v-if="!isOnSearch" class="before-search">
      <h2 class="display-3">Cerca un Film o una Serie</h2>
    </div>
    <div v-else class="container">
      <h3 class="text-center display-2 text-white mb-5">Film</h3>
      <div v-if="movies.length > 0" class="row row-cols-2 row-cols-md-3 row-cols-lg-4 g-0 gy-5">
        <div class="col" v-for="movie in movies" :key="movie.id">
          <SingleCardProduct :title="movie.title" :original_title="movie.original_title" :vote="movie.vote_average" :language="movie.original_language" :poster="movie.poster_path" :overview="movie.overview"/>
        </div>
      </div>
      <div v-else class="text-center"><h1>NESSUN FILM TROVATO!</h1></div>
      <h3 class="text-center display-2 text-white my-5">Series</h3>
      <div v-if="series.length > 0" class="row row-cols-2 row-cols-md-3 row-cols-lg-4 g-0 gy-5">
        <div class="col" v-for="serie in series" :key="serie.id">
          <SingleCardProduct :title="serie.name" :original_title="serie.original_name" :vote="serie.vote_average" :language="serie.original_language" :poster="serie.poster_path" :overview="serie.overview"/>
        </div>
      </div>
      <div v-else class="text-center"><h1>NESSUNA SERIE TROVATA!</h1></div>
    </div>
  </main>
</template>

<script>
import SingleCardProduct from "./SingleCardProduct.vue"

export default {
  name: "BaseMain",
  components: {
    SingleCardProduct,
  },
  props: {
    movies: Array,
    series: Array,
    isOnSearch: String,
  },
  data() {
    return {
    }
  },
  methods: {
  }
}
</script>

<style lang="scss">
  main {
    background-color: rgba(47, 41, 41, 0.937);
    min-height: 100%;
    display: flex;
    .before-search {
      width: 100%;
      display: flex;
      justify-content: center;
      align-items: center;
    }
    .col {
      padding: 0 3px;
    }
  }
</style>