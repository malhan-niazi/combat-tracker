<template>
  <div class="row">
    <div class="col">
      <div class="row margin-bottom-small" v-if="combatant.name">
        <div class="col">
          <div>
            <b>name</b>
          </div>
          <div>{{ combatant.name }}</div>
        </div>
      </div>
      <div class="row margin-bottom-small" v-if="combatant.size">
        <div class="col">
          <div>
            <b>size</b>
          </div>
          <div>{{ size }}</div>
        </div>
      </div>
      <div class="row margin-bottom-small" v-if="combatant.armorClass">
        <div class="col">
          <div>
            <b>armorClass</b>
          </div>
          <input
            class="col s4 m4 l4 margin-btm-none margin-top-small"
            type="number"
            id="armorClass"
            v-model.number="combatant.armorClass"
          />
        </div>
      </div>
      <div class="row margin-bottom-small">
        <div class="col">
          <div>
            <b>hitPoints</b>
          </div>
          <div>
            <input
              class="col s4 m4 l4 margin-btm-none margin-top-small"
              type="number"
              id="hitPoints"
              v-model.number="combatant.hitPoints"
            />
          </div>
        </div>
      </div>
      <div class="row margin-bottom-small" v-if="combatant.passivePerception">
        <div class="col">
          <div>
            <b>passivePerception</b>
          </div>
          <div>
            <input
              class="col s4 m4 l4 margin-btm-none margin-top-small"
              type="number"
              id="passivePerception"
              v-model.number="combatant.passivePerception"
            />
          </div>
        </div>
      </div>
      <div class="row margin-bottom-small" v-if="combatant.initiative">
        <div class="col">
          <div>
            <b>initiative</b>
          </div>
          <div>
            <input
              class="col s4 m4 l4 margin-btm-none margin-top-small"
              type="number"
              id="initiative"
              v-model.number="combatant.initiative"
            />
          </div>
        </div>
      </div>
      <div class="row margin-bottom-small" v-if="combatant.speed">
        <div class="col">
          <div>
            <b>speed</b>
          </div>
          <div>
            <input
              class="col s4 m4 l4 margin-btm-none margin-top-small"
              type="number"
              id="speed"
              v-model.number="combatant.speed"
            />
          </div>
        </div>
      </div>
      <div class="row margin-bottom-small" v-if="combatant.abilityScore">
        <div class="col s12 m12 l6">
          <div class="row">
            <div class="col">str {{ combatant.abilityScore.str }}</div>
            <div class="col">dex {{ combatant.abilityScore.dex }}</div>
            <div class="col">con {{ combatant.abilityScore.con }}</div>
          </div>
        </div>
        <div class="col s12 m12 l6">
          <div class="row">
            <div class="col">int {{ combatant.abilityScore.int }}</div>
            <div class="col">wis {{ combatant.abilityScore.wis }}</div>
            <div class="col">cha {{ combatant.abilityScore.cha }}</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CombatantDetail",
  props: {
    combatant: Object
  },
  computed: {
    size() {
      switch (this.combatant.size) {
        case "tn":
          return "tiny";
        case "sm":
          return "small";
        case "md":
          return "medium";
        case "lg":
          return "large";
        case "hg":
          return "huge";
        case "gr":
          return "gargantuan";
        default:
          return "whoa";
      }
    }
  }
};
</script>

<style scoped>
.margin-btm-none {
  margin-bottom: 0;
}
.margin-top-small {
  margin-top: 5px;
}
.margin-bottom-small {
  margin-bottom: 5px;
}
</style>