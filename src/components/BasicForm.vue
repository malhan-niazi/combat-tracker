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
      const hp = this.hp;
      const initiative = this.initiative;
      const ac = this.ac;
      const pp = this.pp;
      this.$emit("add-combatant", {
        name,
        hp,
        initiative,
        ac,
        pp
      });
      this.reset();
    },
    init() {
      return {
        name: "",
        hp: "",
        initiative: "",
        ac: "",
        pp: ""
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

<style>
.btn-block {
  width: 100%;
}
</style>