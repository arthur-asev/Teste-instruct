<template>
  <div class="leads">
    <Logo />
    <!-- <Logo dark-background /> -->
    <h1 class="leads__title">Leads</h1>
    <div class="filtro-container">
      <div class="filtro_pesquisa">
        <label for="">Nome</label>
        <input type="text" placeholder="  Pesquisar por Nome" />
        <label for="">Categorias</label>
        <input type="text" placeholder=" Pesquisar por Categoria" />
        <div class="espaco-bottom"></div>
      </div>
    </div>
    <div class="lista-container">
      <div class="tabela-style">
        <ListaDeUsuarios :users="users" />
      </div>
    </div>
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
      try {
        const response = await axios.get(
          'https://jsonplaceholder.typicode.com/users'
        )
        this.users = response.data
      } catch (error) {
        console.error('Ocorreu um erro na execução da API')
      }
    },
  },
}
</script>

<style scoped="true">
.lista-container {
  margin: 0 auto;
  width: 74%;
  height: auto;
}

input {
  width: 50vw;
  height: 1.5rem;
  border-radius: 8px;
}
.espaco-bottom {
  margin-bottom: 1.5em;
}
label {
  font-size: 0.8rem;
  margin-top: 1rem;
  color: white;
}
.filtro_pesquisa {
  margin-bottom: 2rem;
  align-items: center;
  display: flex;
  flex-direction: column;
}

.filtro-container {
  margin: 0 auto;
  width: 60%;
  border-radius: 8px;
  background-color: rgb(34, 135, 213);
}

.leads {
  &__title {
    margin: 1.4rem 0;
    padding: 1.4rem 0;
    border-top: $border-color 1px solid;
  }
}
</style>
