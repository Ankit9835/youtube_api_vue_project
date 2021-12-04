<template>
    <div>
       <SearchBar @termChange="onTermChange"></SearchBar>
       <VideoDetail :video="selectedVideo" />
       <VideoList @videoSelect="onVideoSelect" :videos="videos"></VideoList>
      
    </div>
</template>

<script>
    import axios from 'axios';
    import SearchBar from './components/SearchBar.vue';
    import VideoDetail from './components/VideoDetail.vue';
    import VideoList from './components/VideoList.vue';
    const API_KEY = 'AIzaSyDW27T6OdeomeV83V4sZ6-Y6k9NzTDYgSw';

    export default{
        name: 'App',
        components:{
            SearchBar,
            VideoList,
            VideoDetail,
        },
        data(){
            return { videos: [], selectedVideo: null };
        },
        methods:{
            onVideoSelect(video){
                //console.log(video);
                this.selectedVideo = video;
            },
            onTermChange: function(searchTerm){
                axios.get('https://www.googleapis.com/youtube/v3/search', {
                    params:{
                        key: API_KEY,
                        type:'video',
                        part:'snippet',
                        q:searchTerm
                    }
                }).then(response => {
                    this.videos = response.data.items
                });
            }
        }
    }

</script>
