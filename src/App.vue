<template>
  <div id="app">
    <div class="dice-wrapper">
      <Home :count="count" :result="result"/>
      <button @click="setRandomDiceData">Roll dice!</button>
    </div>
  </div>
</template>

<script>
import Home from "./components/Home.vue";
import axios from "axios";
export default {
  name: "App",
  data() {
    return {
      diceNum: 1,
      result:null,
      count:3,
    };
  },
  components: {
    Home,
  },
  methods: {
    setRandomDiceData() {
      const randomDiceNum = Math.floor(Math.random() * 6) + 1;
      this.diceNum = randomDiceNum;
      this.callAPI();
    },
    callAPI() {
      axios
        .get(
          `https://www.random.org/integers/?num=${this.count}&min=1&max=6&col=1&base=10&format=plain&rnd=new`
        )
        .then((response) => {
          this.result = response.data;
        })
        .catch((e) => {
          this.errors.push(e);
        });
    },
  },
  computed: {
    getDice() {
      this.setRandomDiceData();
      return `dice dice-${this.diceNum}`;
    },
  },
  watch: {
  },
};
</script>

<style>
button {
  margin-top: 1em;
  margin-right: 0;
  margin-bottom: 0;
}
.dice-wrapper {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.dice {
  font-size: 3em;
}
</style>
