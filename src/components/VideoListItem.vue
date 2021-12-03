<template>
    <li class="list-group-item media">
         <img :src="thumbnailUrl" @click="onVideoSelect">
         <div class = "media-body">
            {{ video.snippet.title }}
         </div> 
    </li>
</template>

<script>
    export default {
        name:'VideoListItem',
        computed: {
            thumbnailUrl(){
                return this.video.snippet.thumbnails.default.url
            }
        },
        methods:{
            onVideoSelect(){

            }
        },
        props: ['video']
    }
</script>

<style scoped>
    li{
        display: flex;
        cursor: pointer;
        margin-left: 2px;
    }
    li:hover{
        background-color:#eee;
    }

</style>
