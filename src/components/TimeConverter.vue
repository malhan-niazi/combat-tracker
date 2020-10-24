<template>
  <div class="">
    <div class="">
      <h5>{{ msg }}</h5>
      <div class="">
        <input
          type="number"
          id="value"
          placeholder="Value"
          v-model.number="input"
        />
        <small id="valueHelp">Enter a value, and select the corresponding unit of time.</small>
      </div>
      <div class="">
        <select class="" v-model="selection">
          <option value disabled selected>select time unit</option>
          <option>hour</option>
          <option>minute</option>
          <option>second</option>
          <option>round</option>
        </select>
      </div>
      <!-- <p v-if="conversion">{{ conversion }}</p> -->
      <p v-if="rounds">{{ rounds }}</p>
    </div>
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
  data: function() {
    return {
      msg: "time converter",
      input: "",
      selection: SELECTION_HOUR
    };
  },
  computed: {
    seconds: function() {
      return this.toSeconds();
    },
    conversion: function() {
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

<style scoped></style>
