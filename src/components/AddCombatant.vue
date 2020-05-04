<template>
  <div>
    <div class="row" v-if="!displayForm">
      <div class="col s12">
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
      <form class="col" v-on:submit.prevent="addCombatant">
        <div class="row">
          <div class="input-field col s12">
            <input id="name" type="text" v-model="name" />
            <label for="name">name</label>
          </div>
        </div>
        <div class="row">
          <div class="input-field col s6">
            <input id="hp" type="number" v-model.number="hp" />
            <label for="hp">hit points</label>
          </div>
          <div class="input-field col s6">
            <input id="ac" type="number" v-model.number="ac" />
            <label for="ac">armor class</label>
          </div>
        </div>
        <div class="row">
          <div class="input-field col s6">
            <input id="init" type="number" v-model.number="initiative" />
            <label for="init">initiative</label>
          </div>
          <div class="input-field col s6">
            <input id="pp" type="number" v-model.number="pp" />
            <label for="pp">passive perception</label>
          </div>
        </div>
        <input type="hidden" id="type" name="type" :value="isNpc" />
        <div class="row">
          <div class="col s6">
            <button
              class="btn-small btn-block"
              type="submit"
              name="add"
              :class="isNpc ? 'red' : 'blue'"
            >
              <i class="tiny material-icons left">check</i> ok
            </button>
          </div>
          <div class="col s6">
            <button
              type="submit"
              class="btn-small btn-block amber darken-1"
              @click="displayForm = !displayForm"
              name="cancel"
            >
              <i class="material-icons left">clear</i> cancel
            </button>
          </div>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "AddCombatantComponent",
  data: function() {
    return this.init();
  },
  methods: {
    addCombatant() {
      const name = this.name;
      const hp = this.hp;
      const initiative = this.initiative;
      const ac = this.ac;
      const pp = this.pp;
      const isNpc = this.isNpc;
      this.$emit("add-combatant", {
        name,
        hp,
        initiative,
        ac,
        pp,
        isNpc
      });
      this.reset();
    },
    init() {
      return {
        name: "",
        hp: "",
        initiative: "",
        ac: "",
        pp: "",
        isNpc: false,
        displayForm: false
      };
    },
    reset() {
      this.name = this.init().name;
      this.hp = this.init().hp;
      this.initiative = this.init().initiative;
      this.ac = this.init().ac;
      this.pp = this.init().pp;
    }
  }
};
</script>

<style scoped>
.btn-block {
  width: 100%;
}
</style>
