<template>
  <div class="container">
    <h3 class="text-center">Movies</h3>
    <div class="row row-cols-3">
      <div class="col" v-for="movie in movies" :key="movie.id">
        <SingleCardProduct :title="movie.title" :original_title="movie.original_title" :vote="movie.vote_average" :language="movie.original_language" :poster="movie.poster_path"/>
      </div>
    </div>
    <h3 class="text-center">Series</h3>
    <div class="row row-cols-3">
      <div class="col" v-for="serie in series" :key="serie.id">
        <SingleCardProduct :title="serie.name" :original_title="serie.original_name" :vote="serie.vote_average" :language="serie.original_language" :poster="serie.poster_path"/>
      </div>
    </div>
  </div>
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
  },
  data() {
    return {
    }
  },
  methods: {
  }
}
</script>

<style>
  .card {
    position: relative;
  }
</style>