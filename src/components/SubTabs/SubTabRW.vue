<template>
  <div>
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
        Lore: ['Ort', 'Sol'],
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
            console.log(this.itemsArray.indexOf(piece), 'beep');
            recipeStatus[runeword] = 'Unavailable';
          }
        });
      });
      return recipeStatus;
    },
  },

  methods: {},
  created() {
    console.log(this.allItems, 'bbop');
  },
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
