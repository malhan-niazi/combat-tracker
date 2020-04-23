<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <input v-model.number="input" type="number" placeholder="Value" />
    <br />
    <input type="radio" id="hour" value="hour" v-model="selection" />
    <label for="hour">hour(s)</label>
    <input type="radio" id="minute" value="minute" v-model="selection" />
    <label for="minute">minute(s)</label>
    <input type="radio" id="second" value="second" v-model="selection" />
    <label for="second">second(s)</label>
    <input type="radio" id="round" value="round" v-model="selection" />
    <label for="round">round(s)</label>
    <p v-if="format">{{ format }}</p>
    <p v-if="rounds">{{ rounds }}</p>
    <p></p>
  </div>
</template>

<script>
const SELECTION_HOUR = "hour";
const SELECTION_MINUTE = "minute";
const SELECTION_ROUND = "round";
const FIXED_TIME_UNIT = 60;
const SECONDS_PER_ROUND = 6;
const DECIMAL_PLACES = 2;

export default {
  name: "TimeConverter",
  props: {
    msg: String
  },
  data: function() {
    return {
      input: "",
      selection: SELECTION_HOUR
    };
  },
  computed: {
    seconds: function() {
      return this.toSeconds();
    },
    format: function() {
      const seconds = this.seconds % FIXED_TIME_UNIT;
      let minutes = Math.floor(this.seconds / FIXED_TIME_UNIT);
      const hours = Math.floor(minutes / FIXED_TIME_UNIT);
      minutes = minutes % FIXED_TIME_UNIT;
      return `${hours} hour(s), ${minutes} minute(s) and ${seconds} second(s)`;
    },
    rounds: function() {
      let fixed = 0;
      if (this.seconds % SECONDS_PER_ROUND > 0) {
        fixed = (this.seconds / SECONDS_PER_ROUND).toFixed(DECIMAL_PLACES);
      } else {
        fixed = this.seconds / SECONDS_PER_ROUND;
      }
      return `${fixed} round(s)`;
    }
  },
  methods: {
    toSeconds() {
      switch (this.selection) {
        case SELECTION_HOUR: {
          return this.input * FIXED_TIME_UNIT * FIXED_TIME_UNIT;
        }
        case SELECTION_MINUTE: {
          return this.input * FIXED_TIME_UNIT;
        }
        case SELECTION_ROUND: {
          return this.input * SECONDS_PER_ROUND;
        }
        default:
          return Math.floor(this.input);
      }
    }
  }
};
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
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