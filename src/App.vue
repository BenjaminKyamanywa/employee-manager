<template>
  <div id="app" class="small-container">
    <h1>Employees</h1>
    <employee-table :employees="employees"/>
  </div>
</template>

<script>
import EmployeeTable from '@/components/EmployeeTable.vue'

export default {
  name: 'App',
  components: {
    EmployeeTable
  },
  data() {
    return {
      employees: [
        {
          id: 1,
          name: 'John Snow',
          email: 'john@snow.com',
        },
        {
          id: 2,
          name: 'Daenerys Targaryen',
          email: 'dany@targaryen.com',
        },
        {
          id: 3,
          name: 'Robert Baratheon',
          email: 'robert@baratheon.com',
        },
      ],
    }
  }
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
