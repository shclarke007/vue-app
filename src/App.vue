<template>
  <div id="app">
    <div class="logo-container">
      <img alt="Vue logo" src="./assets/logo.png">
    </div>
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
  },
  data() {
  employees: [
    {
      id: 1,
      name: 'Richard Hendricks',
      email: 'richard@piedpiper.com'
    },
    {
      id: 2,
      name:'Bertram Gilfoyle',
      email: 'gilfoyle@piedpiper.com'
    },
    {
      id: 3,
      name: 'Dinesh Chugtai',
      email: 'dinesh@piedpiper.com'
    }
  ]
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
  margin: 0 auto;
  width: 50%;
  border: 1px solid black;
}

.logo-container {
  height: 50px;
  width: 50px;
  border: 1px solid black;
}

.logo-container img {
  height: 50px;
}

button {
  background: #009435;
  border: 1px solid #009435;
}

.small-container {
  max-width: 680px;
}
</style>
