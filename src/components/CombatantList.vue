<template>
  <div class="row">
    <div class="col">
      <table>
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
            :class="
              showDetail && index === currentIndex ? 'grey lighten-4' : ''
            "
          ></combatant-item>
        </tbody>
      </table>
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
  data() {
    return {
      showDetail: false,
      currentIndex: 0
    };
  },
  props: ["combatants"],
  methods: {
    sortDescending() {
      this.combatants.sort((a, b) => (a.initiative < b.initiative ? 1 : -1));
      this.$emit("hide-detail", false);
    },
    updateSelection(index, showDetail) {
      this.currentIndex = index;
      this.showDetail = showDetail;
      this.$emit("update-selection", index, showDetail);
    }
  }
};
</script>

<style lang="css" scoped></style>
