<template>
  <div class="container">
    <SearchBar @termChange="onTermChange"></SearchBar>
    <div class="row">
    <videoDetail :video="selectedVideo"/>
    <video-list @videoSelect='onVideoSelect' v-bind:videos="videos"></video-list>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import SearchBar from "./components/SearchBar.vue";
import VideoList from "./components/videoList.vue";
import VideoDetail from './components/VideoDetail.vue';

const API_KEY = "AIzaSyCNu8QUJFO2VYP3wt7QuPH1IgfJmQsvh2E";

export default {
  components: { SearchBar, VideoList, VideoDetail },
  data() {
    return { videos: [], selectedVideo: null };
  },
  name: "App",
  methods: {
    onVideoSelect(video) {
      console.log(video)
      this.selectedVideo = video
    },
    onTermChange(searchTerm) {
      console.log(searchTerm)
      axios
        .get("https://www.googleapis.com/youtube/v3/search", {
          params: {
            type: "video",
            part: "snippet",
            key: API_KEY,
            q: searchTerm
          },
        })
        .then((response) => {
          this.videos = response.data.items;
          console.log(this.videos);
        });
    },
  },
};
</script>

<style scoped>

</style>
