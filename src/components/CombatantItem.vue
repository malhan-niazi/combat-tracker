<template>
  <div class="combatant-items">
    <div class="">
      <a href @click.prevent="updateSelection">{{ combatant.name }}</a>
    </div>
    <div class="hp-field">
      <input
        type="number"
        id="hitPoints"
        v-model.number="combatant.hitPoints"
        class="field-value"
      />
      <label for="maxHitPoints">/{{ maxHitPoints }}</label>
    </div>
    <div>
      <input
        type="number"
        id="armorClass"
        v-model.number="combatant.armorClass"
        class="field-value"
      />
    </div>
    <div>
      <input
        type="number"
        id="passivePerception"
        v-model.number="combatant.passivePerception"
        class="field-value"
      />
    </div>
    <div>
      <input
        type="number"
        id="initiative"
        v-model.number="combatant.initiative"
        class="field-value"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: "CombatantItem",
  props: {
    combatant: Object,
    index: Number,
  },
  data() {
    return {
      maxHitPoints: this.combatant.hitPoints,
    };
  },
  methods: {
    updateSelection() {
      const index = this.index;
      const showDetail = true;
      this.$emit("update-selection", index, showDetail);
    },
  },
};
</script>

<style lang="css" scoped>
.combatant-items {
  display: grid;
  grid-template-columns: repeat(5, minmax(0, 1fr));
}
.field-value {
  box-sizing: border-box;
  width: 100%;
}
.hp-field {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
}
</style>
