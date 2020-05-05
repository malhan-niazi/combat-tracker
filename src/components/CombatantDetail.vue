<template>
  <div>
    <div v-if="combatant.name">name: {{ combatant.name }}</div>
    <div v-if="combatant.size">size: {{ combatant.size }}</div>
    <div v-if="combatant.armorClass">ac: {{ combatant.armorClass }}</div>
    <div v-if="combatant.hitPoints">hp: {{ combatant.hitPoints }}</div>
    <div v-if="combatant.passivePerception">passive perception: {{ combatant.passivePerception }}</div>
    <div v-if="combatant.initiative">initiative: {{ combatant.initiative }}</div>
    <div v-if="combatant.speed">speed: {{ combatant.speed }}</div>
    <div v-if="combatant.abilityScore" class="row">
      <div class="col">str: {{ combatant.abilityScore.str }}</div>
      <div class="col">dex: {{ combatant.abilityScore.dex }}</div>
      <div class="col">con: {{ combatant.abilityScore.con }}</div>
      <div class="col">int: {{ combatant.abilityScore.int }}</div>
      <div class="col">wis: {{ combatant.abilityScore.wis }}</div>
      <div class="col">cha: {{ combatant.abilityScore.cha }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CombatantDetail",
  props: {
    combatant: Object
  }
};
</script>

<style>
</style>