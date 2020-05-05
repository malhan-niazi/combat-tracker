<template>
  <div class="row">
    <table class="col s12">
      <thead>
        <tr>
          <th>Name</th>
          <th>HP</th>
          <th>AC</th>
          <th>Pass. Perc.</th>
          <th @click="sortDescending">
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
          @update-selection="updateSelection"
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
    sortDescending() {
      this.combatants.sort((a, b) => (a.initiative < b.initiative ? 1 : -1));
    },
    updateSelection(index, showDetail) {
      this.$emit("update-selection", index, showDetail);
    }
  }
};
</script>

<style lang="css" scoped></style>
