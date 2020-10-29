<template>
  <div class="input-form">
    <form v-on:submit.prevent>
      <div>
        <label for="name">Name</label>
        <input id="name" type="text" v-model="name" />
      </div>
      <div>
        <label for="hit-points">Hit Points</label>
        <input id="hit-points" type="number" v-model.number="hitPoints" />
      </div>
      <div>
        <label for="armor-class">Armor Class</label>
        <input id="armor-class" type="number" v-model.number="armorClass" />
      </div>
      <div>
        <label for="initiative">Initiative</label>
        <input id="initiative" type="number" v-model.number="initiative" />
      </div>
      <div>
        <label for="passive-perception">Passive Perception</label>
        <input
          id="passive-perception"
          type="number"
          v-model.number="passivePerception"
        />
      </div>
      <div>
        <button type="submit" name="add" @click="addCombatant">ok</button>
        <button type="submit" name="cancel" @click="cancel">cancel</button>
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
</style>