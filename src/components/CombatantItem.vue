<template>
  <div>
    <div class="row">
      <div class="col" :class="combatant.isNpc ? 'villain' : 'hero'">{{combatant.name}}</div>
      <div class="col">
        <div class="form-group">
          <input type="number" class="form-control form-control-sm" id="hp" v-model="combatant.hp" />
        </div>
      </div>
      <div class="col">
        <div class="form-group">
          <input type="number" class="form-control form-control-sm" id="ac" v-model="combatant.ac" />
        </div>
      </div>
      <div class="col">
        <div class="form-group">
          <input
            type="number"
            class="form-control form-control-sm"
            id="init"
            v-model="combatant.initiative"
          />
        </div>
      </div>
      <div class="col">
        <div class="form-group">
          <input type="number" class="form-control form-control-sm" id="pp" v-model="combatant.pp" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CombatantItem",
  props: ["combatant"]
};
</script>

<style lang="css" scoped>
.hero {
  color: #7ed6df;
}
.villain {
  color: #eb4d4b;
}
</style>