<template>
  <div id="combatant-list">
    <div id="combatant-list-headers" class="grid col-5x grid-gap-1">
      <div class="center__vertical underline">Name</div>
      <div class="center__vertical underline">Hit Points</div>
      <div class="center__vertical underline">Armor Class</div>
      <div class="center__vertical underline">Perception</div>
      <div @click="sortDescending" class="center__vertical underline">
        Initiative
      </div>
    </div>
    <combatant-item
      v-for="(combatant, index) in combatants"
      :key="index"
      v-bind:combatant="combatant"
      v-bind:index="index"
      @update-selection="updateSelection"
      class="grid col-5x grid-gap-1"
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
.grid {
  display: grid;
}
.col-5x {
  grid-template-columns: repeat(5, minmax(0, 1fr));
}
.grid-gap-1 {
  grid-gap: 5px;
}
.center__vertical {
  display: flex;
  align-items: center;
}
.underline {
  text-decoration: underline;
}
</style>
