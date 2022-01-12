<template>
  <div>
    <Dice
      v-for="(diceNum, index) in arrResult"
      :key="index"
      :diceNum="diceNum"
    />
  </div>
</template>

<script>
import Dice from "./Dice.vue";
export default {
  name: "Home",
  components: {
    Dice,
  },
  props: ["count", "result"],
  computed: {
    arrResult() {
      return this.result ? this.result.trim().split("\n") : [];
    },
  },
  beforeCreate(){
      console.log('befor created',this.count);
  },
  created() {
      console.log('created',this.count);
  }
};
</script>

<style></style>
