<template>
  <li class="list-group-item" @click="onVideoSelect">
    <img :src="thumbnailUrl" alt="" />
    <p class="p-2">{{ singleVideo.snippet.title }}</p>
  </li>
</template>
  

<script>
import { computed } from "vue";
export default {
  props: {
    singleVideo: Object,
  },
  setup(props, { emit }) {
    function onVideoSelect() {
      emit("videoSelect", props.singleVideo);
      console.log("singlevvvv", props.singleVideo);
    }

    const thumbnailUrl = computed(() => {
      return props.singleVideo.snippet.thumbnails.default.url;
      // console.log("singlev", singleVideo);
    });

    return { thumbnailUrl, onVideoSelect };
  },
};
</script>

<style scoped>
li {
  display: flex;
  /* flex-flow: column; */
  cursor: pointer;
}
li:hover {
  background-color: #eee;
}
</style>