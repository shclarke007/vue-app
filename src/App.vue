<template>
  <div id="app">
    <nav>
      <div class="logo-container">
        <img alt="Vue logo" src="./assets/logo.png">
      </div>
    <header>
      <hello-world msg="Demo Vue App"/>
    </header>
    </nav>
    <div>
      <employee-form @add:employee="addEmployee" />
    </div>
    <div>
      <employee-table 
        title="Employees Table" 
        name="Name" 
        email="Email"
        actions="Actions"
        :employees="employees" 
        @del:employee="delEmployee"
        @edit:employee="editEmployee"
      />
    </div>
  </div>
</template>

<script>
import HelloWorld from '@/components/HelloWorld.vue'
import EmployeeTable from '@/components/EmployeeTable.vue'
import EmployeeForm from '@/components/EmployeeForm.vue'

export default {
  name: 'app',
  components: {
    HelloWorld,
    EmployeeTable,
    EmployeeForm
  },
  data() {
    return {
      employees: [],
  }
}, 
  mounted() {
    this.getEmployees()
  },
  methods: {
    async getEmployees() {
      try {
        const response = await fetch('https://jsonplaceholder.typicode.com/users')
        const data = await response.json()
        this.employees = data
      } catch(error) {
        console.log(error)
      }  
    },
    async addEmployee(employee) {
      try {
        const response = await fetch('https://jsonplaceholder.typicode.com/users', {
          method: 'POST',
          body: JSON.stringify(employee),
          headers: { 'Content-type': 'application/json; charset=UTF-8'}
        })
        const data = await response.json()
        this.employees = [...this.employees, data]
      } catch(error) {
        console.log(error)
      }
      
    },
  async delEmployee(id) {
    try {
      await fetch(`https://jsonplaceholder.typicode.com/users/${id}`, {
        method: 'DELETE'
      })
      this.employees = this.employees.filter(employee => employee.id !== id)
    } catch(error) {
        console.log(error)
    }
    },
  async editEmployee(id, updatedEmployee) {
      try {
        const response = await fetch(`https://jsonplaceholder.typicode.com/users/${id}`, {
          method: 'PUT',
          body: JSON.stringify(updatedEmployee),
          headers: { 'Content-type': 'application/json; charset=UTF-8' },
        })
        const data = await response.json()
        this.employees = this.employees.map(employee => employee.id === id ? data : employee)
      } catch(error) {
        console.log(error)
      }
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
  padding: 10px;
  /* border: 1px solid black; */
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

button:hover,
button:active,
button:focus {
  background: #32a95d;
  border: 1px solid #32a95d;
}

.small-container {
  max-width: 680px;
}
</style>
