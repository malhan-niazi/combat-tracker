<template>
  <div class="row">
    <form class="col s12" v-on:submit.prevent>
      <div class="row margin-btm-none margin-top-small">
        <div class="input-field col s12 margin-btm-none margin-top-small">
          <input id="name" type="text" v-model="name" />
          <label for="name">name</label>
        </div>
      </div>
      <div class="row margin-btm-none margin-top-small">
        <div class="input-field col s6 margin-btm-none margin-top-small">
          <input id="hitPoints" type="number" v-model.number="hitPoints" />
          <label for="hitPoints">hit points</label>
        </div>
        <div class="input-field col s6 margin-btm-none margin-top-small">
          <input id="armorClass" type="number" v-model.number="armorClass" />
          <label for="armorClass">armor class</label>
        </div>
      </div>
      <div class="row margin-btm-none margin-top-small">
        <div class="input-field col s6 margin-btm-none margin-top-small">
          <input id="init" type="number" v-model.number="initiative" />
          <label for="init">initiative</label>
        </div>
        <div class="input-field col s6 margin-btm-none margin-top-small">
          <input id="passivePerception" type="number" v-model.number="passivePerception" />
          <label for="passivePerception">passive perception</label>
        </div>
      </div>
      <div class="row margin-btm-none margin-top-small">
        <div class="input-field col s6 margin-btm-none margin-top-small">
          <select class="browser-default" v-model="size">
            <option value disabled selected>select size</option>
            <option value="ti">tiny</option>
            <option value="sm">small</option>
            <option value="md">medium</option>
            <option value="lg">large</option>
            <option value="hu">huge</option>
            <option value="ga">gargantuan</option>
          </select>
        </div>
        <div class="input-field col s6 margin-btm-none margin-top-small">
          <input id="speed" type="number" v-model.number="speed" />
          <label for="speed">speed</label>
        </div>
      </div>
      <div class="row margin-top-small">
        <div class="col s12 m12 l6">
          <div class="input-field col s4 m4 l4 margin-btm-none margin-top-small">
            <input id="str" type="number" v-model.number="abilityScore.str" />
            <label for="instrit">str</label>
          </div>
          <div class="input-field col s4 m4 l4 margin-btm-none margin-top-small">
            <input id="dex" type="number" v-model.number="abilityScore.dex" />
            <label for="dex">dex</label>
          </div>
          <div class="input-field col s4 m4 l4 margin-btm-none margin-top-small">
            <input id="con" type="number" v-model.number="abilityScore.con" />
            <label for="con">con</label>
          </div>
        </div>
        <div class="col s12 m12 l6">
          <div class="input-field col s4 m4 l4 margin-btm-none margin-top-small">
            <input id="int" type="number" v-model.number="abilityScore.int" />
            <label for="int">int</label>
          </div>
          <div class="input-field col s4 m4 l4 margin-btm-none margin-top-small">
            <input id="wis" type="number" v-model.number="abilityScore.wis" />
            <label for="wis">wis</label>
          </div>
          <div class="input-field col s4 m4 l4 margin-btm-none margin-top-small">
            <input id="cha" type="number" v-model.number="abilityScore.cha" />
            <label for="cha">cha</label>
          </div>
        </div>
      </div>
      <div class="row">
        <div class="col s6">
          <button
            class="btn-small btn-block"
            type="submit"
            name="add"
            :class="isNpc ? 'red' : 'blue'"
            @click="addCombatant"
          >
            <i class="tiny material-icons left">check</i> ok
          </button>
        </div>
        <div class="col s6">
          <button
            type="submit"
            class="btn-small btn-block amber darken-1"
            name="cancel"
            @click="cancel"
          >
            <i class="material-icons left">clear</i> cancel
          </button>
        </div>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: "StatBlockForm",
  props: {
    isNpc: Boolean
  },
  data: function() {
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
        abilityScore
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
          cha: ""
        }
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
    }
  }
};
</script>

<style scoped>
.btn-block {
  width: 100%;
}
.margin-btm-none {
  margin-bottom: 0;
}
.margin-top-small {
  margin-top: 5px;
}
</style>