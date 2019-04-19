<template>
  <div id="app">
    <ChuckFacts />
  </div>
</template>

<script>
import ChuckFacts from "./components/ChuckFacts.vue";

export default {
  name: "app",
  components: {
    ChuckFacts
  }
};
</script>
<style>
html,
body {
  margin: 0;
  padding: 0;
}
</style>
