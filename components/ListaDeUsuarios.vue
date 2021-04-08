<template>
  <div class="lista">
    <tr>
      <th style="width: 24vw">Ip</th>
      <th style="width: 24vw">Nome</th>
      <th style="width: 24vw">Categoria</th>
    </tr>
    <div
      v-for="user in users"
      :key="user.id"
      @click="
        mostraTabela = user.id
        mostraTabelaDropDown()
      "
    >
      <table>
        <tr>
          <td style="width: 33%">{{ user.id }}</td>
          <td style="width: 33%">{{ user.name }}</td>
          <td style="width: 33%">{{ user.company.bs }}</td>
        </tr>
      </table>
      <div class="espc"></div>
      <div
        v-if="mostraTabela == user.id && tabelaVisivel"
        class="listaDropdown"
      >
        <div>
          <p>Compania:</p>
          <p>{{ user.company.name }}</p>
        </div>
        <div>
          <p>Nome de usuário:</p>
          <p>{{ user.username }}</p>
        </div>
        <div>
          <p>Telefone:</p>
          <p>{{ user.phone }}</p>
          <p>abra no seu Smartfone</p>
        </div>
        <div>
          <p>E-mail:</p>
          <a :href="`mailto:${user.email}`" target="_blank">
            {{ user.email }}
          </a>
          <p>Enviar Email agora</p>
        </div>
        <div>
          <p>Endereço:</p>
          <a
            :href="`https://maps.google.com/?q=${user.address.geo.lat},${user.address.geo.lng}`"
            target="_blank"
          >
            {{ user.address.suite }}
            {{ user.address.street }},
            {{ user.address.city }}
          </a>
          <p>Abrir no Google Maps</p>
        </div>
        <div>
          <p>Site</p>

          <a :href="`http://${user.website}`" target="_blank">
            {{ user.website }}
          </a>
        </div>
      </div>
      <div class="espc"></div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    users: { type: Array, require: true },
  },
  data() {
    return {
      tabelaVisivel: false,
      mostraTabela: -1,
    }
  },

  methods: {
    mostraTabelaDropDown() {
      this.tabelaVisivel = !this.tabelaVisivel
    },
  },
}
</script>
<style scoped>
table:hover {
  color: white;
  border-radius: 8px;
  margin: 0 auto;
  background-color: rgba(18, 148, 235, 0.7);
  width: 97%;
}

.listaDropdown {
  font-size: 1rem;
  border-radius: 8px;
  margin: 0 auto;
  background-color: rgba(107, 118, 126, 0.7);
  color: rgb(255, 255, 255);
  width: 60vw;
  display: grid;
  grid-template-columns: 1fr 1fr;
  align-items: center;
  gap: 0.7rem 0.5rem;
  padding: 1.5rem;
  border-radius: 0.5rem;
}
.listaDropdown a,
p {
  font-size: 0.8rem;
  color: rgb(255, 255, 255);
}

.espc {
  padding-top: 5px;
}
.lista {
  width: 70vw;
  border-radius: 10px;
  background: rgba(235, 235, 235, 0.734);
  margin-bottom: 30px;
}

table,
td {
  font-size: 0.7rem;
  text-align: center;
  width: 100%;
}
.testez {
  width: 100%;
}
td {
  cursor: pointer;
}

th {
  padding-top: 10px;
  font-size: 0.8rem;
}
</style>
