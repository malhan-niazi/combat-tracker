<template>
  <div>
    <div v-if="!displayForm" class="">
      <div class="add-combatant-form">
        <b>Add Combatant</b>
        <div class="add-combatant-form-buttons">
          <button
            type="button"
            class="button"
            @click="
              displayForm = !displayForm;
              isNpc = false;
            "
          >
            Add Player
          </button>
          <button
            type="button"
            class="button"
            @click="
              displayForm = !displayForm;
              isNpc = true;
            "
          >
            Add Monster
          </button>
        </div>
      </div>
    </div>
    <!-- monster / character input form -->
    <div v-if="displayForm" class="">
      <div>
        Add
        <span>{{ isNpc ? "Monster" : "Character" }}</span>
      </div>
      <input type="checkbox" v-model="makeStatBlock" class="stat-block-check" />
      <label for="stat-block-check">Create Stat Block</label>
      <stat-block-form
        v-if="makeStatBlock"
        class=""
        @add-combatant="addCombatant"
        @cancel-add="displayForm = !displayForm"
        v-bind:isNpc="isNpc"
      ></stat-block-form>
      <basic-form
        v-if="!makeStatBlock"
        class=""
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
.add-combatant-form-buttons {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
}
</style>
