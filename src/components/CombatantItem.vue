<template>
  <tr>
    <td>
      <!-- <input
        :id="`${combatant.name}`"
        v-model="combatant.name"
        :class="combatant.isNpc ? 'red-text' : 'blue-text'"
      />-->
      <div
        class="name-width"
        :class="combatant.isNpc ? 'red-text' : 'blue-text'"
      >{{ combatant.name }}</div>
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
.name-width {
  min-width: 100px;
  max-width: 100%;
}
</style>
