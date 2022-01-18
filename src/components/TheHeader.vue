<template>
  <div class="header">
    <header>
      <button
        class="button"
        :class="{ active: currentTab === 'SubTabRW' }"
        @click="onClickSubTab('SubTabRW')"
      >
        Runewords
      </button>
      <button
        class="button"
        :class="{ active: currentTab === 'SubTabInv' }"
        @click="onClickSubTab('SubTabInv')"
      >
        Inventory
      </button>
      <button
        class="button"
        :class="{ active: currentTab === 'SubTabAdd' }"
        @click="onClickSubTab('SubTabAdd')"
      >
        Add
      </button>
      <button
        class="button"
        :class="{ active: currentTab === 'SubTabInfo' }"
        @click="onClickSubTab('SubTabInfo')"
      >
        Info
      </button>
    </header>
  </div>
</template>
<script>
export default {
  name: 'TheHeader',
  props: {
    currentTab: {
      type: String,
      required: true,
    },
  },
  methods: {
    onClickSubTab(tabName) {
      this.$emit('onChangeTab', tabName);
    },
  },
};
</script>

<style>
.header {
  padding: 0px;
  position: fixed;
  left: 0px;
  top: 0px;
  width: 100%;
  height: 150px;
  border-radius: 0px;
  border: 2px solid #585858;
  background: #585858;
  text-align: left;
}

.button {
  color: white;
  background-color: #585858;
  padding: 15px 32px;
  font-size: 36px;
  font-family: Exo;
  border: 5px;
  font-weight: 600;
  letter-spacing: 0em;
  font-style: normal;
  display: inline-block;
  margin-top: 30px;
}

.active {
  text-decoration: underline;
  color: white;
}
</style>
