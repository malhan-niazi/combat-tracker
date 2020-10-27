<template>
  <div>
    <a
      href
      @click.prevent="updateSelection"
      class="name"
      :class="combatant.isNpc ? 'npc' : 'player'"
    >
      {{ combatant.name }}
    </a>
    <div class="row">
      <input
        type="number"
        id="hitPoints"
        v-model.number="combatant.hitPoints"
        class="input-hp"
      />
      <span for="maxHitPoints" class="input-static-text"
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
.row {
  display: flex;
  flex-direction: row;
  align-items: flex-start;
}
.input-hp {
  max-width: 3.5rem;
}
.name {
  display: block;
  margin: auto auto auto 0rem;
  text-decoration: none;
}
.npc {
  color: indianred;
}
.player {
  color: steelblue;
}
.input-static-text {
  font-size: 0.85rem;
  margin: auto 0.5rem;
}
</style>
