<template>
  <ul class="list-group col-md-4 col-lg-4">
    <video-list-item
      v-for="video in videos"
      :key="video.etag"
      :singleVideo="video"
      @videoSelect="onVideoSelect"
    >
    </video-list-item>
  </ul>
</template>

<script>
import VideoListItem from "./VideoListItem.vue";
export default {
  components: { VideoListItem },
  name: "videoList",
  props: {
    videos: Array,
  },
  setup(_, { emit }) {
    function onVideoSelect(video) {
      emit("videoSelect", video);
      console.log("fromvideolist", video);
    }
    return {
      onVideoSelect,
    };
  },
};
</script>

<style>
</style>