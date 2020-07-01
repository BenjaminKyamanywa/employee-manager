<template>
  <div id="employee-table">
    <table>
      <thead>
        <tr>
          <th>Employee name</th>
          <th>Employee email</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>John Snow</td>
          <td>john@snow.com</td>
        </tr>
        <tr>
          <td>Daenerys Targaryen</td>
          <td>dany@targaryen.com</td>
        </tr>
        <tr>
          <td>Robert Baratheon</td>
          <td>robert@baratheon.com</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
  export default {
    name: 'employee-table',
  }
</script>

<style scoped></style>