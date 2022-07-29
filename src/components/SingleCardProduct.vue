<template>
  <div>
    <li>{{ title }}</li>
    <li>{{ original_title }}</li>
    <li>
      <img v-if="hasFlag" :src="srcFlag" :alt="'flag '+language">
      <span v-else>{{ language }}</span>
    </li>
    <li>{{ vote }}</li>
  </div>
</template>

<script>
export default {
  name: 'SingleCardProduct',
  props: {
    title: String,
    original_title: String,
    language: String,
    vote: Number,
  },
  computed: {
    hasFlag() {
      const flags = ["it", "en"];
      return (flags.includes(this.language))
    },
    srcFlag() {
      return require(`../assets/image/${this.language}.png`)
    }
  }
}
</script>

<style>

</style>