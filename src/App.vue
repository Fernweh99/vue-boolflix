<template>
  <div id="boolflix">
    <BaseHeader @btn-search-click="setQueryAndSearch"/>
    <BaseMain :movies="movies" :series="series" :isOnSearch="query"/>
  </div>
</template>

<script>
import BaseHeader from "./components/BaseHeader.vue"
import BaseMain from "./components/BaseMain.vue"
import axios from "axios"

export default {
  name: 'BoolFlix',
  components: {
    BaseHeader,
    BaseMain,
  },
  data() {
    return {
      movies: [],
      series: [],
      baseUrl: "https://api.themoviedb.org/3",
      query: "",
    }
  },
  methods: {
    setQueryAndSearch (value) {
      this.query = value;
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=a69091a486f611ccfdfadd6ece3af0c2&query=${this.query}&language=it-IT`)
      .then(res => {
        this.movies = res.data.results
      })
      axios.get(`https://api.themoviedb.org/3/search/tv?api_key=a69091a486f611ccfdfadd6ece3af0c2&query=${this.query}&language=it-IT`)
      .then(res => {
        this.series = res.data.results
      })
    },
    fethData () {
      
    }
  },
}
</script>

<style lang="scss">
@import "./assets/scss/style.scss";
  html {
    height: 100%;
  }
  body{
    height: 100%;
  }
  #boolflix {
    padding-top: 70px;
    height:100%
  }
</style>
