<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="I am in Vue.js App"/>
    <EmployeeTable />
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import EmployeeTable from './components/EmployeeTable.vue'

export default {
  name: 'app',
  components: {
    HelloWorld,
    EmployeeTable
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

button {
  background: #009435;
  border: 1px solid #009435;
}

.small-container {
  max-width: 680px;
}
</style>
