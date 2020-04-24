<template>
  <div id="app">
    <div class="container">
      <div class="row">
        <div class="col">
          <HeaderComponent />
        </div>
      </div>
      <div class="row">
        <div class="col-md">
          COL 1
        </div>
        <div class="col-md">
          COL 2
        </div>
        <div class="col-md">
          COL 3
          <TimeConverter />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import TimeConverter from './components/TimeConverter.vue';
import HeaderComponent from './components/HeaderComponent.vue';

export default {
  name: 'App',
  components: {
    TimeConverter,
    HeaderComponent,
  },
};
</script>

<style>
#app {
  font-family: sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
.col,
.col-md {
  border: 1px dotted #2c3e50;
}
div h3 {
  text-align: left;
}
</style>
