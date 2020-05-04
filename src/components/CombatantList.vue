<template>
  <div class="row">
    <table class="col s12">
      <thead>
        <tr>
          <th>Name</th>
          <th>HP</th>
          <th>AC</th>
          <th>Pass. Perc.</th>
          <th @click="sortDesc">
            Init.
            <i class="tiny material-icons right">sort</i>
          </th>
        </tr>
      </thead>
      <tbody>
        <combatant-item
          v-for="(combatant, index) in combatants"
          :key="index"
          v-bind:combatant="combatant"
          v-bind:index="index"
        ></combatant-item>
      </tbody>
    </table>
  </div>
</template>

<script>
import CombatantItem from "./CombatantItem.vue";

export default {
  name: "combatant-list",
  components: {
    CombatantItem
  },
  props: ["combatants"],
  methods: {
    sortDesc() {
      this.combatants.sort((a, b) => (a.initiative < b.initiative ? 1 : -1));
    }
  }
};
</script>

<style lang="css" scoped></style>
