<template>
    <div>
        <button>prev</button>
        <button v-for="(page, index) of pages"
        :key="index"
        @click="addNumberPage($event)">{{ page }}</button>
        <button>next</button>
    </div>
</template>

<script>
export default {
  name: 'MyPagination',
  props: {
    newPay: {
      type: String
    }
  },
  data () {
    return {
      pages: [],
      numberPage: ''
    }
  },
  created () {
    this.pages = this.$store.getters.GET_ALL_PAGE
  },
  methods: {
    addNumberPage (e) {
      this.$emit('page', e.target.innerText)
      this.$store.commit('SET_RENDER_PAGE', e.target.innerText)
    }
  },
  watch: {
    newPay: function () {
      this.pages = this.$store.getters.GET_ALL_PAGE
    }
  }
}
</script>

<style lang="sass" modules>

</style>
