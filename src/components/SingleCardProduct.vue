<template>
  <div class="card">
    <img class="background" :src="srcPost" alt="poster">
    <div class="content">
      <p>{{ title }}</p>
      <p>{{ original_title }}</p>
      <img v-if="hasFlag" class="flag" :src="srcFlag" :alt="'flag '+language">
      <p v-else>{{ language }}</p>
      <p>{{ getNumberForStars }}</p>
    </div>
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
    poster: String,
  },
  computed: {
    hasFlag() {
      const flags = ["it", "en"];
      return (flags.includes(this.language))
    },
    srcFlag() {
      return require(`../assets/image/${this.language}.png`)
    },
    srcPost() {
      if (this.poster)return `https://image.tmdb.org/t/p/w342${this.poster}?api_key=a69091a486f611ccfdfadd6ece3af0c2`
      else return "https://upload.wikimedia.org/wikipedia/commons/thumb/6/65/No-Image-Placeholder.svg/1665px-No-Image-Placeholder.svg.png"
    },
    getNumberForStars() {
      return Math.ceil(Math.ceil(this.vote)/2)
    }
  }
}
</script>
  
<style lang="scss">
  .card {
    position: relative;
    height:500px;
    width: 342px;
    margin: 40px 0;
    .background {
      position: absolute;
      z-index: -1;
      top: 0;
      bottom: 0;
      height: 100%;
      width: 342px;
    }.content {
      overflow: auto;
      .flag {
        width: 50px
      }
    }
  }
</style>