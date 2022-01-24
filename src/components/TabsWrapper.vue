<template>
  <div class="tabs">
    <p v-if="isLoading">Loading....</p>
    <div v-else>
      <component :itemsArray="itemsArray" :muleObject="muleObject" :is="currentTab" />
    </div>
  </div>
</template>

<script>
import SubTabAdd from './SubTabs/SubTabAdd.vue';
import SubTabInv from './SubTabs/SubTabInv.vue';
import SubTabRW from './SubTabs/SubTabRW.vue';
import SubTabInfo from './SubTabs/SubTabInfo.vue';

export default {
  name: 'TabWrapper',
  components: {
    SubTabAdd,
    SubTabInv,
    SubTabRW,
    SubTabInfo,
  },
  data() {
    return {
      muleObject: {},
      isLoading: false,
      itemsArray: [],
    };
  },
  props: {
    currentTab: {
      type: String,
      required: true,
    },
  },
  methods: {
    loadResults() {
      this.isLoading = true;
      fetch('https://mule-organizer-default-rtdb.firebaseio.com/inventory.json')
        .then((response) => {
          if (response.ok) {
            return response.json();
          }
          return false;
        })
        .then((data) => {
          this.isLoading = false;
          const keyArray = Object.keys(data);
          keyArray.forEach((item) => {
            const muleName = data[item].mule;
            if (this.muleObject[muleName]) {
              this.muleObject[muleName].push(data[item]);
            } else {
              this.muleObject[muleName] = [data[item]];
            }
            this.itemsArray.push(data[item].rune, data[item].base);
          });
        });
    },
  },
  created() {
    this.loadResults();
  },
};
</script>

<style>
h1 {
  font-family: exo;
  color: black;
}
.tabs {
  padding-top: 100px;
}
</style>
