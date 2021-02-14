<template>
  <div>
    <!-- <input type="text" v-model="searchQuery" @input="onInputChange" /> -->
    <input type="text" v-model="searchQuery" @keypress.enter="onInputChange" />
  </div>
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

<style scoped>
input {
  width: 75%;
}
div {
  text-align: center;
  margin: 20px;
}
</style>