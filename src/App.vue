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
    const employees = JSON.parse(localStorage.getItem('employees'))
    if(employees){
      this.employees = employees
    }
  },
  methods: {
    addEmployee(employee) {
      const lastId = this.employees.length > 0 ? this.employees[this.employees.length - 1].id : 0;
      const id = lastId + 1;
      const newEmployee = { ...employee, id };
      this.employees = [...this.employees, newEmployee];
      localStorage.setItem('employees', JSON.stringify(this.employees))
    },
    delEmployee(id) {
      this.employees = this.employees.filter(employee => employee.id !== id)
      localStorage.setItem('employees', JSON.stringify(this.employees))
    },
    editEmployee(id, updatedEmployee) {
      this.employees = this.employees.map(employee => {
        employee.id === id ? updatedEmployee : employee
      })
      // localStorage.setItem('employees', JSON.stringify(this.employees))
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

.small-container {
  max-width: 680px;
}
</style>
