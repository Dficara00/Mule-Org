<template>
  <div id="app">
    <TheHeader :currentTab="currentTab" @onChangeTab="setTab" />
    <TabsWrapper :currentTab="currentTab" />
  </div>
</template>

<script>
import TheHeader from './components/TheHeader.vue';
import TabsWrapper from './components/TabsWrapper.vue';

export default {
  name: 'App',
  components: {
    TheHeader,
    TabsWrapper,
  },
  data() {
    return {
      currentTab: 'SubTabRW',
    };
  },
  methods: {
    setTab(newTab) {
      this.currentTab = newTab;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: black;
  margin-top: 60px;
  text-align: center;
}
</style>
