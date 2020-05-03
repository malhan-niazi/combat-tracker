<template>
  <div>
    <h5>combatants</h5>
    <table class="table table-sm">
      <thead class="thead-dark">
        <tr>
          <th scope="col">name</th>
          <th scope="col">hp</th>
          <th scope="col">ac</th>
          <th scope="col">
            <button class="btn btn-sm btn-block btn-warning" @click="sortByInitiative">init</button>
          </th>
          <th scope="col">perc</th>
        </tr>
      </thead>
      <tbody>
        <combatant-item
          v-for="(combatant, index) in combatants"
          :key="index"
          v-bind:combatant="combatant"
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
  data() {
    return {
      sortDesc: true
    };
  },
  props: ["combatants"],
  methods: {
    sortByInitiative() {
      if (this.sortDesc) {
        this.combatants.sort((a, b) => (a.initiative < b.initiative ? 1 : -1));
      } else {
        this.combatants.sort((a, b) => (a.initiative > b.initiative ? 1 : -1));
      }
      this.sortDesc = !this.sortDesc;
    }
  }
};
</script>

<style lang="css" scoped>
.white {
  color: #fff;
}
.btn-warning {
  background-color: #f6e58d;
  border-color: #f6e58d;
}
</style>