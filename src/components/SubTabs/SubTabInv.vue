<template>
  <div>
    <div>
      <h1>
        <img class="stash" src="@/assets/stashClosed.png" alt="" />
        <u> Mule Inventories</u>
        <img class="stash" src="@/assets/Treasure-Open-icon.png" alt="" />
      </h1>
    </div>
    <br />
    <p v-if="isLoading">Loading....</p>
    <div v-else>
      <div v-for="(value, key) in muleObject" :key="key">
        <h2>{{ key }}</h2>
        <div class="invBox" v-for="item in value" :key="item.rune">
          <span class="rune"> {{ item.rune }} </span>
          <span class="base">{{ item.base }} </span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SubTabInv',
  data() {
    return {
      muleObject: {},
      isLoading: false,
    };
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
.stash {
  padding-left: 10px;
  padding-right: 10px;
}
.invBox {
  display: flex;
  justify-content: center;
  align-items: center;
  color: black;
}
span.rune {
  padding: 10px;
  font-size: 18px;
}
span.base {
  font-size: 18px;
}
</style>
