<template>
  <div :id="id" class="cs_card">
    <img class="background" :src="srcPost" alt="poster">
    <div class="content">
      <div>
        <h4>Titolo:</h4><span>{{ title }}</span>
      </div>
      <div>
        <h4>Titolo Originale:</h4><span>{{ original_title }}</span>
      </div>
      <div>
        <h4>Lingua Originale:</h4><img v-if="hasFlag" class="flag" :src="srcFlag" :alt="'flag '+language">
        <span v-else>{{ language }}</span>
      </div>
      <div>
        <h4>Valutazione:</h4>
        <svg v-for="(star , i) in maxRating" :key="i" xmlns="http://www.w3.org/2000/svg" width="16" height="16" :fill="isYellowStar(i)" class="bi bi-star-fill" viewBox="0 0 16 16">
          <path d="M3.612 15.443c-.386.198-.824-.149-.746-.592l.83-4.73L.173 6.765c-.329-.314-.158-.888.283-.95l4.898-.696L7.538.792c.197-.39.73-.39.927 0l2.184 4.327 4.898.696c.441.062.612.636.282.95l-3.522 3.356.83 4.73c.078.443-.36.79-.746.592L8 13.187l-4.389 2.256z"/>
        </svg>
      </div>
      <div>
        <h4>Overview:</h4>
        <span>{{ overview }}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SingleCardProduct',
  props: {
    id: Number,
    title: String,
    original_title: String,
    language: String,
    vote: Number,
    poster: String,
    overview: String,
  },
  data() {
    return {
      maxRating: 5,
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
    isYellowStar(i) {
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
    background-color: black;
    border-radius: 7px;
    overflow: hidden;
    cursor: pointer;
    .background {
      position: absolute;
      z-index: 0;
      top: 0;
      bottom: 0;
      height: 100%;
      max-width: 100%;
      border-radius: 7px;
      transition: opacity 0.4s;
    }.content {
      height: 100%;
      display: block;
      color: white;
      position: relative;
      padding: 25px;
      transform: translateX(-100%);
      transition: transform 0.6s;
      overflow: auto;
      h4 {
        margin: 10px 0;
        color: red;
        display: inline-block;
      }
      .flag {
        width: 50px
      }
    }
  }.cs_card:hover .background {
    opacity: 0.3;
  }
  .cs_card:hover .content {
    transform: translateX(0%);
  }
</style>