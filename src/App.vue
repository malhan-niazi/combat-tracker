<template>
  <div id="app" class="content">
    <header-component />
    <add-combatant @add-combatant="add" />
    <combatant-tracker v-bind:combatants="combatants" />
    <!-- <time-converter /> -->
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
          size: "m",
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
          size: "m",
          speed: 20,
          abilityScore: {
            str: 14,
            dex: 12,
            con: 16,
            int: 8,
            wis: 12,
            cha: 9,
          },
        },
        {
          name: "elf",
          hitPoints: 20,
          armorClass: 17,
          initiative: 18,
          passivePerception: 14,
          isNpc: false,
          size: "m",
          speed: 30,
          abilityScore: {
            str: 8,
            dex: 17,
            con: 10,
            int: 12,
            wis: 12,
            cha: 13,
          },
        },
        {
          name: "dragon",
          hitPoints: 86,
          armorClass: 18,
          initiative: 14,
          passivePerception: 18,
          isNpc: true,
          size: "l",
          speed: 30,
          abilityScore: {
            str: 20,
            dex: 17,
            con: 23,
            int: 15,
            wis: 19,
            cha: 19,
          },
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
body {
  background-color: #121214;
  color: #af9a91;
}
input {
  background-color: #af9a91;
  color: #121214;
}
button {
  background-color: #4e4b61;
  color: #af9a91;
}
body,
input,
button {
  font-family: "DM Mono", monospace;
  font-size: 16px;
}
button {
  font-size: 0.75rem;
}
input {
  font-size: 0.5rem;
}
.content {
  padding-right: 15px;
  padding-left: 15px;
  margin-right: auto;
  margin-left: auto;
  max-width: 750px;
}
</style>
