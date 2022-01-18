<template>
  <form>
    <div>
      <h1>
        <u>Goal Runewords</u>
        <img class="iconL" src="@/assets/Tyreal.png" alt="" />
      </h1>
    </div>
    <div>
      <h2>Enigma - Available</h2>
    </div>
    <br />
    <div>
      <h2>
        <img class="iconR" src="@/assets/Amazon.png" alt="" />
        Infinity - Unavailable
      </h2>
    </div>
    <br />
    <div>
      <h2>Call To Arms - Unavailable</h2>
    </div>
    <br />
    <div>
      <h2>
        <img class="iconR" src="@/assets/Necro.png" alt="" />
        Beast - Unavailable
      </h2>
    </div>
  </form>
</template>

<script>
export default {
  name: 'SubTabRW',
  // data() {},
  computed: {},
  methods: {},
  created() {},
};
</script>

<style>
h2 {
  font-family: exo;
  color: black;
  text-align: center;
}
.iconL {
  padding-left: 10px;
}
.iconR {
  padding-right: 10px;
}
</style>
