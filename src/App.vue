<template>
  <div id="app">
    <calc-table :items="fruits"></calc-table>
  </div>
</template>

<script>
import calcTable from './calcTable'
export default {
  name: "App",
  data () {
    return {
      fruits: [
       	{name: "りんご", tanka:100, qty:1 },
      	{name: "バナナ", tanka:250, qty:2 },
      	{name: "みかん", tanka:200, qty:3 },
      	{name: "ぶどう", tanka:400, qty:4 } 
      ]      
    }
  },
  components: {
    calcTable
  },
  methods: {
  },
  computed: {
  }
};
</script>

<style>
#app {
  margin-top: 60px;
}
* {  
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  font-size: 16px;
}
</style>
