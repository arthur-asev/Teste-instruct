<template>
  <div class="lista">
    <div class="container">
      <table id="Tab">
        <tr>
          <th>Id</th>
          <th>Nome</th>
          <th>Categorias</th>
        </tr>
        <tr v-for="user in users" :key="user.id">
          <th class="x">{{ user.id }}</th>
          <td class="y">{{ user.name }}</td>
          <td class="z">{{ user.company.bs }}</td>
        </tr>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    users: { type: Array },
  },
  data() {
    return {}
  },

  methods: {},
}
</script>
<style scoped>
table {
  border-radius: 8px;
  border: 2px solid black;
}
.y,
.z {
  text-align: center;
}

th {
}
table {
  margin: 0 auto;
  width: 80%;
}
</style>
