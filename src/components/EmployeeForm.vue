<template>
  <div>
    <form id="employee-form">
      <label>Employee name</label>
      <input for="employee-name" type="text" placeholder="enter name"/>
      <label>Employee email</label>
      <input for="employee-email" type="text" placeholder="enter email"/>
      <button>Add Employee</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'employee-form',
  data() {
    return {
      employee: {
        name: '',
        email: '',
      },
    }
  },
}
</script>

<style scoped>
  form {
    margin-bottom: 2rem;
  }
</style>


