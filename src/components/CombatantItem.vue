<template>
  <tr>
    <td>
      <input
        type="text"
        id="name"
        v-model="combatant.name"
        :class="combatant.isNpc ? 'red-text' : 'blue-text'"
      />
    </td>
    <td>
      <input type="number" id="hp" v-model.number="combatant.hp" />
    </td>
    <td>
      <input type="number" id="ac" v-model.number="combatant.ac" />
    </td>
    <td>
      <input type="number" id="init" v-model.number="combatant.initiative" />
    </td>
    <td>
      <input type="number" id="pp" v-model.number="combatant.pp" />
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
