<template>
  <div class="">
    <div class="">
      <div class="center-text">
        <b>Combatant List</b>
      </div>
      <combatant-list
        v-bind:combatants="combatants"
        @update-selection="updateSelection"
        @hide-detail="showCombatantDetail = false"
        class="margin-bottom-section"
      />
    </div>
    <div v-if="showCombatantDetail">
      <combatant-detail v-bind:combatant="combatants[currentIndex]" />
    </div>
  </div>
</template>

<script>
import CombatantList from "./CombatantList";
import CombatantDetail from "./CombatantDetail";

export default {
  name: "CombatantTracker",
  components: {
    CombatantList,
    CombatantDetail,
  },
  props: {
    combatants: Array,
  },
  data() {
    return {
      currentIndex: 0,
      showCombatantDetail: false,
    };
  },
  methods: {
    updateSelection(index, showDetail) {
      this.currentIndex = index;
      this.showCombatantDetail = showDetail;
    },
  },
};
</script>

<style scoped>
</style>