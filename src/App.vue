<template>
  <div id="app">
    <nav>
      <div class="logo-container">
      <img alt="Vue logo" src="./assets/logo.png">
    </div>
    <header>
      <HelloWorld msg="Demo Vue App"/>
    </header>
    </nav>
    <EmployeeTable heading="Employees Table"/>
  </div>
</template>

<script>
import HelloWorld from '@/components/HelloWorld.vue'
import EmployeeTable from '@/components/EmployeeTable.vue'

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
  padding: 10px;
  border: 1px solid black;
  display: flex;
  flex-direction: column;
}

.logo-container {
  height: 50px;
  width: 50px;
  /* border: 1px solid black; */
}

.logo-container img {
  height: 50px;
}

nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

button {
  background: #009435;
  border: 1px solid #009435;
}

.small-container {
  max-width: 680px;
}
</style>
