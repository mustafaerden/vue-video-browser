<template>
  <div class="container">
    <SearchBar @termChange="onTermChange"></SearchBar>
    <div class="row">
      <div class="col-md-8">
        <VideoDetail :videoDetail="videoDetail"></VideoDetail>
      </div>
      <div class="col-md-4">
        <!-- child component e props gönderme v-bind ile oluyor -->
        <VideoList :videos="videos" @videoSelect="onVideoSelect"></VideoList>
        <!-- <VideoList v-bind:videos="videos"></VideoList> -->
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import SearchBar from "@/components/SearchBar";
import VideoList from "@/components/VideoList";
import VideoDetail from "@/components/VideoDetail";
const API_KEY = "YOUTUBE_API_KEY";
export default {
  name: "App",
  components: { SearchBar, VideoList, VideoDetail },
  data() {
    return {
      videos: [],
      videoDetail: null
    };
  },
  methods: {
    onTermChange(searchTerm) {
      axios
        .get("https://www.googleapis.com/youtube/v3/search", {
          params: {
            key: API_KEY,
            type: "video",
            part: "snippet",
            q: searchTerm
          }
        })
        // .then(response => console.log(response.data.items));
        .then(response => (this.videos = response.data.items))
        .catch(err => console.log(err));
    },
    onVideoSelect(video) {
      this.videoDetail = video;
    }
  }
};
</script>
