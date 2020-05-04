<template>
  <div class="row">
    <form class="col s12" v-on:submit.prevent>
      <div class="row">
        <div class="input-field col s12">
          <input id="name" type="text" v-model="name" />
          <label for="name">name</label>
        </div>
      </div>
      <div class="row">
        <div class="input-field col s6">
          <input id="hitPoints" type="number" v-model.number="hitPoints" />
          <label for="hitPoints">hit points</label>
        </div>
        <div class="input-field col s6">
          <input id="armorClass" type="number" v-model.number="armorClass" />
          <label for="armorClass">armor class</label>
        </div>
      </div>
      <div class="row">
        <div class="input-field col s6">
          <input id="init" type="number" v-model.number="initiative" />
          <label for="init">initiative</label>
        </div>
        <div class="input-field col s6">
          <input id="passivePerception" type="number" v-model.number="passivePerception" />
          <label for="passivePerception">passive perception</label>
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
  name: "BasicForm",
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
      this.$emit("add-combatant", {
        name,
        hitPoints,
        initiative,
        armorClass,
        passivePerception
      });
      this.reset();
    },
    init() {
      return {
        name: "",
        hitPoints: "",
        initiative: "",
        armorClass: "",
        passivePerception: ""
      };
    },
    reset() {
      this.name = this.init().name;
      this.hitPoints = this.init().hitPoints;
      this.initiative = this.init().initiative;
      this.armorClass = this.init().armorClass;
      this.passivePerception = this.init().passivePerception;
    }
  }
};
</script>

<style>
.btn-block {
  width: 100%;
}
</style>