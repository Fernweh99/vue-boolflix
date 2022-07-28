<template>
  <div class="container">
    <ul>
      <li v-for="item in searchArray" :key="item.original_title">
        <h3>Titolo:</h3> {{ item.title }}
        <h3>Titolo Originale:</h3> {{ item.original_title }}
        <h3>Lingua:</h3> {{ item.language }}
        <h3>Voto:</h3> {{ item.vote }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "SectionMovies",
  props: {
    searchArray: Array,
  }
}
</script>

<style>

</style>