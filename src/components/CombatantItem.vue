<template>
  <div class="combatant-items">
    <div class="">
      <a href @click.prevent="updateSelection">{{ combatant.name }}</a>
    </div>
    <div>
      <input
        type="number"
        id="hitPoints"
        v-model.number="combatant.hitPoints"
      />
    </div>
    <div>
      <input
        type="number"
        id="armorClass"
        v-model.number="combatant.armorClass"
      />
    </div>
    <div>
      <input
        type="number"
        id="passivePerception"
        v-model.number="combatant.passivePerception"
      />
    </div>
    <div>
      <input
        type="number"
        id="initiative"
        v-model.number="combatant.initiative"
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
</style>
