<template>
  <tr>
    <th :class="combatant.isNpc ? 'villain' : 'hero'">{{ combatant.name }}</th>
    <td>
      <input type="number" id="hp" v-model="combatant.hp" />
    </td>
    <td>
      <input type="number" id="ac" v-model="combatant.ac" />
    </td>
    <td>
      <input type="number" id="init" v-model="combatant.initiative" />
    </td>
    <td>
      <input type="number" id="pp" v-model="combatant.pp" />
    </td>
  </tr>
</template>

<script>
export default {
  name: 'CombatantItem',
  props: ['combatant'],
};
</script>

<style lang="css" scoped>
.hero {
  color: #7ed6df;
}
.villain {
  color: #eb4d4b;
}
</style>
