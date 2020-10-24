<template>
  <div id="app" class="content">
    <header-component />
    <div class="monospace">
      <div class="">
        <add-combatant @add-combatant="add" />
      </div>
      <div class="">
        <combatant-tracker v-bind:combatants="combatants" />
      </div>
      <div class="">
        <!-- <time-converter /> -->
      </div>
    </div>
  </div>
</template>

<script>
// import TimeConverter from "./components/TimeConverter.vue";
import HeaderComponent from "./components/Header";
import AddCombatant from "./components/AddCombatant";
import CombatantTracker from "./components/CombatantTracker";

export default {
  name: "App",
  components: {
    // TimeConverter,
    HeaderComponent,
    AddCombatant,
    CombatantTracker,
  },
  data: function () {
    return {
      currentSelection: "",
      combatants: [
        {
          name: "human",
          hitPoints: 24,
          initiative: 12,
          armorClass: 14,
          passivePerception: 13,
          size: "md",
          speed: 30,
          abilityScore: {
            str: 12,
            dex: 15,
            con: 14,
            int: 8,
            wis: 10,
            cha: 16,
          },
        },
        {
          name: "dwarf",
          hitPoints: 32,
          armorClass: 15,
          initiative: 13,
          passivePerception: 10,
          isNpc: false,
        },
        {
          name: "elf",
          hitPoints: 20,
          armorClass: 17,
          initiative: 18,
          passivePerception: 14,
          isNpc: false,
        },
        {
          name: "dragon",
          hitPoints: 86,
          armorClass: 18,
          initiative: 14,
          passivePerception: 18,
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
.monospace {
  font-family: monospace;
  font-size: 1rem;
}
button {
  font-family: monospace;
  font-size: 0.75rem;
  width: 100%;
}
a {
  font-family: monospace;
  font-size: 0.75rem;
}
input,
select {
  font-family: monospace;
  font-size: 0.75rem;
}
div {
  /* outline: 1px solid lightgray; */
}
.content {
  padding-right: 15px;
  padding-left: 15px;
  margin-right: auto;
  margin-left: auto;
  max-width: 750px;
}
</style>
