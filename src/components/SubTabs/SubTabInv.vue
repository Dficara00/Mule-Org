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
    <div v-for="(value, key) in muleObject" :key="key">
      <h2>{{ key }}</h2>
      <div class="invBox" v-for="item in value" :key="item.rune">
        <span class="rune"> {{ item.rune }} </span>
        <span class="base">{{ item.base }} </span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SubTabInv',
  props: {
    muleObject: {
      type: Object,
      required: true,
    },
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
  padding: 4px;
  font-size: 18px;
}
span.base {
  font-size: 18px;
}
</style>
