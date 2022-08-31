<template>
<div>
    <input type="text" v-model.number="op1">
    <input type="text" v-model.number="op2">
    ={{result}}
    <div>
        <button @click="chose($event)">+</button>
        <button @click="chose($event)">-</button>
        <button @click="chose($event)">/</button>
        <button @click="chose($event)">*</button>
        <button @click="chose($event)">^</button>
        <button @click="chose($event)">%</button>
    </div>
</div>
</template>
<script>
export default {
  name: 'MyCalc',
  data () {
    return {
      result: 0,
      op1: 0,
      op2: 0
    }
  },
  methods: {
    chose (e) {
      switch (e.target.innerText) {
        case '+':
          this.result = this.op1 + this.op2
          break
        case '-':
          this.result = this.op1 - this.op2
          break
        case '/':
          this.result = this.op1 / this.op2
          break
        case '*':
          this.result = this.op1 * this.op2
          break
        case '%':
          this.result = Math.pow(this.op1, this.op2)
          break
        case '^':
          this.result = Math.floor(this.op1 / this.op2)
          break
      }
    }
  }
}

</script>

<style></style>
