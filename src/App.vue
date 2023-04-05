<template>
  <div class="container">

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
    <div>
      <pre>
      {{ JSON.stringify(testForm, null, 2) }}
      </pre>
    </div>
    <form @submit="formSubmit">
      <div>
        <label for="fname" class="form-label">First name:</label><br>
        <input type="text" class="form-control w-50 mx-auto" id="fname" name="fname"
          v-model="testForm.firstName.trim"><br>
      </div>

      <div>
        <label for="description" class="form-label">Description:</label><br>
        <textarea class="form-control w-50 mx-auto" id="description" name="description"
          v-model="testForm.description.trim"></textarea><br><br>
      </div>
      <div class="d-flex justify-content-center">
        <div class="form-check">
          <input class="form-check-input cursor-pointer" type="checkbox" value="" id="flexCheckDefault"
            v-model="testForm.isAggred" true-value="yes" false-value="no">
          <label class="form-check-label" for="flexCheckDefault">
            Default checkbox
          </label>
        </div>
        <!-- <div class="form-check">
          <input class="form-check-input" type="checkbox" value="" id="flexCheckChecked">
          <label class="form-check-label" for="flexCheckChecked">
            Checked checkbox
          </label>
        </div> -->
      </div>
      <div>
        <label class="form-label" for="select">Select Your city</label>
        <select class="form-select" aria-label="Default select example" v-model="testForm.selectCity" id="select">
          <option value="">Open this select menu</option>
          <option value="1">Ahemdabad</option>
          <option value="2">Rajkot</option>
          <option value="3">Baroda</option>
        </select>
      </div>
      <div>
        <label class="form-label" for="preferCity">Prefer City to Work</label>
        <select class="form-select" aria-label="Default select example" multiple v-model="testForm.preferCity"
          id="preferCity">
          <option value="1">Ahemdabad</option>
          <option value="2">Rajkot</option>
          <option value="3">Baroda</option>
        </select>
      </div>
      <div class="d-flex">
        <div class="form-check me-2">
          <input class="form-check-input" type="checkbox" value="html" id="html" v-model="testForm.skills">
          <label class="form-check-label" for="html">
            HTML
          </label>
        </div>
        <div class="form-check me-2">
          <input class="form-check-input" type="checkbox" value="css" id="css" v-model="testForm.skills">
          <label class="form-check-label" for="css">
            Css
          </label>
        </div>
        <div class="form-check me-2">
          <input class="form-check-input" type="checkbox" value="js" id="js" v-model="testForm.skills">
          <label class="form-check-label" for="js">
            Javascript
          </label>
        </div>
      </div>
      <div class="d-flex">
        <div class="form-check me-2">
          <input class="form-check-input" value="male" type="radio" name="gender" v-model="testForm.gender" id="male">
          <label class="form-check-label" for="male">
            Male
          </label>
        </div>
        <div class="form-check">
          <input class="form-check-input" type="radio" value="female" name="gender" v-model="testForm.gender" id="female">
          <label class="form-check-label" for="female">
            Female
          </label>
        </div>
      </div>
      <button type="submit" class="btn btn-primary" value="Submit"> Submit</button>
    </form>
  </div>
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
      baseMultiPly: 5,
      testForm: {
        firstName: '',
        description: '',
        isAggred: 'no',
        selectCity: '',
        preferCity: [],
        skills: [],
        gender: 'male'
      }
    };
  },
  methods: {
    Multiply(num) {
      return this.baseMultiPly * num
    },
    formSubmit(event) {
      event.preventDefault()
      console.log(this.testForm);
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
