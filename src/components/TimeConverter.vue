<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <input v-model="value" type="text" placeholder="Value" />
    <br />
    <input type="radio" id="hour" value="hr" v-model="type" />
    <label for="hour">hour(s)</label>
    <input type="radio" id="minute" value="min" v-model="type" />
    <label for="minute">minute(s)</label>
    <input type="radio" id="second" value="sec" v-model="type" />
    <label for="second">second(s)</label>
    <input type="radio" id="round" value="round" v-model="type" />
    <label for="round">round(s)</label>
    <input type="radio" id="turn" value="turn" v-model="type" />
    <label for="turn">turn(s)</label>
    <p>value is: {{ value }}</p>
    <p>type is: {{ type }}</p>
    <p></p>
  </div>
</template>

<script>
export default {
  name: "TimeConverter",
  props: {
    msg: String
  },
  data: function() {
    return {
      value: "",
      type: "",
      unit: "seconds"
    };
  },
  computed: {}
};
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>