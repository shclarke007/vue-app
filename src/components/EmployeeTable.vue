<template>
  <div id="employee-table">
    <h2>{{title}}</h2>
    <p v-if="employees.length < 1" class="empty-table">No employees yet</p>
    <table>
      <thead>
        <tr>
          <th>{{name}}</th>
          <th>{{email}}</th>
          <th colspan="2">{{actions}}</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="employee in employees" :key="employee.id">
          <td>{{employee.name}}</td>
          <td>{{employee.email}}</td>
          <!-- <td><button>Edit</button></td> -->
          <td><button @click="$emit('del:employee', employee.id)">Del</button></td>
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
}
</script>

<style scoped>

</style>


