<template>
  <div>
    <table>
      <thead>
        <tr>
          <th>name</th>
          <th>hp</th>
          <th>ac</th>
          <th>perc</th>
          <th @click="sortDesc">
            init
            <i class="tiny material-icons">sort</i>
          </th>
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
import CombatantItem from './CombatantItem.vue';

export default {
  name: 'combatant-list',
  components: {
    CombatantItem,
  },
  props: ['combatants'],
  methods: {
    sortDesc() {
      this.combatants.sort((a, b) => (a.initiative < b.initiative ? 1 : -1));
    },
  },
};
</script>

<style lang="css" scoped></style>
