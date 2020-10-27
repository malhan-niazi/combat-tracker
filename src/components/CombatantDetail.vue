<template>
  <div class="">
    <div class="">
      <b>Name</b>
      <div>{{ combatant.name }}</div>
    </div>
    <div class="">
      <b>Size</b>
      <div>{{ size }}</div>
    </div>
    <div class="">
      <b>Armor Class</b>
      <div class="">
        <input
          type="number"
          id="armorClass"
          v-model.number="combatant.armorClass"
        />
      </div>
    </div>
    <div class="">
      <b>Hit Points</b>
      <div class="">
        <input
          class=""
          type="number"
          id="hitPoints"
          v-model.number="combatant.hitPoints"
        />
      </div>
    </div>
    <div class="">
      <b>Perception</b>
      <div class="">
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
      <div class="">
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
      <div class="">
        <input
          class=""
          type="number"
          id="speed"
          v-model.number="combatant.speed"
        />
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
  methods: {
    modifier(abilityScore) {
      return Math.floor((abilityScore - 10) / 2);
    },
    modifierColor(modifier) {
      return modifier < 0 ? "red" : modifier === 0 ? "grey" : "green";
    },
  },
};
</script>

<style scoped>
.grid {
  display: grid;
}
.col-2x {
  grid-template-columns: repeat(2, minmax(0, 1fr));
}
.col-3x {
  grid-template-columns: repeat(3, minmax(0, 1fr));
}
.center__vertical {
  display: flex;
  align-items: center;
}
.red {
  color: red;
}
.green {
  color: green;
}
.grey {
  color: gray;
}
</style>