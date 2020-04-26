<template>
  <div id="app">
    <div class="container-fluid">
      <div class="row">
        <div class="col">
          <header-component />
        </div>
      </div>
      <div class="row">
        <div class="col-md">
          <add-combatant @add-combatant="add" />
        </div>
        <div class="col-md">
          <combatant-list v-bind:combatants="combatants" />
        </div>
        <div class="col-md">
          <time-converter />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import TimeConverter from "./components/TimeConverter.vue";
import HeaderComponent from "./components/Header.vue";
import AddCombatant from "./components/AddCombatantComponent.vue";
import CombatantList from "./components/CombatantList.vue";

export default {
  name: "App",
  components: {
    TimeConverter,
    HeaderComponent,
    AddCombatant,
    CombatantList
  },
  data: function() {
    return {
      combatants: [
        {
          name: "test1",
          hp: "20",
          ac: "11",
          pp: "14",
          isNpc: false
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
  font-family: serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
.col,
.col-md {
  border: 1px solid #8295a8;
}
div h3 {
  text-align: left;
}
</style>
