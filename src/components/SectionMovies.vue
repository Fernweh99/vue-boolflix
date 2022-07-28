<template>
  <div class="container">
    <ul>
      <li v-for="item in searchArray" :key="item.original_title">
        <h3>Titolo:</h3> {{ item.title }}
        <h3>Titolo Originale:</h3> {{ item.original_title }}
        <h3>Lingua:</h3>
        <span v-if="item.language !== 'it'&& item.language !== 'en'">{{ item.language }}</span>
        <div v-else>
          <img v-if="item.language == 'it'" src="../assets/image/it.png" alt="it flag">
          <img v-else src="../assets/image/en.png" alt="en flag">
        </div>
        <h3>Voto:</h3> {{ item.vote }}
      </li>
    </ul>
    ----------------------------------------------------------------
  </div>
</template>

<script>
export default {
  name: "SectionMovies",
  props: {
    searchArray: Array,
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