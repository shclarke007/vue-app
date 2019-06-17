<template>
  <div id="employee-table" class="employee-table-container">
    <h2>{{title}}</h2>
    <p v-if="employees.length < 1" class="empty-table">No employees yet</p>
    <table>
      <thead>
        <tr>
          <th>{{name}}</th>
          <th>{{email}}</th>
          <th>{{actions}}</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="employee in employees" :key="employee.id">
          <td v-if="editing === employee.id">
            <input type="text" v-model="employee.name" v-on:keyup.enter="editEmployee(employee)">
          </td>
          <td v-else>{{employee.name}}</td>
          <td v-if="editing === employee.id">
            <input type="text" v-model="employee.email" v-on:keyup.enter="editEmployee(employee)">
          </td>
          <td v-else>{{employee.email}}</td>
          <td v-if="editing === employee.id">
            <button @click="editEmployee(employee)">Save</button>
            <button class="muted-button" @click="cancelEdit(employee)">Cancel</button>
          </td>
          <td v-else>
            <button @click="editMode(employee)">Edit</button>
            <button @click="$emit('del:employee', employee.id)">Delete</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'employee-table',
  props: {
    employees: Array,
    title: String,
    name: String,
    email: String,
    actions: String,
  },
  data(){
    return {
      editing: null, 
    }
    },
  methods: {
    editMode(employee) {
      this.cachedEmployee = Object.assign({}, employee)
      this.editing = employee.id
    },
    editEmployee(employee) {
      if(employee.name === '' || employee.email === '') return
      this.$emit('edit:employee', employee.id, employee)
      this.editing = null
    },
    cancelEdit(employee){
      Object.assign(employee, this.cachedEmployee)
      this.editing = null
    },
  },
  
}
</script>

<style scoped>
  .employee-table-container {
    display: flex;
    flex-direction: column;
  }

  button {
    margin: 0 0.5rem 0.5rem 0;
  }
</style>



