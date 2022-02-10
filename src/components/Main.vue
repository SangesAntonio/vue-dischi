<template>
  <div class=" lists">
      <div class="container pt-5">

      <CardArtist v-for='(artist, index) in artists' 
      :key='index'
      :album='artist.title'
      :artist='artist.author'
      :year='artist.year'/>
      </div>
  </div>
</template>

<script>
import CardArtist from './CardArtist.vue';
import axios from 'axios';
export default {
    name: 'Main',
    components:{
        CardArtist,
    },
    data(){
        return{
          artists:[],
        }
    },
    mounted(){
        axios.get('https://flynn.boolean.careers/exercises/api/array/music').then(res => {
            this.artists= res.data.response;
        });
    },
}
</script>

<style>
.lists{
    width: 100%;
    height: 100vh;
    background-color: rgba(37, 55, 104, 0.938);
}


</style>