<template lang="pug">
  #app.main 
    tower(
      v-for="tower in towers"
      :key="tower.id"
      :tower="tower"
    )
</template>

<script>
import axios from "axios";
import Tower from "./components/Tower";

export default {
  components: {
    Tower
  },

  data() {
    return {
      towers: []
    };
  },

  created() {
    axios
      .get("https://next.json-generator.com/api/json/get/VkDa46Kpv")
      .then(response => (this.towers = response.data));
  }
};
</script>

<style lang="scss">
html,
body {
  padding: 0;
  margin: 0;
  height: 100%;
  width: 100%;
}
.main {
  background: #2d2d32;
  display: flex;
  align-items: center;
  justify-content: space-around;
  height: 100%;
}
</style>
