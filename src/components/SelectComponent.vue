<template>
  <select @change="emitValue" v-model="value" name="" id="">
    <option value="">Filtra per Genere</option>
    <option v-for="genre in genress" v-show="getGen.includes(genre.id)" :key="genre.id" :value="genre.id">{{ genre.name }}</option>
  </select>
</template>

<script>
  import axios from "axios"
export default {
  name: "SelectComponent",
  props: {
    genreOf: String,
    genres: Set,
  },
  data() {
    return {
      baseUrl: "https://api.themoviedb.org/3",
      genress: [],
      value: "",
    }
  },
  computed: {
    getGen() {
      return [...this.genres]
    }
  },
  methods: {
    emitValue() {
      this.$emit("change-value", this.value)
    },
  },
  mounted() {
    axios.get(`https://api.themoviedb.org/3/genre/${this.genreOf}/list?api_key=a69091a486f611ccfdfadd6ece3af0c2`)
    .then(res => {
      this.genress = res.data.genres
    })
  }
}
</script>

<style>
  select {
    height: 40px;
    border-radius: 12px;
    padding: 3px 10px;
  }
</style>