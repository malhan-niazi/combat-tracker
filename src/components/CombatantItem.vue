<template>
  <div>
    <div>
      <a
        href
        @click.prevent="updateSelection"
        class="name"
        :class="combatant.isNpc ? 'npc' : 'player'"
      >
        {{ combatant.name }}
      </a>
    </div>
    <div class="">
      <input
        type="number"
        id="hit-points"
        v-model.number="combatant.hitPoints"
        class=""
      />
      <span for="maxHitPoints">/{{ maxHitPoints }}</span>
    </div>
    <div class="">
      <input
        type="number"
        id="armor-class"
        v-model.number="combatant.armorClass"
        class=""
      />
    </div>
    <div class="">
      <input
        type="number"
        id="passive-perception"
        v-model.number="combatant.passivePerception"
        class=""
      />
    </div>
    <div class="">
      <input
        type="number"
        id="initiative"
        v-model.number="combatant.initiative"
        class=""
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
</style>
