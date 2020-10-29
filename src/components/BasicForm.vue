<template>
  <div class="input-form">
    <form v-on:submit.prevent>
      <div class="input-field-container margin">
        <label for="name">Name</label>
        <input id="name" type="text" v-model="name" />
      </div>
      <div class="input-field-container margin">
        <label for="hitPoints">Hit Points</label>
        <input id="hitPoints" type="number" v-model.number="hitPoints" />
      </div>
      <div class="input-field-container margin">
        <label for="armorClass">Armor Class</label>
        <input id="armorClass" type="number" v-model.number="armorClass" />
      </div>
      <div class="input-field-container margin">
        <label for="init">Initiative</label>
        <input id="init" type="number" v-model.number="initiative" />
      </div>
      <div class="input-field-container margin">
        <label for="passivePerception">Passive Perception</label>
        <input
          id="passivePerception"
          type="number"
          v-model.number="passivePerception"
        />
      </div>
      <div class="input-field-buttons">
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
  name: "BasicForm",
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
      this.$emit("add-combatant", {
        name,
        hitPoints,
        initiative,
        armorClass,
        passivePerception,
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
      };
    },
    reset() {
      this.name = this.init().name;
      this.hitPoints = this.init().hitPoints;
      this.initiative = this.init().initiative;
      this.armorClass = this.init().armorClass;
      this.passivePerception = this.init().passivePerception;
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
  width: 100%;
}
</style>