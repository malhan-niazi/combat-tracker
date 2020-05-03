<template>
  <div>
    <h5>combatants</h5>
    <div>
      <div class="row">
        <div class="col">name</div>
        <div class="col">hp</div>
        <div class="col">ac</div>
        <div class="col">init</div>
        <div class="col">pp</div>
      </div>
      <div v-for="(combatant, index) in combatants" :key="index">
        <combatant-item v-bind:combatant="combatant"></combatant-item>
      </div>
    </div>
  </div>
</template>

<script>
import CombatantItem from "./CombatantItem.vue";

export default {
  name: "combatant-list",
  components: {
    CombatantItem
  },
  props: ["combatants"]
};
</script>

<style lang="css" scoped>
</style>