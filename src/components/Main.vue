<template>
  <div class=" lists">
      <div class="container cs-cards pt-5 d-flex ">

      <CardArtist v-for='(artist, index) in artists' 
      :key='index'
      :album='artist.title'
      :artist='artist.author'
      :year='artist.year'
      :image='artist.poster'/>
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

<style scoped lang='scss'>
.lists{
    width: 100%;
    height: 100vh;
    background-color: rgba(20, 53, 141, 0.938);

    .cs-cards{
        flex-wrap: wrap;
    }
    
}


</style>