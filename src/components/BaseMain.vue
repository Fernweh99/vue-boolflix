<template>
  <main class="py-5">
    <div v-if="!isOnSearch" class="before-search">
      <h2 class="display-3">Cerca un Film o una Serie</h2>
    </div>
    <div v-else class="container">
      <h2 class="display-3 text-white mb-5">Hai cercato: {{ isOnSearch }}</h2>
      <h3 class="text-center display-2 text-white mb-5">Film</h3>
      <SelectComponent @change-value="setValueMovieSelect" :genreOf="movie"/>
      <div class="position-relative">
        <!-- <Btn-slider v-if="movies.length > 0" direction="left"/> -->
        <div id="movies" v-if="filteredMovies.length > 0" class="row cs_row row-cols-2 row-cols-md-3 row-cols-lg-4 g-0 gy-5">
          <div class="col" v-for="movie in filteredMovies" :key="movie.id">
            <Single-card-product :id="movie.id" :title="movie.title" :original_title="movie.original_title" :vote="movie.vote_average" :language="movie.original_language" :poster="movie.poster_path" :overview="movie.overview"/>
          </div>
        </div>
        <div v-else class="text-center"><h1>NESSUN FILM TROVATO!</h1></div>
        <!-- <Btn-slider v-if="movies.length > 0" direction="right"/> -->
      </div>
      <h3 class="text-center display-2 text-white my-5">Series</h3>
      <SelectComponent @change-value="setValueSeriesSelect" genreOf="tv"/>
      <div class="position-relative">
        <!-- <Btn-slider v-if="series.length > 0" direction="left"/> -->
        <div id="series" v-if="filteredSeries.length > 0" class="row cs_row row-cols-2 row-cols-md-3 row-cols-lg-4 g-0 gy-5">
          <div class="col" v-for="serie in filteredSeries" :key="serie.id">
            <Single-card-product :title="serie.name" :original_title="serie.original_name" :vote="serie.vote_average" :language="serie.original_language" :poster="serie.poster_path" :overview="serie.overview"/>
          </div>
        </div>
        <div v-else class="text-center"><h1>NESSUNA SERIE TROVATA!</h1></div>
        <!-- <Btn-slider v-if="series.length > 0" direction="right"/> -->
      </div>
    </div>
  </main>
</template>

<script>
import SingleCardProduct from "./SingleCardProduct.vue"
import SelectComponent from "./SelectComponent.vue";
// import BtnSlider from "./BtnSlider.vue"

export default {
  name: "BaseMain",
  components: {
    SingleCardProduct,
    SelectComponent,
},
  props: {
    movies: Array,
    series: Array,
    isOnSearch: String,
  },
  data() {
    return {
      valueOptionMovie: "",
      valueOptionSeries: "",
    }
  },
  methods: { 
    setValueMovieSelect(value) {
      this.valueOptionMovie = value;
    },
    setValueSeriesSelect(value) {
      this.valueOptionSeries = value;
    }
  },
  computed: {
    filteredMovies() {
      return this.movies.filter(movie=>{
        if (this.valueOptionMovie == "") return true;
        return (movie.genre_ids.includes(this.valueOptionMovie))
      })
    },
    filteredSeries() {
      return this.series.filter(serie=>{
        if (this.valueOptionSeries == "") return true;
        return (serie.genre_ids.includes(this.valueOptionSeries))
      })
    }
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
    .cs_row {
      flex-wrap: nowrap;
      margin: 0 -10px;
      overflow: scroll;
      position: relative;
      .col {
        padding: 0 3px;
      }
    }
  }
</style>