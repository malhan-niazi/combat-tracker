<template>
  <div>
    <div class="row" v-if="!displayForm">
      <div class="col s12">
        <h5>add combatant</h5>
        <div class="row">
          <div class="col s6">
            <button
              type="button"
              class="btn btn-block blue"
              @click="
                displayForm = !displayForm;
                isNpc = false;
              "
            >
              <i class="tiny material-icons left">add</i> player
            </button>
          </div>
          <div class="col s6">
            <button
              type="button"
              class="btn btn-block red"
              @click="
                displayForm = !displayForm;
                isNpc = true;
              "
            >
              <i class="tiny material-icons left">add</i>monster
            </button>
          </div>
        </div>
      </div>
    </div>
    <!-- monster / character input form -->
    <div class="row" v-if="displayForm">
      <div class="col">
        <h5 col s12>
          add
          <span :class="isNpc ? 'red-text' : 'blue-text'">{{ isNpc ? 'monster' : 'character' }}</span>
        </h5>
        <label>
          <input type="checkbox" class="filled-in" v-model="makeStatBlock" />
          <span>Stat Block</span>
        </label>
      </div>
      <div class="row">
        <stat-block-form
          v-if="makeStatBlock"
          class="col s12"
          @add-combatant="addCombatant"
          @cancel-add="displayForm = !displayForm"
          v-bind:isNpc="isNpc"
        ></stat-block-form>
        <basic-form
          v-if="!makeStatBlock"
          class="col s12"
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
    StatBlockForm
  },
  data: function() {
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
        makeStatBlock: false
      };
    }
  }
};
</script>

<style scoped>
.btn-block {
  width: 100%;
}
</style>
