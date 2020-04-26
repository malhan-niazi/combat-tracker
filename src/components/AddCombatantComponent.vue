<template>
  <div>
    <div>
      <h5>add combatants</h5>
    </div>
    <div v-if="!displayForm" class="d-flex flex-column justify-content-around">
      <div>
        <button
          type="button"
          class="btn btn-primary btn-block"
          @click="displayForm = !displayForm; isNpc = false"
        >add character</button>
      </div>
      <div class="d-flex flex-column justify-content-around">
        <span class="badge badge-light">or</span>
      </div>
      <div>
        <button
          type="button"
          class="btn btn-danger btn-block"
          @click="displayForm = !displayForm; isNpc = true"
        >add monster</button>
      </div>
    </div>
    <!-- monster / character input form -->
    <div v-if="displayForm">
      <form class="margin" v-on:submit.prevent="addCombatant">
        <div class="form-group row">
          <label for="name" class="col-md-4 col-form-label">name</label>
          <div class="col-md-8">
            <input type="text" class="form-control" id="name" v-model="name" />
          </div>
        </div>
        <div class="form-group row">
          <label for="hp" class="col-md-8 col-form-label">hit points</label>
          <div class="col-md-4">
            <input type="number" class="form-control" id="hp" v-model.number="hp" />
          </div>
        </div>
        <div class="form-group row">
          <label for="ac" class="col-md-8 col-form-label">armor class</label>
          <div class="col-md-4">
            <input type="number" class="form-control" id="ac" v-model.number="ac" />
          </div>
        </div>
        <div class="form-group row">
          <label for="pp" class="col-md-8 col-form-label">passive perception</label>
          <div class="col-md-4">
            <input type="number" class="form-control" id="pp" v-model.number="pp" />
          </div>
        </div>
        <input type="hidden" id="type" name="type" :value="isNpc" />
        <div class="form-group row">
          <div class="col-12">
            <button type="submit" class="btn btn-primary btn-block">add</button>
          </div>
          <div class="col-12">
            <button
              type="submit"
              class="btn btn-warning btn-block"
              @click="displayForm = !displayForm"
            >cancel</button>
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
      const ac = this.ac;
      const pp = this.pp;
      const isNpc = this.isNpc;
      this.$emit("add-combatant", {
        name,
        hp,
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
        ac: "",
        pp: "",
        isNpc: false,
        displayForm: false
      };
    },
    reset() {
      this.name = this.init().name;
      this.hp = this.init().hp;
      this.ac = this.init().ac;
      this.pp = this.init().pp;
      this.isNpc = this.init().isNpc;
    }
  }
};
</script>

<style scoped>
</style>
