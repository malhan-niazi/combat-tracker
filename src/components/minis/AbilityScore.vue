<template>
  <div class="grid col-3x">
    <b>{{ ability }}</b>
    <input type="number" :id="'ability' + ability" v-model.number="score" />
    <span :class="modifierColor">{{ modifier }}</span>
  </div>
</template>

<script>
export default {
  // TODO fix mutating prop error.
  name: "AbilityScoreComponent",
  props: {
    score: Number,
    ability: String,
  },
  computed: {
    modifier() {
      return Math.floor((this.score - 10) / 2);
    },
    modifierColor() {
      return this.modifier < 0 ? "red" : this.modifier === 0 ? "gray" : "green";
    },
  },
};
</script>

<style>
.grid {
  display: grid;
}
.col-3x {
  grid-template-columns: repeat(3, minmax(0, 1fr));
}
.red {
  color: red;
}
.green {
  color: green;
}
.gray {
  color: gray;
}
</style>