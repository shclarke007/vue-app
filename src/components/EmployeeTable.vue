<template>
  <div id="employee-table">
    <h2>{{title}}</h2>
    <table>
      <thead>
        <tr>
          <th>Employee name</th>
          <th>Employee email</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="employee in employees" :key="employee.id">
          <td>{{employee.name}}</td>
          <td>{{employee.email}}</td>
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
  },
}
</script>

<style scoped>

</style>


