<template>
  <div id="app">
    <h1>Different components layout using same Renderless component</h1>
    <tagInputOnlyEnter v-model="tags" style="margin-bottom: 2rem" />
  </div>
</template>

<script>
import tagInputOnlyEnter from "@/components/tagInputOnlyEnter.vue";

export default {
  name: "App",
  components: {
    tagInputOnlyEnter,
  },
  data() {
    return {
      tags: ["Design", "Testing"],
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
