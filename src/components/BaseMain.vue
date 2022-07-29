<template>
  <div class="container">
    <h3>Movies</h3>
    <ul v-for="movie in movies" :key="movie.id">
      <SingleCardProduct :title="movie.title" :original_title="movie.original_title" :vote="movie.vote_average" :language="movie.original_language"/>
    </ul>
    <h3>Series</h3>
    <ul v-for="serie in series" :key="serie.id">
      <SingleCardProduct :title="serie.name" :original_title="serie.original_name" :vote="serie.vote_average" :language="serie.original_language"/>
    </ul>
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

</style>