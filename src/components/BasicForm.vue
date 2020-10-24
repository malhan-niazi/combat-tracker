<template>
  <div class="">
    <form class="" v-on:submit.prevent>
      <div class="">
        <div class="">
          <input id="name" type="text" v-model="name" />
          <label for="name">name</label>
        </div>
      </div>
      <div class="">
        <div class="">
          <input id="hitPoints" type="number" v-model.number="hitPoints" />
          <label for="hitPoints">hit points</label>
        </div>
        <div class="">
          <input id="armorClass" type="number" v-model.number="armorClass" />
          <label for="armorClass">armor class</label>
        </div>
      </div>
      <div class="">
        <div class="">
          <input id="init" type="number" v-model.number="initiative" />
          <label for="init">initiative</label>
        </div>
        <div class="">
          <input id="passivePerception" type="number" v-model.number="passivePerception" />
          <label for="passivePerception">passive perception</label>
        </div>
      </div>
      <div class="">
        <div class="">
          <button
            class=""
            type="submit"
            name="add"
            @click="addCombatant"
          >ok
          </button>
        </div>
        <div class="">
          <button
            type="submit"
            class=""
            name="cancel"
            @click="cancel"
          >cancel
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
      const hitPoints = this.hitPoints;
      const initiative = this.initiative;
      const armorClass = this.armorClass;
      const passivePerception = this.passivePerception;
      this.$emit("add-combatant", {
        name,
        hitPoints,
        initiative,
        armorClass,
        passivePerception
      });
      this.reset();
    },
    init() {
      return {
        name: "",
        hitPoints: "",
        initiative: "",
        armorClass: "",
        passivePerception: ""
      };
    },
    reset() {
      this.name = this.init().name;
      this.hitPoints = this.init().hitPoints;
      this.initiative = this.init().initiative;
      this.armorClass = this.init().armorClass;
      this.passivePerception = this.init().passivePerception;
    }
  }
};
</script>

<style scoped>
.btn-block {
  width: 100%;
}
.margin-btm-none {
  margin-bottom: 0;
}
.margin-top-small {
  margin-top: 5px;
}
</style>