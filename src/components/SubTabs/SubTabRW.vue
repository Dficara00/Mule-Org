<template>
  <div>
    <h1><u>Goal Runewords</u></h1>
    <div v-for="(value, key) in allItems" :key="key">
      <h2>{{ key }} {{ value }}</h2>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SubTabRW',
  data() {
    return {
      runewordRecipes: {
        Enigma: ['Jah', 'Ith', 'Ber', 'Archon Plate'],
        Insight: ['Ral', 'Tir', 'Tal', 'Sol', 'Thresher'],
        CallToArms: ['Amn', 'Ral', 'Mal', 'Ist', 'Ohm', 'Flail'],
        Beast: ['Ber', 'Tir', 'Um', 'Mal', 'Lum', 'Axe'],
        Lore: ['Ort', 'Sol', 'Helm'],
      },
    };
  },
  props: {
    muleObject: {
      type: Object,
      required: true,
    },
    itemsArray: {
      type: Array,
      required: true,
    },
  },

  computed: {
    allItems() {
      const recipeStatus = {};
      const runewords = Object.keys(this.runewordRecipes);
      runewords.forEach((runeword) => {
        recipeStatus[runeword] = 'Available';
        this.runewordRecipes[runeword].forEach((piece) => {
          if (this.itemsArray.indexOf(piece) === -1) {
            recipeStatus[runeword] = 'Unavailable';
          }
        });
      });
      return recipeStatus;
    },
  },
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
