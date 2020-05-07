<template>
  <div class="row">
    <div class="col">
      <div class="row margin-bottom-small" v-if="combatant.name">
        <div class="col">
          <b>name</b>
        </div>
        <div>{{ combatant.name }}</div>
      </div>
      <div class="row margin-bottom-small" v-if="combatant.size">
        <div class="col">
          <b>size</b>
        </div>
        <div>{{ size }}</div>
      </div>
      <div class="row margin-bottom-small">
        <div class="col">
          <b>armorClass</b>
        </div>
        <div class="col">
          <input
            class="col s4 margin-btm-none margin-top-small input-height-small"
            type="number"
            id="armorClass"
            v-model.number="combatant.armorClass"
          />
        </div>
      </div>
      <div class="row margin-bottom-small">
        <div class="col">
          <b>hitPoints</b>
        </div>
        <div class="col">
          <input
            class="col s4 margin-btm-none margin-top-small input-height-small"
            type="number"
            id="hitPoints"
            v-model.number="combatant.hitPoints"
          />
        </div>
      </div>
      <div class="row margin-bottom-small">
        <div class="col">
          <b>passivePerception</b>
        </div>
        <div class="col">
          <input
            class="col s4 margin-btm-none margin-top-small input-height-small"
            type="number"
            id="passivePerception"
            v-model.number="combatant.passivePerception"
          />
        </div>
      </div>
      <div class="row margin-bottom-small" v-if="combatant.initiative">
        <div class="col">
          <b>initiative</b>
        </div>
        <div class="col">
          <input
            class="col s4 margin-btm-none margin-top-small input-height-small"
            type="number"
            id="initiative"
            v-model.number="combatant.initiative"
          />
        </div>
      </div>
      <div class="row margin-bottom-small" v-if="combatant.speed">
        <div class="col">
          <b>speed</b>
        </div>
        <div class="col">
          <input
            class="col s4 margin-btm-none margin-top-small input-height-small"
            type="number"
            id="speed"
            v-model.number="combatant.speed"
          />
        </div>
      </div>
      <div class="row margin-bottom-small" v-if="combatant.abilityScore">
        <div class="col s12 m12 l6">
          <div class="row">
            <div class="col s4 l4">
              <b>STR</b>
              <input
                class="margin-btm-none margin-top-small"
                type="number"
                id="str"
                v-model.number="combatant.abilityScore.str"
              />
              <span
                :class="modifierColor(modifier(combatant.abilityScore.str))"
              >{{ modifier(combatant.abilityScore.str) }}</span>
            </div>
            <div class="col s4 l4">
              <b>DEX</b>
              <input
                class="margin-btm-none margin-top-small"
                type="number"
                id="dex"
                v-model.number="combatant.abilityScore.dex"
              />
              <span
                :class="modifierColor(modifier(combatant.abilityScore.dex))"
              >{{ modifier(combatant.abilityScore.dex) }}</span>
            </div>
            <div class="col s4 l4">
              <b>CON</b>
              <input
                class="margin-btm-none margin-top-small"
                type="number"
                id="con"
                v-model.number="combatant.abilityScore.con"
              />
              <span
                :class="modifierColor(modifier(combatant.abilityScore.con))"
              >{{ modifier(combatant.abilityScore.con) }}</span>
            </div>
          </div>
        </div>
        <div class="col s12 m12 l6">
          <div class="row">
            <div class="col s4 l4">
              <b>INT</b>
              <input
                class="margin-btm-none margin-top-small"
                type="number"
                id="int"
                v-model.number="combatant.abilityScore.int"
              />
              <span
                :class="modifierColor(modifier(combatant.abilityScore.int))"
              >{{ modifier(combatant.abilityScore.int) }}</span>
            </div>
            <div class="col s4 l4">
              <b>WIS</b>
              <input
                class="margin-btm-none margin-top-small"
                type="number"
                id="wis"
                v-model.number="combatant.abilityScore.wis"
              />
              <span
                :class="modifierColor(modifier(combatant.abilityScore.wis))"
              >{{ modifier(combatant.abilityScore.wis) }}</span>
            </div>
            <div class="col s4 l4">
              <b>CHA</b>
              <input
                class="margin-btm-none margin-top-small"
                type="number"
                id="cha"
                v-model.number="combatant.abilityScore.cha"
              />
              <span
                :class="modifierColor(modifier(combatant.abilityScore.cha))"
              >{{ modifier(combatant.abilityScore.cha) }}</span>
            </div>
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
  },
  methods: {
    modifier(abilityScore) {
      return Math.floor((abilityScore - 10) / 2);
    },
    modifierColor(modifier) {
      return modifier < 0
        ? "red-text"
        : modifier === 0
        ? "grey-text"
        : "green-text";
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
.input-height-small {
  height: 1em !important;
}
</style>