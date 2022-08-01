<template>
  <div class="cs_card"
  @mouseover="hover=true" 
  @mouseleave="hover=false" >
    <img class="background" :src="srcPost" alt="poster">
    <div v-show="hover==true" class="content">
      <h3>Titolo:</h3><span>{{ title }}</span>
      <h3>Titolo Originale:</h3><span>{{ original_title }}</span>
      <h3>Lingua Originale:</h3><img v-if="hasFlag" class="flag" :src="srcFlag" :alt="'flag '+language">
      <span v-else>{{ language }}</span>
      <div>
        <h3>Valutazione:</h3>
        <svg v-for="(star , i) in maxRating" :key="i" xmlns="http://www.w3.org/2000/svg" width="16" height="16" :fill="isStar(i)" class="bi bi-star-fill" viewBox="0 0 16 16">
          <path d="M3.612 15.443c-.386.198-.824-.149-.746-.592l.83-4.73L.173 6.765c-.329-.314-.158-.888.283-.95l4.898-.696L7.538.792c.197-.39.73-.39.927 0l2.184 4.327 4.898.696c.441.062.612.636.282.95l-3.522 3.356.83 4.73c.078.443-.36.79-.746.592L8 13.187l-4.389 2.256z"/>
        </svg>
      </div>
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
  data() {
    return {
      maxRating: ["false", "false", "false", "false", "false"],
      hover: false,
    }
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
      return parseInt(Math.ceil(Math.ceil(this.vote)/2))
    },
  },
  methods: {
    isStar(i) {
      if(i < this.getNumberForStars) return "yellow"
      else return "white"
    }
  }
}
</script>
  
<style lang="scss">
  .cs_card {
    position: relative;
    height:500px;
    max-width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: black;
    border-radius: 7px;
    cursor: pointer;
    .background {
      position: absolute;
      z-index: 0;
      top: 0;
      bottom: 0;
      height: 100%;
      max-width: 100%;
      border-radius: 7px;
    }.content {
      display: block;
      color: white;
      position: relative;
      text-align: center;
      overflow: auto;
      h3 {
        margin: 10px 0;
        color: red
      }
      .flag {
        width: 50px
      }
    }
  }.cs_card:hover .background {
    opacity: 0.3;
  }
</style>