<template>
  <tr>
    <td>
      <input
        type="text"
        :id="`${combatant.name}`"
        v-model="combatant.name"
        :class="combatant.isNpc ? 'red-text' : 'blue-text'"
      />
    </td>
    <td>
      <input type="number" id="hitPoints" v-model.number="combatant.hitPoints" />
    </td>
    <td>
      <input type="number" id="armorClass" v-model.number="combatant.armorClass" />
    </td>
    <td>
      <input type="number" id="passivePerception" v-model.number="combatant.passivePerception" />
    </td>
    <td>
      <input type="number" id="initiative" v-model.number="combatant.initiative" />
    </td>
  </tr>
</template>

<script>
export default {
  name: "CombatantItem",
  props: ["combatant"]
};
</script>

<style lang="css" scoped>
</style>
