<template>
  <div id="app">
    <div class="container-fluid">
      <header-component />
      <div class="row">
        <div class="col s4 m3 l2">
          <add-combatant @add-combatant="add" />
        </div>
        <div class="col s4 m3 l4">
          <combatant-list v-bind:combatants="combatants" />
        </div>
        <div class="col s4 m6 l6">
          <!-- <time-converter /> -->
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// import TimeConverter from "./components/TimeConverter.vue";
import HeaderComponent from './components/Header.vue';
import AddCombatant from './components/AddCombatant.vue';
import CombatantList from './components/CombatantList.vue';

export default {
  name: 'App',
  components: {
    // TimeConverter,
    HeaderComponent,
    AddCombatant,
    CombatantList,
  },
  data: function() {
    return {
      combatants: [
        {
          name: 'jack',
          hp: 2,
          ac: 2,
          initiative: 2,
          pp: 2,
          isNpc: false,
        },
        {
          name: 'jill',
          hp: 4,
          ac: 4,
          initiative: 4,
          pp: 4,
          isNpc: false,
        },
        {
          name: 'john',
          hp: 3,
          ac: 3,
          initiative: 3,
          pp: 3,
          isNpc: true,
        },
        {
          name: 'jen',
          hp: 1,
          ac: 1,
          initiative: 1,
          pp: 1,
          isNpc: true,
        },
      ],
    };
  },
  methods: {
    add(combatant) {
      this.combatants.push(combatant);
    },
  },
};
</script>

<style>
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
