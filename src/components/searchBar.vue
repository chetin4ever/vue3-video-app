<template>
  <h1>search bar</h1>
  <h2>{{ searchQuery }}</h2>
  <input type="text" v-model="searchQuery" @input="onInputChange" />
</template>

<script>
import { computed, ref } from "vue";
export default {
  setup(_, { emit }) {
    const searchQuery = ref("");
    console.log("helo");
    function onInputChange() {
      emit("search", this.searchQuery);
    }

    return { searchQuery, onInputChange };
  },
};
</script>

<style>
</style>