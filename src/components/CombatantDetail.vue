<template>
  <div>
    <div class="stacked">
      <div class="">
        <b>Detail</b>
      </div>
      <div class="">
        <b>Name</b>
        <span class="name" :class="combatant.isNpc ? 'npc' : 'player'">
          {{ combatant.name }}
        </span>
      </div>
      <div class="">
        <b>Size</b>
        <span>{{ size }}</span>
      </div>
      <div class="">
        <b>Hit Points</b>
        <input
          type="number"
          id="hit-points"
          v-model.number="combatant.hitPoints"
        />
      </div>
      <div class="">
        <b>Armor Class</b>
        <input
          type="number"
          id="armor-class"
          v-model.number="combatant.armorClass"
        />
      </div>
      <div class="">
        <b>Perception</b>
        <input
          class=""
          type="number"
          id="passive-perception"
          v-model.number="combatant.passivePerception"
        />
      </div>
      <div class="">
        <b>Initiative</b>
        <input
          type="number"
          id="initiative"
          v-model.number="combatant.initiative"
        />
      </div>
      <div v-if="combatant.speed" class="">
        <b>Speed</b>
        <input type="number" id="speed" v-model.number="combatant.speed" />
      </div>
    </div>
    <div v-if="combatant.abilityScore" class="grid col-2x">
      <ability-score
        :score="combatant.abilityScore.str"
        ability="STR"
      ></ability-score>
      <ability-score
        :score="combatant.abilityScore.dex"
        ability="DEX"
      ></ability-score>
      <ability-score
        :score="combatant.abilityScore.con"
        ability="CON"
      ></ability-score>
      <ability-score
        :score="combatant.abilityScore.int"
        ability="INT"
      ></ability-score>
      <ability-score
        :score="combatant.abilityScore.wis"
        ability="WIS"
      ></ability-score>
      <ability-score
        :score="combatant.abilityScore.cha"
        ability="CHA"
      ></ability-score>
    </div>
  </div>
</template>

<script>
import AbilityScore from "./minis/AbilityScore";

export default {
  name: "CombatantDetail",
  props: {
    combatant: Object,
  },
  components: {
    AbilityScore,
  },
  computed: {
    size() {
      switch (this.combatant.size) {
        case "t":
          return "Tiny";
        case "s":
          return "Small";
        case "m":
          return "Medium";
        case "l":
          return "Large";
        case "h":
          return "Huge";
        case "g":
          return "Gargantuan";
        default:
          return "NA";
      }
    },
  },
};
</script>

<style scoped>
.grid {
  display: grid;
  grid-gap: 0.25rem;
}
.col-2x {
  grid-template-columns: repeat(2, minmax(0, 1fr));
}
.stacked {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: center;
}
.npc {
  color: indianred;
}
.player {
  color: steelblue;
}
.name {
  display: block;
  margin: auto auto auto 0rem;
  text-decoration: none;
}
</style>