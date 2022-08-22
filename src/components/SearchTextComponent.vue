<template>
  <div>
    <input @keyup.enter="emitSearchText" type="text" v-model="searchText" placeholder="Cerca un film o una serie Tv">
    <button @click="emitSearchText">Vai</button>
  </div>
</template>

<script>
export default {
  name: "SearchTextComponent",
  data() {
    return {
      searchText: ""
    }
  },
  methods: {
    emitSearchText () {
      this.$emit("btn-search-click", this.searchText)
      this.searchText = "";
    }
  }
}
</script>

<style>

</style>