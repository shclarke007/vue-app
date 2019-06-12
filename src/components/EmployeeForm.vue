<template>
  <div class="form-container">
    <form id="employee-form" @submit.prevent="handleSubmit">
      <label>Employee name</label>
      <input v-model="employee.name" for="employee-name" type="text" placeholder="enter name"/>
      <label>Employee email</label>
      <input v-model="employee.email" for="employee-email" type="text" placeholder="enter email"/>
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
  methods: {
    handleSubmit() {
      this.$emit('add:employee', this.employee);
    }
  }
}
</script>

<style scoped>
  form {
    margin-bottom: 2rem;
  }

  .form-container {
    padding: 20px;
    
  }

  @media screen and (min-width: 600px) {
    .form-container {
    width: 20%;
    margin: 0 auto;
  }
  }
</style>


