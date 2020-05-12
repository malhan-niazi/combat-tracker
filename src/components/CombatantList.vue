<template>
  <div class="row">
    <div class="col">
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
                v-bind:currentAction="currentAction"
                @update-selection="updateSelection"
                :class="
              showDetail && index === currentIndex ? 'grey lighten-4' : ''
            "
              ></combatant-item>
            </tbody>
          </table>
        </div>
      </div>
      <div class="row">
        <div class="col left">
          <a class="waves-effect waves-light btn" @click="prev">
            <i class="material-icons left">arrow_back</i>prev
          </a>
        </div>
        <div class="col right">
          <a class="waves-effect waves-light btn" @click="next">
            <i class="material-icons right">arrow_forward</i>next
          </a>
        </div>
      </div>
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
      currentIndex: 0,
      currentAction: 0
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
    },
    next() {
      this.showDetail = true;
      if (this.currentAction < this.combatants.length) this.currentAction++;
      if (this.currentAction === this.combatants.length) this.currentAction = 0;
      this.currentIndex = this.currentAction;
      this.$emit("update-selection", this.currentIndex, this.showDetail);
    },
    prev() {
      this.showDetail = true;
      if (this.currentAction >= 0) this.currentAction--;
      if (this.currentAction < 0)
        this.currentAction = this.combatants.length - 1;
      this.currentIndex = this.currentAction;
      this.$emit("update-selection", this.currentIndex, this.showDetail);
    }
  }
};
</script>

<style lang="css" scoped></style>
