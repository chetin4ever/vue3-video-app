<template>
  <div id="nav">
    <h1>hello</h1>
    <search-bar @search="onTermChange" />
  </div>
  <router-view />
</template>
<script>
import searchBar from "./components/searchBar.vue";
import axios from "axios";
const API_KEY = "AIzaSyApmpR5_NE80PE5H_3yChES4STEIYWsRQY";
export default {
  name: "App",
  components: { searchBar },

  setup() {
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
        .then((response) => console.log(response));
    }
    return { onTermChange };
  },
};
</script>

<style>
</style>
