<template>
  <div>
    <div v-if="!displayForm">
      <button
        type="button"
        @click="
          displayForm = !displayForm;
          isNpc = false;
        "
      >
        Add Player
      </button>
      <button
        type="button"
        @click="
          displayForm = !displayForm;
          isNpc = true;
        "
      >
        Add Monster
      </button>
    </div>
    <!-- monster / character input form -->
    <div v-if="displayForm">
      <div>
        Add
        <span>{{ isNpc ? "Monster" : "Character" }}</span>
      </div>
      <div>
        <input type="checkbox" v-model="makeStatBlock" />
        <label for="stat-block-check">Create Stat Block</label>
      </div>
      <stat-block-form
        v-if="makeStatBlock"
        @add-combatant="addCombatant"
        @cancel-add="displayForm = !displayForm"
        v-bind:isNpc="isNpc"
      ></stat-block-form>
      <basic-form
        v-if="!makeStatBlock"
        @add-combatant="addCombatant"
        @cancel-add="displayForm = !displayForm"
        v-bind:isNpc="isNpc"
      ></basic-form>
    </div>
  </div>
</template>

<script>
import BasicForm from "./BasicForm";
import StatBlockForm from "./StatBlockForm";

export default {
  name: "AddCombatantComponent",
  components: {
    BasicForm,
    StatBlockForm,
  },
  data: function () {
    return this.init();
  },
  methods: {
    addCombatant(combatant) {
      combatant.isNpc = this.isNpc;
      this.$emit("add-combatant", combatant);
    },
    init() {
      return {
        isNpc: false,
        displayForm: false,
        makeStatBlock: false,
      };
    },
  },
};
</script>

<style scoped>
</style>
