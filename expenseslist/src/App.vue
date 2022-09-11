<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <RenderList :expensesList="expensesList"/>
    <AddExpenses/>
  </div>
</template>

<script>
import RenderList from './components/RenderList.vue'
import AddExpenses from './components/AddExpenses.vue'

export default {
  name: 'App',
  components: {
    RenderList,
    AddExpenses
  },
  data () {
    return {
      expensesList: []
    }
  },
  methods: {
    fetchData () {
      return [
        {
          date: '28.03.2020',
          category: 'Food',
          value: 169
        },
        {
          date: '24.03.2020',
          category: 'Transport',
          value: 360
        },
        {
          date: '24.03.2020',
          category: 'Food',
          value: 532
        }]
    }
  },
  created () {
    this.expensesList = this.fetchData()
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
