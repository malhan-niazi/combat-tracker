<template>
  <tr>
    <td>
      <div class="">
        <a
          href
          @click.prevent="updateSelection"
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
    index: Number
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
</style>
