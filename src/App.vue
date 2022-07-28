<template>
  <div>
    <BaseHeader @btn-search-click="setQueryAndSearch"/>
    <main>
      <SectionMovies :searchArray="movies"/>
      <SectionMovies :searchArray="series"/>
    </main>
  </div>
</template>

<script>
import BaseHeader from "./components/BaseHeader.vue"
import SectionMovies from "./components/SectionMovies.vue"
import axios from "axios"

export default {
  name: 'BoolFlix',
  components: {
    BaseHeader,
    SectionMovies,
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
        this.movies = res.data.results.map((item)=>{
          return item = {title: item.title, original_title: item.original_title, language: item.original_language, vote: item.vote_average};
        })
      })
      axios.get(`https://api.themoviedb.org/3/search/tv?api_key=a69091a486f611ccfdfadd6ece3af0c2&query=${this.query}&language=it-IT`)
      .then(res => {
        this.series = res.data.results.map((item)=>{
          return item = {title: item.name, original_title: item.original_name, language: item.original_language, vote: item.vote_average};
        })
      })
    },
  },
}
</script>

<style lang="scss">

</style>
