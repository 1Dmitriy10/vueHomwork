<template>
    <div>
      <div :class="$style.input_box">
        <input type="text"
        placeholder="paymant description"
        v-model="category">
        <input type="number"
        placeholder="paymant amount"
        v-model="value">
        <input type="date"
        placeholder="paymant date"
        v-model="date">
      </div>
      <button :class="$style.add_paymant"
      @click="addPaymant()">ADD +</button>
    </div>
</template>

<script>
export default {
  name: 'AddExpenses',
  data () {
    return {
      date: '',
      category: '',
      value: '',
      data: {}
    }
  },
  methods: {
    addPaymant () {
      this.data = {
        date: this.date || this.getDate,
        category: this.category,
        value: this.value
      }
      this.$emit('newPaymant', this.data)
    }
  },
  computed: {
    getDate () {
      const newDate = new Date()
      const d = newDate.getDate()
      const m = newDate.getMonth() + 1
      const y = newDate.getFullYear()
      return `${d}.${m}.${y}`
    }
  }
}
</script>

<style lang="scss" module>
  .input_box{
    display: flex;
    flex-direction: column;
    width: 400px;
    gap: 15px;
  }
  .add_paymant{
    display: flex;
    justify-content: center;
    align-items: center;
    width: 80px;
    height: 20px;
    background-color: green;
    margin-top: 30px;
  }
</style>
