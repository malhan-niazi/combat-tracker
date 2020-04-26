<template>
  <div>
    <h5>combatants</h5>
    <div>
      <ul>
        <li v-for="(combatant, index) in combatants" :key="index">{{ combatant }}</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "combatant-list",
  props: ["combatants"]
};
</script>

<style>
</style>