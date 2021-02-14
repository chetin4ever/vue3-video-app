<template>
  <div class="container">
    <search-bar @search="onTermChange" />
    <div class="row">
      <video-detail :video="selectedVideo" />
      <video-list :videos="videos" @videoSelect="onVideoSelect" />
    </div>
  </div>
  <router-view />
</template>
<script>
import searchBar from "./components/searchBar.vue";
import axios from "axios";
import VideoList from "./components/VideoList.vue";
import { reactive, ref } from "vue";
import VideoDetail from "./components/VideoDetail.vue";
const API_KEY = "YOUR_KEY";
export default {
  name: "App",
  components: { searchBar, VideoList, VideoDetail },

  setup() {
    const videos = ref([]);
    const selectedVideo = ref(null);
    function onVideoSelect(video) {
      console.log("app", video);
      selectedVideo.value = video;
      console.log("afterchnge", selectedVideo.value);
    }
    function onTermChange(serachTerm) {
      axios
        .get("https://www.googleapis.com/youtube/v3/search", {
          params: {
            key: API_KEY,
            type: "video",
            part: "snippet",
            q: serachTerm,
          },
        })
        .then((response) => {
          // console.log(response);
          videos.value = response.data.items;
          console.log(videos.value);
        });
    }
    return { onTermChange, videos, onVideoSelect, selectedVideo };
  },
};
</script>

<style>
</style>
