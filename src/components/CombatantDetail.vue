<template>
  <div>
    <div class="stacked">
      <div class="">
        <b>Detail</b>
      </div>
      <div class="">
        <b>Name</b>
        <div class="name" :class="combatant.isNpc ? 'npc' : 'player'">
          {{ combatant.name }}
        </div>
      </div>
      <div class="">
        <b>Size</b>
        <div>{{ size }}</div>
      </div>
      <div class="">
        <b>Hit Points</b>
        <div>
          <input
            class=""
            type="number"
            id="hitPoints"
            v-model.number="combatant.hitPoints"
          />
        </div>
      </div>
      <div class="">
        <b>Armor Class</b>
        <div>
          <input
            class=""
            type="number"
            id="armorClass"
            v-model.number="combatant.armorClass"
          />
        </div>
      </div>
      <div class="">
        <b>Perception</b>
        <div>
          <input
            class=""
            type="number"
            id="passivePerception"
            v-model.number="combatant.passivePerception"
          />
        </div>
      </div>
      <div class="">
        <b>Initiative</b>
        <div>
          <input
            class=""
            type="number"
            id="initiative"
            v-model.number="combatant.initiative"
          />
        </div>
      </div>
      <div v-if="combatant.speed" class="">
        <b>Speed</b>
        <div>
          <input
            class=""
            type="number"
            id="speed"
            v-model.number="combatant.speed"
          />
        </div>
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
        case "tn":
          return "tiny";
        case "sm":
          return "small";
        case "md":
          return "medium";
        case "lg":
          return "large";
        case "hg":
          return "huge";
        case "gr":
          return "gargantuan";
        default:
          return "whoa";
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