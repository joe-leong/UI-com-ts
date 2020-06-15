<template>
  <div id="app" :style="`--font-color-tint:blue`">
    <Home></Home>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import Home from "@/home.vue";

@Component({
  components: {
    Home
  }
})
export default class App extends Vue {}
</script>

<style lang="stylus">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
