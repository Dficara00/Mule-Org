<template>
  <div>
    <div>
      <h1 class="mHead">
        <img class="icon" src="@/assets/stashClosed.png" alt="" />
        <u> Mule Inventories</u>
        <img class="icon" src="@/assets/Treasure-Open-icon.png" alt="" />
      </h1>
    </div>
    <div v-for="(value, key) in muleObject" :key="key">
      <h2 class="mHead">
        <u>{{ key }}</u>
      </h2>
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
.icon {
  padding-left: 10px;
  padding-right: 10px;
}
.invBox {
  display: flex;
  justify-content: center;
  color: black;
  margin: 5px;
}
.rune {
  padding-right: 5px;
  font-size: 18px;
}
.base {
  font-size: 18px;
}
.mHead {
  margin: 8px;
}
</style>
