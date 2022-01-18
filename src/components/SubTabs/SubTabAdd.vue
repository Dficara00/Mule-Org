<template>
  <form @submit.prevent="submitData">
    <div>
      <h1>
        <img class="icon" src="@/assets/sword.png" alt="" />
        <u>Add Items</u>
        <img class="icon" src="@/assets/Axe.png" alt="" />
      </h1>
    </div>
    <br />
    <div class="form-control">
      <label for="muleName"> Mule </label>
      <select name="muleName" id="muleName" v-model="muleName">
        <option value="Tubby">Tubby</option>
        <option value="RWBases">RWBases</option>
        <option value="Buzz">Buzz</option>
      </select>
    </div>
    <br />
    <div class="form-control">
      <label for="runeName"> Rune </label>
      <input placeholder="Enter Rune" type="option" name="" id="runeName" v-model="runeName" />
    </div>
    <br />
    <div class="form-control">
      <label for="baseName"> Base </label>
      <input placeholder="Enter Base" type="option" name="" id="baseName" v-model="baseName" />
    </div>
    <br />
    <div>
      <img class="icon" src="@/assets/Jamella.png" alt="" />
      <button class="savebutton">Save Data</button>
      <img class="icon" src="@/assets/Diablo.png" alt="" />
    </div>
  </form>
</template>

<script>
export default {
  name: 'SubTabAdd',
  data() {
    return {
      muleName: '',
      runeName: '',
      baseName: '',
    };
  },
  methods: {
    submitData() {
      fetch('https://mule-organizer-default-rtdb.firebaseio.com/inventory.json', {
        method: 'POST',
        headers: {
          'Content-type': 'application/json',
        },
        body: JSON.stringify({
          mule: this.muleName,
          rune: this.runeName,
          base: this.baseName,
        }),
      });
      this.muleName = '';
      this.runeName = '';
      this.baseName = '';
    },
  },
};
</script>

<style>
br {
  display: block;
  margin: 10px 0;
}
.form-control {
  padding-top: 0px;
  padding-bottom: 2px;
  font-display: exo;
  color: black;
}
.savebutton {
  font: exo;
  border: 1px solid black;
  background-color: black;
  color: white;
  cursor: pointer;
  padding: 0.75rem 2rem;
  border-radius: 30px;
}
.icon {
  padding-left: 10px;
  padding-right: 10px;
}
</style>
