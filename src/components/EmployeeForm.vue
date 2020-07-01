.<template>
  <div id="employee-form">
      <form @submit.prevent="handleSubmit">
        <label>Employee name</label>
        <input v-model="employee.name" type="text" />
        <label>Employee Email</label>
        <input v-model="employee.email" type="text" />
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
  computed: {
    invalidName(){
      return this.employee.name === ''
    },
    invalidEmail(){
      return this.employee.email === ''
    }
  },
    methods: {
        handleSubmit() {
            this.$emit('add:employee', this.employee)
        }
    }
}
</script>

<style scoped>
form {
    margin-bottom: 2rem;
  }
</style>