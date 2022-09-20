<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <RenderList :page='page'/>
    <MyPagination @page='getPage' :newPay='newPay'/>
    <button @click="show=!show">ADD NEW COST</button>
    <AddExpenses @addNewPay="getNewPay" v-show="show"/>
  </div>
</template>

<script>
import RenderList from './components/RenderList.vue'
import AddExpenses from './components/AddExpenses.vue'
import MyPagination from './components/Pagination.vue'

export default {
  name: 'App',
  components: {
    RenderList,
    AddExpenses,
    MyPagination
  },
  data () {
    return {
      show: false,
      page: '',
      newPay: ''
    }
  },
  methods: {
    getPage (data) {
      this.page = data
    },
    getNewPay (it) {
      this.newPay = it
    }
  },
  created () {
    this.$store.dispatch('getPaymentList')
    this.$store.dispatch('getDefaultPaymentListPage')
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
