<template>
  <div class="lists">
    <div class="container cs-cards pt-5 d-flex">
      <div class="text-center w-100" v-if="isLoaded">
        <h1>CARICAMENTO IN CORSO..</h1>
      </div>

      <CardArtist
        v-else
        v-for="(artist, index) in artists"
        :key="index"
        :album="artist.title"
        :artist="artist.author"
        :year="artist.year"
        :image="artist.poster"
      />
    </div>
  </div>
</template>

<script>
import CardArtist from "./CardArtist.vue";
export default {
  name: "Main",
  props: {
    artists: Array,
    isLoaded: { type: String, required: false },
    selected: String,
  },
  components: {
    CardArtist,
  },
  data() {
    return {
      filtredArtists: [],
    };
  },
  computed: {},
};
</script>

<style scoped lang='scss'>
.lists {
  width: 100%;
  height: 100vh;
  background-color: rgba(20, 53, 141, 0.938);

  .cs-cards {
    flex-wrap: wrap;
  }
}
</style>