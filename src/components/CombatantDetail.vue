<template>
  <div class="">
    <div class="">
      <b>Name</b>
      <div>{{ combatant.name }}</div>
    </div>
    <div class="">
      <b>Size</b>
      <div>{{ combatant.name }}</div>
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
    <div class="">
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
    <div v-if="combatant.abilityScore" class="ability-scores">
      <div class="ability-score-item">
        <b>STR</b>
        <input
          class=""
          type="number"
          id="str"
          v-model.number="combatant.abilityScore.str"
        />
        <span>{{ modifier(combatant.abilityScore.str) }}</span>
      </div>
      <div class="ability-score-item">
        <b>DEX</b>
        <input
          class=""
          type="number"
          id="dex"
          v-model.number="combatant.abilityScore.dex"
        />
        <span>{{ modifier(combatant.abilityScore.dex) }}</span>
      </div>
      <div class="ability-score-item">
        <b>CON</b>
        <input
          class=""
          type="number"
          id="con"
          v-model.number="combatant.abilityScore.con"
        />
        <span>{{ modifier(combatant.abilityScore.con) }}</span>
      </div>
      <div class="ability-score-item">
        <b>INT</b>
        <input
          class=""
          type="number"
          id="int"
          v-model.number="combatant.abilityScore.int"
        />
        <span>{{ modifier(combatant.abilityScore.int) }}</span>
      </div>
      <div class="ability-score-item">
        <b>WIS</b>
        <input
          class=""
          type="number"
          id="wis"
          v-model.number="combatant.abilityScore.wis"
        />
        <span>{{ modifier(combatant.abilityScore.wis) }}</span>
      </div>
      <div class="ability-score-item">
        <b>CHA</b>
        <input
          class=""
          type="number"
          id="cha"
          v-model.number="combatant.abilityScore.cha"
        />
        <span>{{ modifier(combatant.abilityScore.cha) }}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CombatantDetail",
  props: {
    combatant: Object,
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
      return modifier < 0
        ? "red-text"
        : modifier === 0
        ? "grey-text"
        : "green-text";
    },
  },
};
</script>

<style scoped>
.ability-scores {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
}
.ability-score-item {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
}
</style>