<template>
  <div class="hello">
    <!-- <button @click="counter++">Click</button>
    <h1 class="counter">{{ counter }}</h1>
    <input @keyup="keyUpMethod" />
    <button @mouseover="mouseOverMethos">Meow</button>
    <button @click="countMulti">Multi count!</button> -->
    <h1>Калькулятор :)</h1>
    <input v-model.number="operand1" type="number" />
    <input v-model.number="operand2" type="number" />
    = {{ result }}
    <br />
    <button @click="result = operand1 + operand2">+</button>
    <button @click="minus(operand1, operand2)">-</button>
    <button @click="multiply(operand1, operand2)">*</button>
    <button
      v-if="operand1 !== 0 && operand2 !== 0"
      @click="divide(operand1, operand2)"
    >
      /
    </button>
    <button v-else disabled>/</button>
    <h1>{{ msg }}</h1>
    <p>
      For a guide and recipes on how to configure / customize this project,<br />
      check out the
      <a href="https://cli.vuejs.org" target="_blank" rel="noopener"
        >vue-cli documentation</a
      >.
    </p>
    <h3>Installed CLI Plugins</h3>
    <ul>
      <li>
        <a
          href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-babel"
          target="_blank"
          rel="noopener"
          >babel</a
        >
      </li>
      <li>
        <a
          href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-eslint"
          target="_blank"
          rel="noopener"
          >eslint</a
        >
      </li>
    </ul>
    <h3>Essential Links</h3>
    <ul>
      <li>
        <a href="https://vuejs.org" target="_blank" rel="noopener">Core Docs</a>
      </li>
      <li>
        <a href="https://forum.vuejs.org" target="_blank" rel="noopener"
          >Forum</a
        >
      </li>
      <li>
        <a href="https://chat.vuejs.org" target="_blank" rel="noopener"
          >Community Chat</a
        >
      </li>
      <li>
        <a href="https://twitter.com/vuejs" target="_blank" rel="noopener"
          >Twitter</a
        >
      </li>
      <li>
        <a href="https://news.vuejs.org" target="_blank" rel="noopener">News</a>
      </li>
    </ul>
    <h3>Ecosystem</h3>
    <ul>
      <li>
        <a href="https://router.vuejs.org" target="_blank" rel="noopener"
          >vue-router</a
        >
      </li>
      <li>
        <a href="https://vuex.vuejs.org" target="_blank" rel="noopener">vuex</a>
      </li>
      <li>
        <a
          href="https://github.com/vuejs/vue-devtools#vue-devtools"
          target="_blank"
          rel="noopener"
          >vue-devtools</a
        >
      </li>
      <li>
        <a href="https://vue-loader.vuejs.org" target="_blank" rel="noopener"
          >vue-loader</a
        >
      </li>
      <li>
        <a
          href="https://github.com/vuejs/awesome-vue"
          target="_blank"
          rel="noopener"
          >awesome-vue</a
        >
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      operand1: 0,
      operand2: 0,
      result: 0,
    };
  },
  methods: {
    minus(op1, op2) {
      this.result = op1 - op2;
    },
    multiply(op1, op2) {
      this.result = op1 * op2;
    },
    divide(op1, op2) {
      this.result = parseInt(op1 / op2);
    },
    // keyUpMethod() {
    //   console.log("keyup");
    // },
    // mouseOverMethos() {
    //   console.log("mouse");
    // },
    // countMulti() {
    //   this.counter = this.counter * 2;
    // },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
