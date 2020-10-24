<template>
  <div id="combatant-list" class="combatant-list">
    <div id="combatant-headers" class="combatant-headers">
      <div>Name</div>
      <div>Hit Points</div>
      <div>Armor Class</div>
      <div>Perception</div>
      <div @click="sortDescending">Initiative</div>
    </div>
    <combatant-item
      v-for="(combatant, index) in combatants"
      :key="index"
      v-bind:combatant="combatant"
      v-bind:index="index"
      @update-selection="updateSelection"
    ></combatant-item>
  </div>
</template>

<script>
import CombatantItem from "./CombatantItem.vue";

export default {
  name: "combatant-list",
  components: {
    CombatantItem,
  },
  data() {
    return {
      showDetail: false,
      currentIndex: 0,
    };
  },
  props: ["combatants"],
  methods: {
    sortDescending() {
      this.combatants.sort((a, b) => (a.initiative < b.initiative ? 1 : -1));
      this.$emit("hide-detail", {});
    },
    updateSelection(index, showDetail) {
      this.currentIndex = index;
      this.showDetail = showDetail;
      this.$emit("update-selection", index, showDetail);
    },
  },
};
</script>

<style lang="css" scoped>
.combatant-headers {
  display: grid;
  grid-template-columns: repeat(5, minmax(0, 1fr));
}
</style>
