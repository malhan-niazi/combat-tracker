<template>
  <div class="input-form">
    <form class="" v-on:submit.prevent>
      <div class="input-field-container">
        <label for="name">Name</label>
        <input id="name" type="text" v-model="name" />
      </div>
      <div class="input-field-container">
        <label for="hitPoints">Hit Points</label>
        <input id="hitPoints" type="number" v-model.number="hitPoints" />
      </div>
      <div class="input-field-container">
        <label for="armorClass">Armor Class</label>
        <input id="armorClass" type="number" v-model.number="armorClass" />
      </div>
      <div class="input-field-container">
        <label for="init">Initiative</label>
        <input id="init" type="number" v-model.number="initiative" />
      </div>
      <div class="input-field-container">
        <label for="passivePerception">Passive Perception</label>
        <input
          id="passivePerception"
          type="number"
          v-model.number="passivePerception"
        />
      </div>
      <div class="input-field-container">
        <label for="sizeSelect">Select Size</label>
        <select class="">
          <option value="tn" selected>Tiny</option>
          <option value="sm">Small</option>
          <option value="md">Medium</option>
          <option value="lg">Large</option>
          <option value="hu">Huge</option>
          <option value="gr">Gargantuan</option>
        </select>
      </div>
      <div class="input-field-container">
        <label for="speed">Speed</label>
        <input id="speed" type="number" v-model.number="speed" />
      </div>
      <div class="input-field-container">
        <label for="instrit">STR</label>
        <input id="str" type="number" v-model.number="abilityScore.str" />
      </div>
      <div class="input-field-container">
        <label for="dex">DEX</label>
        <input id="dex" type="number" v-model.number="abilityScore.dex" />
      </div>
      <div class="input-field-container">
        <label for="con">CON</label>
        <input id="con" type="number" v-model.number="abilityScore.con" />
      </div>
      <div class="input-field-container">
        <label for="int">INT</label>
        <input id="int" type="number" v-model.number="abilityScore.int" />
      </div>
      <div class="input-field-container">
        <label for="wis">WIS</label>
        <input id="wis" type="number" v-model.number="abilityScore.wis" />
      </div>
      <div class="input-field-container">
        <label for="cha">CHA</label>
        <input id="cha" type="number" v-model.number="abilityScore.cha" />
      </div>
      <div class="input-field-container">
        <button class="" type="submit" name="add" @click="addCombatant">
          ok
        </button>
        <button type="submit" class="" name="cancel" @click="cancel">
          cancel
        </button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: "StatBlockForm",
  props: {
    isNpc: Boolean,
  },
  data: function () {
    return this.init();
  },
  methods: {
    cancel() {
      this.$emit("cancel-add", {});
      this.reset();
    },
    addCombatant() {
      const name = this.name;
      const hitPoints = this.hitPoints;
      const initiative = this.initiative;
      const armorClass = this.armorClass;
      const passivePerception = this.passivePerception;
      const size = this.size;
      const speed = this.speed;
      const abilityScore = this.abilityScore;
      this.$emit("add-combatant", {
        name,
        hitPoints,
        initiative,
        armorClass,
        passivePerception,
        size,
        speed,
        abilityScore,
      });
      this.reset();
    },
    init() {
      return {
        name: "",
        hitPoints: "",
        initiative: "",
        armorClass: "",
        passivePerception: "",
        size: "",
        speed: "",
        abilityScore: {
          str: "",
          dex: "",
          con: "",
          int: "",
          wis: "",
          cha: "",
        },
      };
    },
    reset() {
      this.name = this.init().name;
      this.hitPoints = this.init().hitPoints;
      this.initiative = this.init().initiative;
      this.armorClass = this.init().armorClass;
      this.passivePerception = this.init().passivePerception;
      this.size = this.init().size;
      this.speed = this.init().speed;
      this.abilityScore = this.init().abilityScore;
    },
  },
};
</script>

<style scoped>
.input-form {
  display: grid;
  grid-template-columns: repeat(1, minmax(0, 1fr));
}
.input-field-container {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
}
</style>