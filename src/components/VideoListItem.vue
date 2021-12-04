<template>
    <li class="list-group-item media">
        <div @click="onVideoSelect">
         <img :src="thumbnailUrl">
         <div class = "media-body">
            {{ video.snippet.title }}
         </div>
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
                this.$emit('videoSelect', this.video);
            }
        },
        props: ['video']
    }
</script>

<style scoped>
div{
   display: flex; 
}
    li{
        display: flex;
        cursor: pointer;
        margin-left: 2px;
    }
    li:hover{
        background-color:#eee;
    }

</style>
