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
      <div class="d-flex flex-column justify-content-around">
        <span
          class="badge"
          :class="isNpc ? 'badge-danger' : 'badge-primary'"
        >{{ isNpc ? 'fill out monster details' : 'fill out hero details' }}</span>
      </div>
      <form class="margin" v-on:submit.prevent="addCombatant">
        <div class="form-group row">
          <label for="name" class="col-lg-4 col-form-label">name</label>
          <div class="col-lg-8">
            <input type="text" class="form-control" id="name" v-model="name" />
          </div>
        </div>
        <div class="form-group row">
          <label for="hp" class="col-lg-7 col-form-label">hit points</label>
          <div class="col-lg-5">
            <input type="number" class="form-control" id="hp" v-model.number="hp" />
          </div>
        </div>
        <div class="form-group row">
          <label for="ac" class="col-lg-7 col-form-label">armor class</label>
          <div class="col-lg-5">
            <input type="number" class="form-control" id="ac" v-model.number="ac" />
          </div>
        </div>
        <div class="form-group row">
          <label for="pp" class="col-lg-7 col-form-label">initiative</label>
          <div class="col-lg-5">
            <input type="number" class="form-control" id="initiative" v-model.number="initiative" />
          </div>
        </div>
        <div class="form-group row">
          <label for="pp" class="col-lg-7 col-form-label">passive perception</label>
          <div class="col-lg-5">
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
</style>
