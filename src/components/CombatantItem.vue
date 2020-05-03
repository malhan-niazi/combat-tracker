<template>
  <tr>
    <th scope="row" :class="combatant.isNpc ? 'villain' : 'hero'">{{combatant.name}}</th>
    <td>
      <input type="number" class="form-control form-control-sm" id="hp" v-model="combatant.hp" />
    </td>
    <td>
      <input type="number" class="form-control form-control-sm" id="ac" v-model="combatant.ac" />
    </td>
    <td>
      <input
        type="number"
        class="form-control form-control-sm"
        id="init"
        v-model="combatant.initiative"
      />
    </td>
    <td>
      <input type="number" class="form-control form-control-sm" id="pp" v-model="combatant.pp" />
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
.hero {
  color: #7ed6df;
}
.villain {
  color: #eb4d4b;
}
</style>