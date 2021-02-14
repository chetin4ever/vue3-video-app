<template>
  <!-- <iframe src="https://www.youtube.com/embed/hdI2bqOjy3c" /> -->
  <div v-if="video" class="col-md-8 col-lg-8">
    <div class="embed-responsive embed-responsive-16by9">
      <iframe class="embed-responsive-item" :src="videoUrl" />
      <!-- <iframe src="https://www.youtube.com/embed/hdI2bqOjy3c" /> -->
    </div>
    <div class="viedo-details">
      <h4>{{ video.snippet.title }}</h4>
      <p>{{ video.snippet.description }}</p>
    </div>
  </div>
</template>

<script>
import { computed, onMounted, onUpdated } from "vue";
export default {
  props: {
    video: Object,
  },

  setup(props) {
    onUpdated(() => {
      console.log("v detail", props.video);
    });
    const videoUrl = computed(() => {
      //es 2015 syntax
      // const videoId=props.video.id.videoId;
      //es6 destructuring the data
      const { videoId } = props.video.id;
      console.log(videoId);
      //   return "https://www.youtube.com/embed/" + videoId;
      return `https://www.youtube.com/embed/${videoId}`;
    });

    return { videoUrl };
  },
};
</script >

<style scoped>
.viedo-details {
  margin-top: 10px;
  padding: 10px;
  border: 1px solid #ddd;
}
</style>