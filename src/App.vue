<template>
  <div id="app">
    <img src="./assets/logo.png">
    <div>{{ msg }}</div>
    <vueSelect2 :options="options" label="label" tagValue="value" v-model="text1" @change="selectChange"></vueSelect2>
  </div>
</template>

<script>
import vueSelect2 from './components/vueSelect2'

export default {
  name: 'App',
  components: { vueSelect2 },
  data () {
    return {
      text1: '',
      msg: '一个Vue中使用的selecet2组件',
      options: [
        // { name: '苹果', value: 1, label: 'label1' },
        // { name: '香蕉', value: 2, label: 'label2' },
        // { name: '西瓜', value: 3, label: 'label3' },
        // { name: '芒果', value: 4, label: 'label4' }
      ]
    }
  },
  watch: {
    text1: function(newVal, oldVal) {
      console.log(newVal, 'newValue')
      console.log(this.text1, 'text1')
    }
  },
  mounted() {
    setTimeout(() => {
      this.options = [
        { name: '苹果1', value: 11, label: 'label5' },
        { name: '香蕉1', value: 12, label: 'label6' },
        { name: '西瓜1', value: 13, label: 'label7' },
        { name: '芒果1', value: 14, label: 'label8' }
      ]
    }, 5000)
  },
  methods: {
    selectChange(val) {
      console.log('父亲的change', val)
      // this.optionValue = ''
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
