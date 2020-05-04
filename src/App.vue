<template>
  <div id="app">
    <div class="container-fluid">
      <header-component />
      <div class="row">
        <div class="col s12 m4 l3">
          <add-combatant @add-combatant="add" />
        </div>
        <div class="col s12 m4 l4">
          <combatant-list v-bind:combatants="combatants" />
        </div>
        <div class="col s12 m4 l5">
          <!-- <time-converter /> -->
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// import TimeConverter from "./components/TimeConverter.vue";
import HeaderComponent from "./components/Header.vue";
import AddCombatant from "./components/AddCombatant.vue";
import CombatantList from "./components/CombatantList.vue";

export default {
  name: "App",
  components: {
    // TimeConverter,
    HeaderComponent,
    AddCombatant,
    CombatantList
  },
  data: function() {
    return {
      combatants: [
        {
          name: "human",
          hitPoints: 24,
          armorClass: 14,
          initiative: 12,
          passivePerception: 14,
          isNpc: false
        },
        {
          name: "dwarf",
          hitPoints: 32,
          armorClass: 15,
          initiative: 13,
          passivePerception: 10,
          isNpc: false
        },
        {
          name: "elf",
          hitPoints: 20,
          armorClass: 17,
          initiative: 18,
          passivePerception: 14,
          isNpc: false
        },
        {
          name: "dragon",
          hitPoints: 86,
          armorClass: 18,
          initiative: 14,
          passivePerception: 18,
          isNpc: true
        }
      ]
    };
  },
  methods: {
    add(combatant) {
      this.combatants.push(combatant);
    }
  }
};
</script>

<style>
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
