<template>
<div class="cs-card  text-center p-2">
    <div class="p-2 cs-container">
        <img :src="image" alt="">
        <h2>{{album}}</h2>
        <p class=" mt-3 mb-0">{{artist}}</p>
        <p>{{year}}</p>
    </div>
</div>
</template>

<script>
export default {
    name: 'CardArtist',
    props:['album', 'artist', 'year', 'image'],
}
</script>

<style scoped lang='scss'>
.cs-card{
    width: 20%;
    height: 400px;
    color: white;
    .cs-container{
        height: 100%;
        background-color: rgba(67, 85, 134, 0.938);
        img{
            min-width: 90%;
            min-height: auto;
        }
        p{
            color: rgb(175, 172, 172);
        }
    }

}
</style>