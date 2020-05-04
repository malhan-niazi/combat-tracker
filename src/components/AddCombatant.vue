<template>
  <div>
    <div class="row">
      <div class="col">
        <h5>add combatants</h5>
      </div>
    </div>
    <div v-if="!displayForm">
      <div class="row">
        <div class="col">
          <button
            type="button"
            class="btn-small"
            @click="
              displayForm = !displayForm;
              isNpc = false;
            "
          >
            add character
          </button>
        </div>
      </div>
      <div class="row">
        <div class="col">
          <button
            type="button"
            class="btn-small"
            @click="
              displayForm = !displayForm;
              isNpc = true;
            "
          >
            add monster
          </button>
        </div>
      </div>
    </div>
    <!-- monster / character input form -->
    <div class="row" v-if="displayForm">
      <div class="col">
        <div class="row">
          <div class="col">
            <span :class="isNpc ? 'badge-danger' : 'badge-primary'">{{
              isNpc ? 'fill out monster details' : 'fill out hero details'
            }}</span>
          </div>
        </div>
        <div class="row">
          <div class="col">
            <form v-on:submit.prevent="addCombatant">
              <div class="row">
                <div class="input-field col">
                  <input id="name" type="text" v-model="name" />
                  <label for="name">name</label>
                </div>
              </div>
              <div class="row">
                <div class="input-field col">
                  <input id="hp" type="text" v-model.number="hp" />
                  <label for="hp">hit points</label>
                </div>
              </div>
              <div class="">
                <label for="ac" class="">armor class</label>
                <div class="">
                  <input type="number" class="" id="ac" v-model.number="ac" />
                </div>
              </div>
              <div class="">
                <label for="pp" class="">initiative</label>
                <div class="">
                  <input
                    type="number"
                    class=""
                    id="initiative"
                    v-model.number="initiative"
                  />
                </div>
              </div>
              <div class="">
                <label for="pp" class="m">passive perception</label>
                <div class="">
                  <input type="number" class="" id="pp" v-model.number="pp" />
                </div>
              </div>
              <input type="hidden" id="type" name="type" :value="isNpc" />
              <div class="">
                <div class="">
                  <button type="submit" class="btn-small">add</button>
                </div>
                <div class="">
                  <button
                    type="submit"
                    class="btn-small"
                    @click="displayForm = !displayForm"
                  >
                    cancel
                  </button>
                </div>
              </div>
            </form>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'AddCombatantComponent',
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
      this.$emit('add-combatant', {
        name,
        hp,
        initiative,
        ac,
        pp,
        isNpc,
      });
      this.reset();
    },
    init() {
      return {
        name: '',
        hp: '',
        initiative: '',
        ac: '',
        pp: '',
        isNpc: false,
        displayForm: false,
      };
    },
    reset() {
      this.name = this.init().name;
      this.hp = this.init().hp;
      this.initiative = this.init().initiative;
      this.ac = this.init().ac;
      this.pp = this.init().pp;
    },
  },
};
</script>

<style scoped></style>
