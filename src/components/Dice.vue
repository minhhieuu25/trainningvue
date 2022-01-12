<template>
  <div class="container">
    <div :class="face.tag" v-if="face.col.length > 1">
      <div v-for="(item, index) in face.col" :key="index" class="column">
        <span
          v-for="(subItem, index) in face.col[index]"
          :key="index"
          class="pip"
        ></span>
      </div>
    </div>
    <div :class="face.tag" v-else>
      <span
        v-for="(item, index) in face.col[0]"
        :key="index"
        class="pip"
      ></span>
    </div>
  </div>
</template>

<script>
export default {
  name: "Dice",
  props: ["diceNum"],
  data: function () {
    return {
      numCheck: null,
      activeClass: "",
      faceDice: {
        1: {
          tag: "first-face",
          col: [1],
        },
        2: {
          tag: "second-face",
          col: [2],
        },
        3: {
          tag: "third-face",
          col: [3],
        },
        4: {
          tag: "fourth-face",
          col: [2, 2],
        },
        5: {
          tag: "fifth-face",
          col: [2, 1, 2],
        },
        6: {
          tag: "sixth-face",
          col: [3, 3],
        },
      },
    };
  },
  components: {},
  methods: {},
  watch: {},
  computed: {
    face() {
      console.log(this.result);
      return this.faceDice[this.diceNum];
    },
  },
};
</script>

<style>
.container {
  display: flex;
  justify-content: center;
  margin-bottom: 50px;
  margin-top: 20px;
}
.first-face {
  display: flex;
  justify-content: center;
  align-items: center;
}

.second-face {
  display: flex;
  justify-content: space-between;
}

.second-face .pip:nth-of-type(2) {
  align-self: flex-end;
}

.third-face {
  display: flex;
  justify-content: space-between;
}

.third-face .pip:nth-of-type(2) {
  align-self: center;
}

.third-face .pip:nth-of-type(3) {
  align-self: flex-end;
}

.fourth-face,
.sixth-face {
  display: flex;
  justify-content: space-between;
}

.fourth-face .column,
.sixth-face .column {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.fifth-face {
  display: flex;
  justify-content: space-between;
}

.fifth-face .column {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.fifth-face .column:nth-of-type(2) {
  justify-content: center;
}

/* OTHER STYLES */

* {
  box-sizing: border-box;
}

html,
body {
  height: 100%;
}

body {
  display: flex;
  align-items: center;
  justify-content: center;
  vertical-align: center;
  flex-wrap: wrap;
  align-content: center;
  font-family: "Open Sans", sans-serif;

  /* background: linear-gradient(to right, #222, #333); */
}

[class$="face"] {
  margin: 16px;
  padding: 4px;

  background-color: #e7e7e7;
  width: 104px;
  height: 104px;
  object-fit: contain;

  box-shadow: inset 0 5px white, inset 0 -5px #bbb, inset 5px 0 #d7d7d7,
    inset -5px 0 #d7d7d7;

  border-radius: 10%;
}

.pip {
  display: block;
  width: 24px;
  height: 24px;
  border-radius: 50%;
  margin: 4px;

  background-color: #333;
  box-shadow: inset 0 3px #111, inset 0 -3px #555;
}
</style>
