<template>
  <div>
    <div v-if="!displayForm" class="d-flex flex-column justify-content-around">
      <div>
        <button
          type="button"
          class="btn btn-primary btn-block"
          @click="displayForm = !displayForm; combatant.isNpc = false"
        >add character</button>
      </div>
      <div class="d-flex flex-column justify-content-around">
        <span class="badge badge-light">or</span>
      </div>
      <div>
        <button
          type="button"
          class="btn btn-danger btn-block"
          @click="displayForm = !displayForm; combatant.isNpc = true"
        >add monster</button>
      </div>
    </div>
    <!-- monster / character input form -->
    <div v-if="displayForm">
      <form class="margin">
        <div class="form-group row">
          <label for="name" class="col-md-4 col-form-label">name</label>
          <div class="col-md-8">
            <input type="text" class="form-control" id="name" />
          </div>
        </div>
        <div class="form-group row">
          <label for="hp" class="col-md-8 col-form-label">hit points</label>
          <div class="col-md-4">
            <input type="number" class="form-control" id="hp" v-model.number="combatant.hp" />
          </div>
        </div>
        <div class="form-group row">
          <label for="ac" class="col-md-8 col-form-label">armor class</label>
          <div class="col-md-4">
            <input type="number" class="form-control" id="ac" v-model.number="combatant.ac" />
          </div>
        </div>
        <div class="form-group row">
          <label for="pp" class="col-md-8 col-form-label">passive perception</label>
          <div class="col-md-4">
            <input type="number" class="form-control" id="pp" v-model.number="combatant.pp" />
          </div>
        </div>
        <input type="hidden" id="type" name="type" :value="combatant.isNpc" />
        <div class="form-group row">
          <div class="col-12">
            <button type="submit" class="btn btn-primary btn-block">add</button>
          </div>
          <div class="col-12">
            <button
              type="submit"
              class="btn btn-warning btn-block"
              @click="displayForm = !displayForm"
            >cancel</button>
          </div>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "AddCombatantComponent",
  data: function() {
    return {
      combatant: {
        name: "",
        hp: "",
        ac: "",
        pp: "",
        isNpc: false
      },
      displayForm: false
    };
  }
};
</script>

<style scoped>
</style>
