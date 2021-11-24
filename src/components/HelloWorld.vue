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
    <div class="display">
      fib(<input v-model.number="operand1" type="number" />) fib(<input
        v-model.number="operand2"
        type="number"
      />) = {{ fibResult }}
    </div>
    <!-- <button @click="calculate('+')">+</button>
    <button @click="calculate('-')">-</button>
    <button @click="calculate('*')">*</button>
    <button @click="calculate('/')">/</button> -->
    <div class="keyboard">
      <button
        v-for="operand in operands"
        v-bind:key="operand"
        v-bind:title="operand"
        v-bind:disabled="operand1 === '' || operand2 === ''"
        @click="calculate(operand)"
      >
        {{ operand }}
      </button>
    </div>
    <div class="strange-message">
      <template v-if="result < 0">Получилось отрицательное число</template>
      <template v-else-if="result < 100">Результат в первой сотне</template>
      <template v-else>Получилось слишком большое число</template>
    </div>
    <div>
      <input type="checkbox" v-model="clicked" />
      <label>Отобразить экранную клавиатуру</label><br />
      <button
        class="myCollection"
        v-for="item in myCollection"
        v-bind:key="item"
        v-show="clicked"
        @click="addNumber(item, picked)"
      >
        {{ item }}
      </button>
      <button @click="removeNumber(picked)">&#8592;</button>
      <br />
      <input type="radio" id="one" value="operand1" v-model="picked" />
      <label for="one">Операнд 1</label>
      <input type="radio" id="two" value="operand2" v-model="picked" />
      <label for="two">Операнд 2</label>
      <br />
    </div>
    <div v-if="error">Ошибка! {{ error }}</div>
    <div class="logs">
      <div v-for="(log, id) in logs" v-bind:key="id">{{ log }}</div>
    </div>
    <h1>{{ msg }}</h1>
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
      operand1: "",
      operand2: "",
      result: 0,
      error: "",
      myCollection: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9],
      operands: ["+", "-", "*", "/"],
      logs: {},
      fibResult: 0,
      clicked: true,
      picked: "",
    };
  },
  methods: {
    addNumber(item, picked) {
      if (picked == "operand1") {
        this.operand1 = `${this.operand1}${item}`;
      } else {
        this.operand2 = `${this.operand2}${item}`;
      }
    },
    removeNumber(picked) {
      if (picked == "operand1") {
        this.operand1 = this.operand1.slice(0, -1);
      } else {
        this.operand2 = this.operand2.slice(0, -1);
      }
    },
    fib(n) {
      return n <= 1 ? n : this.fib(n - 1) + this.fib(n - 2);
    },
    calculate(operation = "+") {
      this.error = "";
      switch (operation) {
        case "+":
          this.add();
          break;
        case "-":
          this.substract();
          break;
        case "*":
          this.multiply();
          break;
        case "/":
          this.divide();
          break;
      }
      const key = Date.now();
      const value = `${this.operand1} ${operation} ${this.operand2} = ${this.result}`;
      this.$set(this.logs, key, value);
      // this.logs[
      //   Date.now()
      // ] = `${this.operand1} ${operation} ${this.operand2} = ${this.result}`;
    },
    add() {
      this.result = this.operand1 + this.operand2;
      this.fibResult = this.fibb1 + this.fibb2;
    },
    substract() {
      this.result = this.operand1 - this.operand2;
      this.fibResult = this.fibb1 - this.fibb2;
    },
    multiply() {
      this.result = this.operand1 * this.operand2;
      this.fibResult = this.fibb1 * this.fibb2;
    },
    divide() {
      const { operand2 } = this;
      if (operand2 === 0) {
        this.error = "Делить на 0 нельзя!";
      } else {
        this.result = parseInt(this.operand1 / this.operand2);
        this.fibResult = this.fibb1 / this.fibb2;
      }
    },
   },
  computed: {
    fibb1() {
      return this.fib(this.operand1);
    },
    fibb2() {
      return this.fib(this.operand2);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.myCollection {
  display: inline-block;
}
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
