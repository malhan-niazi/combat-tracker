<template>
  <tr>
    <td>
      <div v-if="currentAction === index">
        <i class="material-icons right">directions_run</i>
      </div>

      <div class="name-width">
        <a
          href
          @click.prevent="updateSelection"
          :class="[combatant.isNpc ? 'red-text' : 'blue-text', currentAction === index ? 'bold' : '']"
        >{{ combatant.name }}</a>
      </div>
    </td>
    <td>
      <input type="number" id="hitPoints" v-model.number="combatant.hitPoints" />
    </td>
    <td>
      <input type="number" id="armorClass" v-model.number="combatant.armorClass" />
    </td>
    <td>
      <input type="number" id="passivePerception" v-model.number="combatant.passivePerception" />
    </td>
    <td>
      <input type="number" id="initiative" v-model.number="combatant.initiative" />
    </td>
  </tr>
</template>

<script>
export default {
  name: "CombatantItem",
  props: {
    combatant: Object,
    index: Number,
    currentAction: Number
  },
  methods: {
    updateSelection() {
      const index = this.index;
      const showDetail = true;
      this.$emit("update-selection", index, showDetail);
    }
  }
};
</script>

<style lang="css" scoped>
.name-width {
  min-width: 100px;
  max-width: 100%;
}
.bold {
  font-weight: bold;
}
</style>
