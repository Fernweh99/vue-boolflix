<template>
  <header>
    <input type="text" v-model="searchText" placeholder="Cerca un film o una serie Tv">
    <button @click="emitSearchText">Vai</button>
  </header>
</template>

<script>
export default {
  name: "BaseHeader",
  data() {
    return {
      searchText: ""
    }
  },
  methods: {
    emitSearchText () {
      this.$emit("btn-search-click", this.searchText)
    }
  }
}
</script>

<style>

</style>