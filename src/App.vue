<template>
  <div>{{ greet }} {{ name }}</div>
  <div v-html="channel">
  </div>
  <h2 :id="head" :class="isbtnClicked ? 'success' : 'danger'">Heading</h2>
  <h2 :id="head" :class="isbtnClicked && 'success'">Heading 2</h2>
  <button :disabled="isDisabled" @click="isbtnClicked = !isbtnClicked; showIf = !showIf;">Button</button>

  <h2 v-if="num === 0"> number is zero</h2>
  <h2 v-else-if="num > 0"> number is greater then zero</h2>
  <h2 v-else-if="num < 0"> number is greater less zero</h2>
  <h2 v-else> not a number</h2>
  <div v-if="showIf">
    <h2>test</h2>
  </div>
  <template v-if="showIf">
    <h2>test 2</h2>
  </template>
  <h2 v-show="showIf"> v-Show test</h2>
  <p v-for="(item, i) in arrayData" :key="i">{{ item }}</p>
  <h1>{{ 'Multiply function ' + Multiply(3) }}</h1>
  <!-- <img alt="Vue logo" src="./assets/logo.png" /> -->
  <!-- <HelloWorld msg="Welcome to Your Vue.js App" /> -->
</template>

<script>
// import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "App",
  components: {
    // HelloWorld,
  },
  data() {
    return {
      greet: 'hello',
      name: "Raviraj",
      head: "Head",
      channel: "<b>Welcome Here</b>",
      isDisabled: false,
      isbtnClicked: false,
      num: 0,
      showIf: false,
      arrayData: ['test 1', 'test 2', 'test 3'],
      baseMultiPly: 5
    };
  },
  methods: {
    Multiply(num) {
      return this.baseMultiPly * num
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /* margin-top: 60px; */
}

.success {
  color: rgb(86, 231, 19);
}

.danger {
  color: red;
}
</style>
