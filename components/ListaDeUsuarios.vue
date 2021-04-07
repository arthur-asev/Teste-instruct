<template>
  <div class="lista">
    <div class="titulo">
      <p>Clientes</p>
    </div>

    <div class="container">
      <table id="Tab">
        <tr>
          <th>Id</th>
          <th>Nome</th>
          <th>Categorias</th>
        </tr>
        <tr>
          <th></th>
          <td></td>
          <td></td>
        </tr>
      </table>
    </div>
    {{ users }}
  </div>
</template>

<script>
const axios = require('axios')

export default {
  data() {
    return {
      users: [],
    }
  },

  mounted() {
    this.getUsers()
  },

  methods: {
    async getUsers() {
      const response = await axios.get(
        'https://jsonplaceholder.typicode.com/users'
      )
      this.users = response.data
    },
  },
}
</script>
<style scoped>
table,
th,
td {
  border: 2px solid black;
}
</style>
