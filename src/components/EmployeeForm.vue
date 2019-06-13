<template>
  <div class="form-container">
    <form id="employee-form" @submit.prevent="handleSubmit">
      <label>Employee name</label>
      <input 
        v-model="employee.name"
        :class="{ 'has-error': submitting && invalidName }"
        @focus="clearStatus" 
        @keypress="clearStatus"
        for="employee-name" 
        type="text" 
        placeholder="enter name"
        ref="first"
      />
      <label>Employee email</label>
      <input 
        v-model="employee.email"
        :class=" { 'has-error' : submitting && invalidEmail }"
        @focus="clearStatus" 
        for="employee-email" 
        type="text" 
        placeholder="enter email"
      />
      <p v-if="error && submitting" class="error-message">
        ❗ Please fill out all required fields
      </p>
      <p v-if="success" class="success-message">
        ✅ Employee successfully added
      </p>
      <button>Add Employee</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'employee-form',
  data() {
    return {
      submitting: false,
      error: false,
      success: false,
      employee: {
        name: '',
        email: '',
      },
    }
  },
  methods: {
    handleSubmit() {
      this.submitting = true
      this.clearStatus()

      if(this.invalidName || this.invalidEmail) {
        this.error = true
        return
      }
      this.$emit('add:employee', this.employee)
      this.$refs.first.focus()
      this.employee == {
        name: '',
        email: '',
      }
      this.error = false
      this.success = true
      this.submitting = false
    },
    clearStatus() {
      this.success = false
      this.error = false
    }
  },
  computed: {
      invalidName(){
        return this.employee.name === ''
      },
      invalidEmail(){
        return this.employee.email === ''
      },
    },
}
</script>

<style scoped>
  form {
    margin-bottom: 2rem;
  }

  .form-container {
    padding: 20px;
    
  }

  [class*='-message'] {
    font-weight: 500;
  }

  .error-message {
    color: #d33c40;
  }

  .success-message {
    color: #32a95d;
  }

  @media screen and (min-width: 600px) {
    .form-container {
    width: 20%;
    margin: 0 auto;
  }
  }
</style>


