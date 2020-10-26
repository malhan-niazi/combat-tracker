<template>
  <div class="grid col-5x">
    <div href @click.prevent="updateSelection" class="center__vertical">
      {{ combatant.name }}
    </div>
    <div class="grid col-2x">
      <input
        type="number"
        id="hitPoints"
        v-model.number="combatant.hitPoints"
        class="field-value"
      />
      <span for="maxHitPoints" class="center__vertical input-static-text"
        >/{{ maxHitPoints }}</span
      >
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
.field-value {
  box-sizing: border-box;
  width: 100%;
}
.grid {
  display: grid;
}
.col-2x {
  grid-template-columns: repeat(2, minmax(0, 1fr));
}
.col-5x {
  grid-template-columns: repeat(5, minmax(0, 1fr));
}
.center__vertical {
  display: flex;
  align-items: center;
}
.input-static-text {
  font-size: 0.85rem;
}
</style>
