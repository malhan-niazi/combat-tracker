<template>
  <div id="app">
    <TimeConverter />
    <div class="alert alert-success alert-dismissible fade show" role="alert">
      With Bootstrap!
      <button
        type="button"
        class="close"
        data-dismiss="alert"
        aria-label="Close"
      >
        <span aria-hidden="true">&times;</span>
      </button>
    </div>
  </div>
</template>

<script>
import TimeConverter from "./components/TimeConverter.vue";

export default {
  name: "App",
  components: {
    TimeConverter
  }
};
</script>

<style>
#app {
  font-family: sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
