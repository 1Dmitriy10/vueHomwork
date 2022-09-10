<template>
<div>
    <input type="text"
    ref="one"
    v-model.number="op1">
    <input type="text"
    ref="two"
    v-model.number="op2">
    ={{result}}
    <div>
        <button v-for="item of operands"
        v-bind:key="item"
        @click="choseOperation($event)">
        {{ item }}
        </button>
    </div>
    <div class="keyboard">
      <input @click="show=!show" type="checkbox">
      <p>Показать клавиатуру</p>
    </div>
    <div v-show="show">
      <div>
        <button
        v-for="item of numbers"
        v-bind:key="item"
        @click="choseNambers($event)">
        {{ item }}
        </button>
        <button class="del"
        @click="del()">
        del</button>
      </div>
      <div>
        <label>
          <input type="radio"
          value="Один"
          id="one"
          v-model="selectedOperand"
          @click="choseOperand()">
          <span>Операнд 1</span>
        </label>
        <label>
          <input type="radio"
          value="Два"
          id="two"
          v-model="selectedOperand"
          @click="choseOperand()">
          <span>Операнд 2</span>
        </label>

      </div>
    </div>
</div>
</template>
<script>
export default {
  name: 'MyCalc',
  data () {
    return {
      result: 0,
      op1: '',
      op2: '',
      show: false,
      numbers: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9],
      operands: ['+', '-', '/', '*', '^', '%'],
      selectedOperand: 'Один',
      delNumber: ''
    }
  },
  methods: {
    choseOperation (e) {
      switch (e.target.innerText) {
        case '+':
          this.getSum()
          break
        case '-':
          this.getSub()
          break
        case '/':
          this.getDiv()
          break
        case '*':
          this.getMulti()
          break
        case '^':
          this.getInt()
          break
        case '%':
          this.getDeg()
          break
      }
    },
    getSum () {
      this.result = Number(this.op1) + Number(this.op2)
    },
    getSub () {
      this.result = this.op1 - this.op2
    },
    getDiv () {
      this.result = this.op1 / this.op2
    },
    getMulti () {
      this.result = this.op1 * this.op2
    },
    getDeg () {
      this.result = Math.floor(Number(this.op1) / Number(this.op2))
    },
    getInt () {
      this.result = Math.pow(Number(this.op1), Number(this.op2))
    },
    choseOperand () {
      console.log(this.$refs.one.placeholder)
      function delChoseOperand () {
        if (this.selectedOperand === 'Один') {
          this.$refs.one.focus()
        } else {
          this.$refs.two.focus()
        }
      }
      setTimeout(delChoseOperand, 1000)
    },
    choseNambers (e) {
      this.selectedOperand === 'Один' ? this.op1 += e.target.innerText : this.op2 += e.target.innerText
    },
    del () {
      if (this.selectedOperand === 'Один') {
        this.delNumber = this.op1.split('')
        this.delNumber.pop()
        this.op1 = this.delNumber.join('')
      } else {
        this.delNumber = this.op2.split('')
        this.delNumber.pop()
        this.op2 = this.delNumber.join('')
      }
    }
  }
}

</script>

<style lang="scss">
  .keyboard{
    display: flex;
    justify-content: center;
  }
</style>
