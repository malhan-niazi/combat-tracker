<template>
  <div class="row">
    <div class="col s12 m6 l6">
      <combatant-list
        v-bind:combatants="combatants"
        @update-selection="updateSelection"
        @hide-detail="showCombatantDetail = false"
      />
    </div>
    <div class="col s12 m6 l6">
      <h5>combatant detail</h5>
      <combatant-detail v-if="showCombatantDetail" v-bind:combatant="combatants[currentIndex]" />
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
    CombatantDetail
  },
  props: {
    combatants: Array
  },
  data() {
    return {
      currentIndex: 0,
      showCombatantDetail: false
    };
  },
  methods: {
    updateSelection(index, showDetail) {
      this.currentIndex = index;
      this.showCombatantDetail = showDetail;
    }
  }
};
</script>

<style>
</style>