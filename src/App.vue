<template>
  <div id="app" class="content">
    <header-component />
    <div class="monospace">
      <div class="" style="margin-bottom: 1rem">
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
          size: "md",
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
          size: "md",
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
          size: "lg",
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
body,
input,
button {
  font-family: "DM Mono", monospace;
  font-size: 16px;
}
button {
  font-size: 0.75rem;
  border: none;
  display: block;
  margin: 0.5rem;
  width: 100%;
  border-radius: 0.25rem;
}
input {
  font-size: 0.5rem;
  box-sizing: border-box;
  width: 100%;
  border: 1px dotted lightgray;
  border-radius: 0.25rem;
}
.content {
  padding-right: 15px;
  padding-left: 15px;
  margin-right: auto;
  margin-left: auto;
  max-width: 750px;
}
</style>
