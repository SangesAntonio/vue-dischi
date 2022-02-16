<template>
  <div id="app">
    <Header :genres="genres" @getOption="getResult" />
    <Main :artists="artists" :isLoaded="isLoaded" :resultGen="resultGen" />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";
import axios from "axios";

export default {
  name: "App",

  components: {
    Header,
    Main,
  },
  data() {
    return {
      artists: [],
      genres: [],
      isLoaded: false,
      resultGen: "",
    };
  },
  methods: {
    getResult(value) {
      return (this.resultGen = value);
    },
    getGenres() {
      this.genres = [];
      return this.artists.forEach((artist) => {
        const { genre } = artist;
        if (!this.genres.includes(genre)) this.genres.push(genre);
      });
    },
    getApi() {
      this.isLoaded = true;
      axios
        .get("https://flynn.boolean.careers/exercises/api/array/music")
        .then((res) => {
          this.artists = res.data.response;
          this.isLoaded = false;
          this.getGenres();
        });
    },
  },
  computed: {
    filtredArray() {
      return this.artists.filter((artist) => {
        if (artist.genre.includes(this.getResult)) {
          return true;
        }
        return false;
      });
    },
  },

  mounted() {
    this.getApi();
  },
};
</script>

<style lang="scss">
@import "./assets/scss/style.scss";
</style>
