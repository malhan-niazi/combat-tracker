<template>
  <div class="hello">
    <h3>{{ msg }}</h3>
    <div class="form-group">
      <input
        type="number"
        class="form-control"
        id="value"
        aria-describedby="value"
        placeholder="Value"
        v-model.number="input"
      />
      <small id="valueHelp" class="form-text text-muted"
        >Enter a value, and select the corresponding unit of time.</small
      >
    </div>
    <div class="form-group">
      <label for="unitSelection">Select Time-Unit</label>
      <select class="form-control" id="unitSelection" v-model="selection">
        <option>hour</option>
        <option>minute</option>
        <option>second</option>
        <option>round</option>
      </select>
    </div>
    <p v-if="conversion">{{ conversion }}</p>
    <p v-if="rounds">{{ rounds }}</p>
  </div>
</template>

<script>
const SELECTION_HOUR = 'hour';
const SELECTION_MINUTE = 'minute';
const SELECTION_ROUND = 'round';
const FIXED_TIME_UNIT = 60;
const SECONDS_PER_ROUND = 6;
const DECIMAL_PLACES = 2;

export default {
  name: 'TimeConverter',
  data: function() {
    return {
      msg: 'Time Converter',
      input: '',
      selection: SELECTION_HOUR,
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
    },
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
    },
  },
};
</script>

<style scoped></style>
