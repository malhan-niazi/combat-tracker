<template>
  <div>
    <div v-if="!displayForm" class="">
      <div class="">
        <b>Add Combatant</b>
        <div class="">
          <div class="">
            <button
              type="button"
              class=""
              @click="
                displayForm = !displayForm;
                isNpc = false;
              "
            >
              Add Player
            </button>
            <button
              type="button"
              class=""
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
    </div>
    <!-- monster / character input form -->
    <div v-if="displayForm" class="">
      <div class="">
        <div>
          Add
          <span>{{ isNpc ? "Monster" : "Character" }}</span>
        </div>
        <label>
          <input type="checkbox" v-model="makeStatBlock" class="" />
          <span>Stat Block</span>
        </label>
      </div>
      <div class="">
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
.btn-block {
  width: 100%;
}
</style>
