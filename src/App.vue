<template>
  <div id="app" class="small-container">
    <h1>Employee Manager</h1>

    <employee-form @add:employee="addEmployee"/>
    <employee-table 
      :employees="employees" 
      @delete:employee="deleteEmployee"
      @edit:employee="editEmployee"
      />
  </div>
</template>

<script>
import EmployeeTable from '@/components/EmployeeTable.vue'
import EmployeeForm from '@/components/EmployeeForm.vue'


export default {
  name: 'App',
  components: {
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
    // GET method for retrieving employees
    async getEmployees() {
      try { 
        const response = await fetch('https://jsonplaceholder.typicode.com/users')
        let data = await response.json()
        this.employees = data.filter(employee => (employee.id > 0 && employee.id < 4))
      } catch (error) { 
        console.error(error)
      }
    },
    // POST method for creating an employee
    async addEmployee(employee) {
      try {
        const response = await fetch('https://jsonplaceholder.typicode.com/users', {
          method: 'POST',
          body: JSON.stringify(employee),
          headers: { 'Content-type': 'application/json; charset=UTF-8' },
        })
        const data = await response.json()
        this.employees = [...this.employees, data]
      } catch (error) {
        console.error(error)
      }
    },
    // PUT method for editing employee
    async editEmployee(id, updatedEmployee) {
      try {
        const response = await fetch(`https://jsonplaceholder.typicode.com/users/${id}`, 
        {
          method: 'PUT',
          body: JSON.stringify(updatedEmployee),
          headers: { 'Content-type': 'application/json; charset=UTF-8' }
        })
        const data = await response.json()
        this.employees = this.employees.map(employee => (employee.id === id ? data : employee))
      } catch (error) {
        console.error(error)
      }
    },
    // DELETE method for deleting employee
    async deleteEmployee(id) {
      try {
          await fetch(`https://jsonplaceholder.typicode.com/users/${id}`, {
            method: "DELETE"
          });
          this.employees = this.employees.filter(employee => employee.id !== id);
        } catch (error) {
          console.error(error);
        }
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

button {
  background: #009435;
  border: 1px solid #009435;
}

.small-container {
  max-width: 5
}
</style>
